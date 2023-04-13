---
title: "Practical Use Cases for Edge Computing"
seoTitle: "Practical Use Cases for Edge Computing"
seoDescription: "Want to know how to get the most out of edge computing? When should you use edge functions and when to use serverless functions? Let's find out."
datePublished: Thu Apr 13 2023 09:16:27 GMT+0000 (Coordinated Universal Time)
cuid: clgewon2x000e08mb73z4hh54
slug: practical-use-cases-for-edge-computing
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681375584733/b03bb24d-4c2c-4050-b7a7-09959634476b.jpeg
tags: javascript, typescript, serverless, vercel, edgecomputing

---

Following on from my last blog post on [WTF is Edge Computing](https://blog.alexanderkaran.com/wtf-is-edge-computing), let's take a practical look at some of its use cases. We will cover frameworks and tools, where they shine and some drawbacks.

## Fullstack Frameworks

The easiest and best example of where edge computing shines is with frameworks for building websites. I will focus on NextJS and SvelteKit as I have used these two the most. Don't worry if these two are not your go-to framework; edge functions work with Nuxt, Remix, Astro and more. If you have not tried SvelteKit yet, please give it a go. You won't regret it.

So why would you run a web app built in SvelteKit on the edge? SvelteKit pages are rendered with functions. If you think back to the speed tests in the first blog post and the fact that edge locations are closer to the user, we get faster page loads. Any server-side rendering framework benefits hugely from generating pages using edge functions. When you have pages that require dynamic content, frameworks like SvelteKit and NextJS can use serverless functions to create this content. One of the drawbacks of serverless functions is cold starts. They take a while to respond if they have not been active for a while. If we move these functions to the edge, we get shorter cold start times, and content has less distance to go between the server and the client. Let's be honest; we all want perfect lighthouse scores for every page.

There is also another reason for running your web app on the edge network, and that is middleware. Edge middleware is fantastic. The edge runs a lightweight version of JavaScript, so think less NodeJS and more browser runtime. Using middleware, we can achieve authentication, personalisation, localised content, and more. Let's dig into three examples.

### Geolocation on the Edge

Using edge location functions, we can get city, country and region from the request to render or customise different pages. Great example, my app is only available in Australia. When some access my app outside Australia, I can render a register your interest page tailoring the sign experience to the country their request came from.

### A/B Testing

In every website and web app, you need to do A/B testing at some point. To make this work, we end up with different versions of a page or feature. We make multiple trips to the server and rely on client-side code to choose which version a user receives. Now with edge functions, we can cache each version of a page or feature in the edge close to the user. Once again, we are coming back to the main benefit, speed. Edge functions are all about bringing faster responses for our end users. Rember, slower response times for websites and web apps cause people to bounce. Refer back to that [study by Google](https://blog.google/products/admanager/the-need-for-mobile-speed/) that sites: \`**53% of visits are likely to be abandoned if pages take longer than 3 seconds to load**\`

### Maintenance Mode

Say you do a production release, run a promotion or do something else crazy with your site or web app. We can use an edge config to check a maintenance mode flag. If something goes wrong, we can switch on the maintenance page while we fix it. Borrowing words from the Vercel page here, \`**give the users dynamic at the speed of static\`.** The edge is excellent at improving response times for our users, and we all want a faster web.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679732958392/7fb0affc-962f-476a-85af-095821144bcc.jpeg align="center")

So we got a bunch of great reasons for building our website and web app on the edge. What happens when your web app or website gets more complex? Maybe you need a backend and database? Before you start building an API, let's look at our options.

## Backend in the Frontend

Before we dive into this divisive topic, I want you to keep a few things in mind. We're still talking about a web app that needs a backend. We're not talking about an API supporting mobile apps and other clients. Let's face it most web apps need some backend, but do you need to build a full-fledged backend any more? A rhetorical question here; of course, you don't. Tools like Firebase, Supabase and others mean you no longer need to roll out a full-fledged backend.

As mentioned above, we can run dynamic code in the edge functions using tools like Vercel with NextJS and SvelteKit. Now there are some limitations to edge functions that we need to mention, and I will focus on Vercel. You will also find similar restrictions using other services, but they may differ slightly. Vercel edge functions use a much more lightweight JS runtime, so we don't have access to all the NPM modules and core Node libraries you usually do. It's worth mentioning here that Vercel and other tools like Deno and Cloudflare are going out of their way to make a lot of core Node libraries available on the edge. The edge moves fast, and what is possible is increasing every week.

Edge functions also need to be small and lightweight. Current caps in Vercel edge functions as of writing this blog:

* Code size limit: 1 - 4 MB
    
* Maximum memory usage of 128MB
    
* The initial response must be within 30 seconds
    

You can find the complete list of [limitations here](https://vercel.com/docs/concepts/functions/edge-functions/limitations) if they after publishing this blog. Of course, serverless functions on Vercel on not limited to this setup. Consider these limitations when building server-side code in an edge function over a serverless function.

## Database on the Edge

So edge functions are great for creating or processing stateless content, but what about when we need to keep hold of the state? What if we need a database? For those of you with experience with databases, you might be yelling at me right now. Distributed databases are complex and can cause a lot of issues. Heck, even serverless functions and databases can cause problems. Before we jump straight into the bleeding edge of a DB on the edge, let's step back and look at databases in each setup.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681375649407/3b583543-f6dd-40ff-b194-968d021e721a.jpeg align="center")

Traditional servers and databases are set up close together. You want to keep a database close to the server making the requests due to bandwidth, data caching, and limiting latency. With this setup, your server on start will spin up a connection to the database and create a pool of connections. The pool is then used to make requests to and from the database. Were simplifying this, but how pools and database connections work is another blog post.

With serverless functions, you create a connection and cache it. When the serverless function is called, it checks whether the connection exists (in the cache) and makes the DB call. If the connection does not exist, it makes a new one. Like the traditional server setup, we also locate the function as close as possible to the DB. There is a considerable drawback here. If the serverless function has not been active for a while, you get the latency from the function cold start and more latency from creating the database connection.

Now with edge functions? Wait, we have limits on the size of our code, and we don't have access to all the same libraries as Node. How do we connect a database? Say hello to HTTP database connections—no database connection creation adding to your cold start latency. Let's look at two options, MongoDB and PlanetScale, but plenty of others exist.

MongoDB Atlas has a traditional database and a serverless database setup. Only pay for what you use and let them manage the database. The best part of serverless is that there is less to manage, meaning you can do more with less. I work with MongoDB daily, so it has a special place in my heart. Set up your MongoDB Atlas cluster to accept HTTP accept requests via their [data API](https://www.mongodb.com/blog/post/introducing-mongodb-atlas-data-api-now-available-preview), and you can start reading and writing data from your edge locations without a database driver.

[PlanetScale](https://planetscale.com) is dropping serverless MySQL. Like MongoDB Atlas, they will handle the database. Seriously who wants to scale a database? I like learning how that works under the hood and playing with it in my spare time—no way I want to scale a database in real time with a small team.

PlanetScale has taken things further and built a Fetch-based JavaScript library for serverless functions and the edge. You may think each request still has to go back to the database, making the request slow. However, PlanetScale has gone to considerable lengths to work on a special cache and create global routing. The routing works like a CDN. When a client connects from an edge location, it will connect to PlanetScale's closest edge location. The request then uses long-held connection pools over their internal network to reach the destination, resulting in speedy connections. Combining this with caching on the edge and the compute being close to your users, we can achieve some quick DB connections on the edge.

We are seeing a massive jump in what is possible with edge computing; it's like serverless on steroids. The low latency and ability to run and connect to many things on the edge means you can do much. However, there is a severe gotcha with running the database on the edge. With a database, you should always try locating the compute as close as possible to the database. There are a few reasons for this, but the main one is you usually have to make multiple requests to a database for every function or endpoint invocation. If the edge function is doing the compute and your database is in a fixed location, every time it makes a request, it has to go back and forth. The constant back and forth will add huge latency to your request. You are creating a worse user experience and a super slow connection. Think about it carefully. If your database is in Sydney, but a user in Europe hits your edge function, each DB call goes back and further between Sydney and the edge function in the EU. If the compute were located with the DB in Syndey, it would only be one round trip versus many.

You need to keep the location of your compute and database in mind when deploying edge functions. Vercel talks about this in length and offers [regional edge functions](https://vercel.com/blog/regional-execution-for-ultra-low-latency-rendering-at-the-edge). These regional functions allow you to take advantage of the edge but still locate compute near your database. Cloudflare also offers something called [Smart Placement](https://developers.cloudflare.com/workers/platform/smart-placement/) to minimise latency.

Another great thing about tools like NextJS is they allow you to opt-in at the route level to what type of compute you use. You can choose between serverless and edge using a config in your project. You can use the best tools for each API route or function. Always think about where you're compute and your data are located. Sometimes the location of data may mean the edge is not suitable for your use case. Maybe the new database tools and opt-in config are all you need.

## Wait, I need more

So our web apps can do a lot now. We have a database and middleware, and it's also serverless running on the edge. What more could I need? Maybe you need to run Cron Jobs?

Another pitfall of the serverless/edge setup is the subscription costs. For some projects, you constantly need something that a standard server could do in seconds, but as you're running serverless, you reach for another service. Before you know it, you're up to your eyeballs in monthly subscriptions, and it would have been cheaper to spin up a dedicated server. Something to watch out for, but most of the time, this is offset by the savings from running serverless infrastructure.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679732804313/20642c21-39c2-4b28-996f-94d0e56a3b80.jpeg align="center")

So you need to run a Cron Job; the edge can do that too. CloudFlare workers have a [Cron Trigger](https://developers.cloudflare.com/workers/platform/triggers/cron-triggers/) that lets you easily pull this off. However, say it's getting more complicated, and you need to start triggering background jobs when certain events happen. Tools like [Inngest](https://www.inngest.com) make it easy to define functions triggered by events from your app or anywhere on the internet.

## Building an API

So we have discussed how great the edge is and how much you can build. However, maybe you now need a mobile app. Perhaps you have a situation like my work; we have a web app, but some clients integrate our API into their software. So it is time to decouple the backend code from your web app project and turn it into an API.

Now, this is where the use cases for edge computing start to fall apart. Don't get me wrong, you can still pull it off, and it will work. Right now, we can spin up Deno and build a wicked-fast API that resembles APIs built with Node/Express, Ruby on Rails, Python and others. We can connect to PlanetScale or MongoDB Atlas. We could connect Firebase or Supabase for our DB and other functions. Before you know it, we have a functional API running on the edge using [Deno Deploy](https://deno.com/deploy). We got to give credit to Deno here for how easy it is to build stuff in TypeScript, test and deploy. I love Deno so much. The cuteness of their logo also makes me want to use nothing else.

On a side note, and nothing to do with edge computing. Deno has this [artwork page](https://deno.land/artwork) that is fun to look at. Deno Simpson slays me.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680939860004/8387a5cf-06f7-4471-8676-dc1db0e7c29d.png align="center")

However, what if your data needs to be in a fixed location? What if you have other services to interact with that are also in set locations? We're starting to hit issues here where latency improvements might not be worth the trade-off of building larger distributed systems. Even building microservices that run next to each other is complicated in certain situations. Sometimes creating and uploading your API to AWS or Azure is easier.

I am focusing on AWS, where I spend most of my time. We can still take advantage of a serverless setup. I always use serverless setups to spin up Docker images on ECS. I use serverless functions like AWS Lambda to build APIs all the time. I have forgotten how to spin up and provision an EC2 instance to run a web app or API server. However, the edge does not have to end here. You can use edge optimise endpoints when connecting your API from ECS or Lambdas to your API gateway.

## Conclusion

The edge is an exciting space. So much is happening, and what is possible is changing daily. You can build incredibly responsive products for your users using the edge combined with Netlify or Vercel with frameworks like NextJS or SvelteKit. You can build systems that scale effortlessly and products faster than ever. You no longer have to think about how everything works under the hood and maintain that. Serverless and the edge empower us to deliver better products and focus more on the core logic of our product, not infrastructure.

If you are building the web today, take advantage of the edge. If you are making more than a web app going full edge might not be the proper use case. However, it is becoming a tool that any setup should use. Remember, always think about where you place your data and compute.