````
function newlinelToBrTag(str, is_xhtml) {
  const breakTag = is_xhtml || typeof is_xhtml === 'undefined' ? '<br />' : '<br>';
  return `${str} `.replace(/([^>\r\n]?)(\r\n|\n\r|\r|\n)/g, `$1${breakTag}$2`);
}

const htmlText='john:hello\namrut:hi';

 <div     
 dangerouslySetInnerHTML={{
            __html: newlinelToBrTag(htmlText, true),
          }}
  />

`````
````
//above div will render as
john:hello
namrut:hi
````
