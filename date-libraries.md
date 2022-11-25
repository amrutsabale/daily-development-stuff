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
