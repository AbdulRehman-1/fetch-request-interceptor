<div align="center">
	<h1> Fetch Interceptor<br>
	</h1>
</div>

> Fetch Interceptor is an npm library that allows you to modify, enhance, and inspect HTTP requests and responses made using the Fetch API. It supports adding headers, handling errors, and chaining multiple interceptors for sophisticated request/response handling.

## Install

```bash
$ npm install --save react-fetch-interceptor
```

## Usage
```
import {useEffect} from 'react'
import { createFetchInterceptor } from 'react-fetch-interceptor';

function App() {
  
  useEffect(() => {

	const jwt = localStorage.getItem('jwt')
    const interceptor = createFetchInterceptor();
    interceptor.setRequestInterceptor(async (input, init = {}) => {
      // Ensure init is defined and headers object is initialized
      init.headers = {
        ...init.headers, // Preserve any existing headers
        Authorization:
          `Bearer ${jwt}`,
        // If you want to override any header do here...
      };

      console.log('Intercepted request:', input, init);

      return { input, init };
    });

    fetch('https://jsonplaceholder.typicode.com/todos/1', {
      headers: {
        'Content-Type': 'application/json',
      },
    })
      .then((response) => response.json())
      .then((data) => console.log({ data }));
  }, []);
  return <div>React fetch interceptor</div>
}
```



## 👨🏻‍💻 AUTHOR
  Abdul Rehman
   
