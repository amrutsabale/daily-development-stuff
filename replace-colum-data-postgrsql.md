
epoch_date
`2023-07-30 04:00:00` -> `2023-07-30 05:00:00`

````
update account.tb_container_weather_forecast df1 set day_epoch=(
select TO_TIMESTAMP(replace(ct,'04','05'), 'YYYY-MM-DD HH:MI:SS')::timestamp without time zone from
	(select TO_CHAR(day_epoch,'YYYY-MM-DD HH24:MI:SS') as ct from 
		  account.tb_container_weather_forecast df2  WHERE 
          df2.container_id = df1.container_id AND  df2.container_type= df1.container_type
          AND df2.ix= df1.ix AND df2.epoch_time=df1.epoch_time
	) df_sub
) WHERE 
         df1.container_id = 334
          AND df1.container_type = 1
          AND df1.epoch_time>'2023-07-10T08:14:44.278Z'
		  AND  CAST(df1.day_epoch AS varchar) like '%04:00:00';

````
