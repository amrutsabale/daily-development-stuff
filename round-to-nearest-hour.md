
## Round Date to the Nearest Hour

``````
import { DateTime } from 'luxon';

//for local date 
export function roundToNearestHour(date) {
  date.setMinutes(date.getMinutes() + 30);
  date.setMinutes(0, 0, 0);
  return date;
}

// for UTC 
export function roundToNearestUTCHour(date) {
  const utc_dt = DateTime.fromMillis(date.getTime()).toUTC();
  const hour_dt = utc_dt.plus({ minutes: 30 }).set({ minute: 0, second: 0, millisecond: 0 });

  return new Date(hour_dt.toMillis());
}

``````

ref: https://bobbyhadz.com/blog/javascript-date-add-minutes
