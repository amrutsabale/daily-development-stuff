### Query pssql json onject
Eg. assume this is row in table `Sample`

| id      | Description |
| ----------- | ----------- |
| 1      | {  "user_id":1,"account_id": 1}   |
| 2   |{  "user_id":2,"account_id": 2}   |
| 3   |{  "user_id":4,"account_id": 1}   |

````
SELECT * FROM Sample where params @> '{"account_id": 1}';

````
