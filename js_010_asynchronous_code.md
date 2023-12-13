# Asynchronous Code



## Promises
```js
let p = new Promise(function(resolve, reject) {
	
	// Do an async task async task and then...

	if(/* good condition */) {
		resolve('Success!');
	}
	else {
		reject('Failure!');
	}
});

p.then(function(result) { 
	/* do something with the result */
}).catch(function() {
	/* error :( */
}).finally(function() {
   /* executes regardless or success for failure */ 
});
```

<details>
        <summary>Example of Promise</summary>

https://davidwalsh.name/promises
```js
function get(url) {
  // Return a new promise.
  return new Promise(function(resolve, reject) {
    // Do the usual XHR stuff
    var req = new XMLHttpRequest();
    req.open('GET', url);

    req.onload = function() {
      // This is called even on 404 etc
      // so check the status
      if (req.status == 200) {
        // Resolve the promise with the response text
        resolve(req.response);
      }
      else {
        // Otherwise reject with the status text
        // which will hopefully be a meaningful error
        reject(Error(req.statusText));
      }
    };

    // Handle network errors
    req.onerror = function() {
      reject(Error("Network Error"));
    };

    // Make the request
    req.send();
  });
}

// Use it!
get('story.json').then(function(response) {
  console.log("Success!", response);
}, function(error) {
  console.error("Failed!", error);
});
```
</details>

### Promise.all

```js
let request1 = fetch('/users.json');
let request2 = fetch('/articles.json');

Promise.all([request1, request2]).then(function(results) {
	// Both promises resolved
})
.catch(function(error) {
	// One or more promises was rejected
});
```
Another Example:
```js
let req1 = new Promise(function(resolve, reject) { 
	// A mock async action using setTimeout
	setTimeout(function() { resolve('First!'); }, 4000);
});
let req2 = new Promise(function(resolve, reject) { 
	// A mock async action using setTimeout
	setTimeout(function() { reject('Second!'); }, 3000);
});
Promise.all([req1, req2]).then(function(results) {
	console.log('Then: ', results);
}).catch(function(err) {
	console.log('Catch: ', err);
});

// From the console:
// Catch: Second!
```

### Promise.race

```js
let req1 = new Promise(function(resolve, reject) { 
	setTimeout(function() { resolve('First!'); }, 8000);
});
let req2 = new Promise(function(resolve, reject) { 
	setTimeout(function() { resolve('Second!'); }, 3000);
    // Will finish before 'req1', therefore will get ...
});
Promise.race([req1, req2]).then(function(one) {
	console.log('Then: ', one); // ... Here! And then finish
    // (And not wait for the others)
}).catch(function(one, two) {
	console.log('Catch: ', one);
});

// From the console:
// Then: Second!
```

## Fetch

```js
fetch('https://url.com/some/url')
  .then(function(response) {
    // Successful response :)
  })
  .catch(function(err) {
    // Error :(
  });
```

> Best to use `CORS`, so then `fetch('url.url.com/api', {
  mode: 'cors'});`, allows restricted resources on a web page to be accessed from another domain outside the domain from which the first resource was served

So then:
```js
const img = document.querySelector('img');

fetch('https://api.giphy.com/v1/gifs/translate?api_key=YOUR_KEY_HERE&s=cats', {mode: 'cors'})
.then(function(response) {
    console.log(response.json());
}).then(function(response) {
    // Because it returned to us another promise
    // We do another '.then'
    img.src = response.data.images.original.url;
    // We needed to drill down to get the gif
});
```

## Async and Await

### How to use in syntax

```js
const yourAsyncFunction = async () => {
    // do something asynchronously and return a promise
    return result;
}

anArray.forEach(async item => {
    // do something asynchronously for each item in 'anArray'
    // one could also use .map here to return an array of promises to use with 'Promise.all()'
});

server.getPeople().then(async people => {
    people.forEach(person => {
    // do something asynchronously for each person
    });
});
```

### Generally

```js
async function getPersonsInfo(name) {
  try {
    const people = await server.getPeople();
    const person = people.find(person => { return person.name === name });
    return person;
  } catch (error) {
    // Handle the error any way you'd like
  }
}
```
Another Example:
```js
async function getCats() {
    const response = await fetch('https://api.giphy.com/v1/gifs/translate?api_key=YOUR_KEY_HERE&s=cats', {mode: 'cors'});
    const catData = await response.json();
    img.src = catData.data.images.original.url;
}
getCats();
```