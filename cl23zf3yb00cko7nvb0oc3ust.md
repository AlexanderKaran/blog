---
title: "Fetch, Networking and Async Functions"
datePublished: Mon Apr 18 2022 00:31:40 GMT+0000 (Coordinated Universal Time)
cuid: cl23zf3yb00cko7nvb0oc3ust
slug: fetch-networking-and-async-functions
cover: https://cdn.hashnode.com/res/hashnode/image/unsplash/8bghKxNU1j0/upload/v1649673574446/JM5NYu-7R.jpeg
tags: javascript, apis, reactjs, networking, fetch

---

*Disclaimer: I created this blog and content to help my 2022 SheCodes Australia Plus cohort understand the basics of using fetch in React.*

How do we fetch data from an API in React? When JavaScript is run in the browser, it has access to a fantastic built-in library called `fetch`. Fetch allows us to make a network request using a simple JavaScript function. Let's see it in action.

```
fetch("https://blog.alexanderkaran.com/rss.xml", {method: "GET"})
```

The first parameter or argument we give to the `fetch` function is the URL we want to make the network request to. The function's second argument is an object that we can use to pass in different settings. Here, the method key is set to the value `"GET"`; it is a request using the HTTP method `GET`. If you're new to fetch, I might have lost you. Let's break down HTTP methods and what they mean.

***

## HTTP Methods

HTTP methods tell fetch what type of request we are making and changes the way our function works. Changing the request method also changes how an API responds to our request.

### GET

A `GET` request means we are fetching data from the API. Essentially you are saying, can I please have the resources, data or contents at this URL. The response could come back in many formats HTML, JSON, XML and more.

### POST

A `POST` request means we are submitting data to the API. The client's (the browser) way of saying here is some new data; please validate it, process it or save it. 

### PATCH

A `PATCH` request is similar to the `POST request in that you send data but used to update the current object with this new data, unlike `POST`, which creates new data.

### PUT

There is a lot of debate about when to use `PUT` or `POST`, and a lot of developers use `PUT` instead of `POST`, which is fine. Like most things in programming, it's subjective. A `PUT` request does the same as a `POST` request; however, how it behaves will depend on the API you are using. I try to stick to RESTfull* principles when building APIs myself, so I follow these rules when choosing between `PUT` and `POST`. If I were to make the network request repeatedly and each time it would create brand new objects or data, I would choose `POST`. If I make the same network request over and over, creating the first time and then completely replacing the data on each subsequent request, I choose `PUT`. To give you an example of when I would use it, let's look at creating a user object and adding their profile image. Making a call to my APIs user endpoint always creates a new user so that it would be `POST`. Where uploading a profile image for the user in my API replaces the image before, making it a `PUT` request.

* REST is a set of rules and principles to build an API. You can find [out more here](https://restfulapi.net/).

### DELETE

A `DELETE` request is easy; it deletes the resources, content or data at the URL in your request.

***

## Async Functions

Now that we have a basic idea of the different network requests, let's look at the `fetch` function. Now I oversimplified the function example I used at the blog's beginning. We need a few more lines of code to make `fetch` work correctly. When making a fetch request, it returns something called a promise. A promise is JavaScript's way of saying I have gone off to do something for you and will come back to you in the future and let you know if it succeeds. A promise exists in three states, `pending`, `fulfilled` and `rejected`. The promise starts as pending and will either return what you asked for if it is successful (fulfilled) or an error if it failed (rejected). Let's see this in action. I have left comments in the code to explain what I am doing.

```
// The async before the function is our way of letting JavaScript and the compiler/run-time know that this function returns a promise. 
// A network call takes time, so to allow us to wait for the response, we need to mark the function as async. 
async function getAlexanderGithubEvents () {
  // What is this try and catch keyword? 
  // Any code that executes inside the try section and throws an error will cause the code inside the try section to stop and pass the error to the catch section, and then any code in there will run.
  try {
    // We are making a fetch request using the " Get " method. 
    // The request fetches my user's event details from the Github API. 
    // Before the fetch function call, the await keyword tells the system to wait for this function to return a promise before processing the following line of code. 
    // Remember, a promise returns either a success or an error. 
    // The success option can have data in it. When using fetch the success from a promise or its fulfilled state, it returns the response from the network call.
    const res = await fetch("https://api.github.com/users/AlexanderKaran/events", {"method": "GET"})
    // When we have the response, we need to format it to access the data inside. 
    // We can use another async function that returns a promise to parse the response into JSON. 
    const body = await res.json()
    // Now, we can return the data we got from the Github API from the function
    return body
  } catch (err) {
    console.log(err)
  }
}
```

If you run this function, the return data would look something like this:

```
[
  {
    id: '21207323061',
    type: 'PushEvent',
    actor: {
      id: 47707063,
      login: 'AlexanderKaran',
      display_login: 'AlexanderKaran',
      gravatar_id: '',
      url: 'https://api.github.com/users/AlexanderKaran',
      avatar_url: 'https://avatars.githubusercontent.com/u/47707063?'
    },
    repo: {
      id: 278240670,
      name: 'AlexanderKaran/AlexanderKaran',
      url: 'https://api.github.com/repos/AlexanderKaran/AlexanderKaran'
    },
    payload: {
      push_id: 9586198889,
      size: 1,
      distinct_size: 1,
      ref: 'refs/heads/master',
      head: '73bc96c09eba93eb4684332c7f2cc2151550bd08',
      before: 'faf37b0a0f155e87e9175d317f244aa90a488a99',
      commits: [
        {
          sha: '73bc96c09eba93eb4684332c7f2cc2151550bd08',
          author: {
            email: '47707063+AlexanderKaran@users.noreply.github.com',
            name: 'Alexander Karan'
          },
          message: 'Updated about page',
          distinct: true,
          url: 'https://api.github.com/repos/AlexanderKaran/AlexanderKaran/commits/73bc96c09eba93eb4684332c7f2cc2151550bd08'
        }
      ]
    },
    public: true,
    created_at: '2022-04-10T11:19:17Z'
  },
]
```

Now you have a rough idea of how to make a network request, let's spin up a small app and load some of the data from the Github API there.

***

## Example App

First, set up a new project with Create React App using the following command in the terminal `npx create-react-app networking`.

Wait for it to set up the project, cd into the folder using `cd networking`. Run the app to ensure everything is working by typing in `npm start`. Head to our `app.js` file, and let's update the code to run the network request.


```
import "./App.css";

