REF: https://ctoomey.com/writing/downsampling-data-with-postgres-window-functions/

### Basic Downsampling Example
If I just wanted to grab all the weigh-in records, ordered by date, I could use:

````
SELECT id, date, weight FROM weighins ORDER BY date;
In order to downsample this data, I can use a window function to add a ROW_NUMBER value for the records ordered by date:
````

````
SELECT id, date, weight, ROW_NUMBER() OVER (ORDER BY date) FROM weighins;
````
Now I had the computed row number but in order to use it to filter the records I had to include it as a sub-query and then filter in the outer query:

````
SELECT id, date, weight FROM (
  SELECT id, date, weight, ROW_NUMBER() OVER (ORDER BY date) FROM weighins;
) x WHERE mod(ROW_NUMBER, 10) = 0;
````
I only want to return the id, date, and weight fields, but I’m able to use the ROW_NUMBER in our WHERE clause to grab every 10th record using mod(ROW_NUMBER, 10) = 0 filter.

Note - the x here is a name I’m giving to the sub-query. Postgres requires a name, but I’m not actually using it in the rest of the query.

Other Note - you’ll likely want to have an index on the date column to make that ORDER BY clause efficient.

### Make It User Specific
Let’s say I have the same setup as above, but the records in the table I want to downsample are user-specific and I want to provide a similar overview graph for each user. 
Some users will have long histories with thousands of records, but others will only have a handful, and I’d like to return a consistent number of records for the overview graph for all users.

In this case I can use another sub-query to determine the relevant downsample rate on a per-user basis. Let’s say I want to show a maximum of 300 data points in the overview graph; I can use a query like the following to get the downsample rate:
`````
SELECT COUNT(*) / 300 FROM weighins WHERE user_id = 7;
`````
Now, rather than using the fixed value 10 as in the first query (aka, grab every 10th record), we’ll have a value that will vary for each user to ensure we get ~300 records in the returned data set.

I can then combine that with the original query to efficiently grab the downsampled overview with the desired ~300 records:
`````
SELECT id, date, weight FROM (
  SELECT id, date, weight, ROW_NUMBER() OVER (ORDER BY date)
    FROM weighins
    WHERE user_id = 7
) x WHERE mod(ROW_NUMBER, (SELECT COUNT(*) / 300 FROM weighins WHERE user_id = 7)) = 0;
`````
Note - you’ll likely already have this, but just as a reminder, you’ll want to have an index on user_id for the relevant table to make sure the sub-query won’t slow things down too much.

