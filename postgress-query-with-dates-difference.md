````
select extract(epoch from (end_epoch::timestamp - start_epoch::timestamp));
````
## query recods with <=3 seconds durations in start and end
````
SELECT * FROM student where end_epoch is not null
and extract(epoch from (end_epoch::timestamp - start_epoch::timestamp)) <= 3;
````

