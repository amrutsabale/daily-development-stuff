## Without TimeZone Prefer: [date-fns](https://date-fns.org/)
````
import {
  subDays,
  addDays,
  addHours,
  addMinutes,
  format,
  getMinutes,
  isSameDay,
  startOfDay,
  startOfHour } from 'date-fns';

addDays(new Date(), 1) // tomorrow's date
format(alertSentDate, 'MMM DD, YYYY, h:mm A') //Nov 16, 2022, 1:17 PM
````
 
## With TimeZone Prefer: [luxon](https://moment.github.io/luxon/#/tour)
````
import { DateTime, Settings } from 'luxon';
 
 Settings.defaultZone = your_timezone;
 Settings.defaultLocale = 'en-US';
 
 DateTime.local().toFormat('yyyy-MM-dd')
 DateTime.local()
    .setZone(your_timezone)
    .setLocale('en-US');
    
const asOf=DateTime.local();    
const tomorrow = asOf.plus({ days: 1 ,months:1,hours:1});  

dt = DateTime.now();
dt.year     //=> 2017
dt.month    //=> 9
dt.day      //=> 14
dt.second   //=> 47
dt.weekday  //=> 4
````

```
 const start = DateTime.fromMillis(
    new Date("2018-05-01T13:44:48.708709Z").getTime()
  );
  const end = DateTime.fromMillis(
    new Date("2018-05-01T13:46:48.708709Z").getTime()
  );

  const asd = end.diff(start, "seconds").toObject();
  console.log("asd", asd.seconds);
```


```
const dt = DateTime.fromMillis(new Date("2023-05-07").getTime());
console.log(
    DateTime.local().hasSame(dt, "day"),
    DateTime.local().toJSDate(),
    dt.toJSDate()
  );
//false
//Fri Jul 07 2023 10:49:31 GMT+0530 (India Standard Time)
//Sun May 07 2023 05:30:00 GMT+0530 (India Standard Time)
```

```
const dt = DateTime.fromMillis(new Date("2023-07-07").getTime());
console.log(
    DateTime.local().hasSame(dt, "day"),
    DateTime.local().toJSDate(),
    dt.toJSDate()
  );
//true
//Fri Jul 07 2023 10:51:26 GMT+0530 (India Standard Time)
//Fri Jul 07 2023 05:30:00 GMT+0530 (India Standard Time)
```