function App() {
  async function getAlexanderGithubEvents() {
    try {
      const res = await fetch("https://api.github.com/users/AlexanderKaran/events", {
        method: "GET",
      });
      const body = await res.json();
      return body;
    } catch (err) {
      console.log(err);
    }
  }

  return (
    <div className="App">
      <header className="App-header">
        <p>{getAlexanderGithubEvents()}</p>
      </header>
    </div>
  );
}

export default App;
```

If we open the dev tools and head to the networking tab, you can see the network request has been made; however, the page is blank. The data has not loaded, but why?


![Screen Shot 2022-04-15 at 9.05.21 am.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649984777939/JkzODRW2G.png)

What is going on? Remember, the function is a promise and takes time to run. React has already rendered the UI onto the page, so unless something changes in the state, it won't update. Let's re-write the function to load my profile image from the Github data we get back from the API call using state and a React hook (function) called useEffect.

```
// useEffect get imported from React just like the useState hook
import { useState, useEffect } from "react";
// We can keep the default CSS that comes with the project to make the image spin round
import "./App.css";

function App() {
  // Declare state for us to store the response from the Github network call in
  const [githubData, setGithubData] = useState();

  // useEffect takes two arguments, the first is the code we want to run, and the second is an array.
  // Putting arguments into the array means the useEffect watches them for changes and re-runs the code.
  // The code will only run once when the array is empty after the first UI render.
  useEffect(() => {
    // Here, I create my function like before, but instead of returning the data, I set it to state using setGithubData
    async function getAlexanderGithubEvents() {
      try {
        const res = await fetch(
          "https://api.github.com/users/AlexanderKaran/events",
          {
            method: "GET",
          }
        );
        const body = await res.json();
        setGithubData(body);
      } catch (err) {
        console.log(err);
      }
    }

    getAlexanderGithubEvents();

    // The empty array
  }, []);

  return (
    <div className="App">
      <header className="App-header">
        {/* Finally, I use a ternary to render an image if there is a value in the state or a paragraph with the words loading inside if it is empty. */}
        {githubData ? (
          <img
            // If you see the data example from earlier, it returns an array, so I need to access that before the object values.
            src={githubData[0].actor.avatar_url}
            className="App-logo"
            alt="logo"
          />
        ) : (
          <p>
            Edit <code>src/App.js</code> and save to reload.
          </p>
        )}
      </header>
    </div>
  );
}

export default App;

```
You should see my funny face spinning around if you head to the browser.

***

## Conclusion

You should now have a basic idea of making network requests in JavaScript and React. There is still a lot to go over with networking, such as handling failed requests and handling different responses from an API, but this is an excellent place to start. Promises and async functions can take a while to get your head around. Here is a [great resource](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) if you are still a little lost. If you want to check out [my example project](https://github.com/AlexanderKaran/networking), you can find all the code on Github. For further reading on fetch, check out the [MDM Docs](https://developer.mozilla.org/en-US/docs/web/api/fetch). 

If you have any questions about what I have covered or spot a mistake, you can reach me here or Twitter.



