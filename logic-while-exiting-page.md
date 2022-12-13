
### Writing logic while exiting the page in React
Sounds like you could either listen for changes to the current location via the history object in a parent component.
[history.listen](https://github.com/remix-run/history/blob/main/docs/api-reference.md#historylistenlistener-listener)

`````
import { useHistory } from 'react-router-dom';
import { useEffect } from "react";

...

const history = useHistory();

useEffect(() => {
  const unlisten = history.listen((location, action) => {
    console.log('Route changed', { location, action });
    // Apply route change logic, i.e. dispatch to store
  });
  return unlisten;
}, []);
`````

Or use unmounting useEffect cleanup function in the component.

`````
import { useEffect } from "react";

...

useEffect(() => {
  return() => {
    // component unmounting (maybe from route change)
    // Apply route change logic, i.e. dispatch to store
  };
}, []);
`````
[more ref](https://stackoverflow.com/questions/70625286/how-can-i-run-code-on-a-route-change-from-certain-pages-using-react-router-5)
