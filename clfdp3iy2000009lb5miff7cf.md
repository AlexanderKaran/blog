---
title: "WTF is Edge Computing"
seoTitle: "What is edge computing, and how does it work?"
seoDescription: "What is edge computing? A dive into the history of edge computing and how it works."
datePublished: Sat Mar 18 2023 08:16:36 GMT+0000 (Coordinated Universal Time)
cuid: clfdp3iy2000009lb5miff7cf
slug: wtf-is-edge-computing
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678000553634/e78b4c62-e2ce-410f-8758-817cf3390970.png
tags: cloud, javascript, networking, edgecomputing

---

What is edge computing? What do those words even mean? With all the hype around AI unleashed on our Twitter and LinkedIn feeds, it may be hard to remember that edge computing was the new bandwagon we needed to jump on not long ago. However, before we jump, we should learn what edge computing is. Edge computing does not refer to any particular technology; it's architecture. A distributed programming pattern that is location sensitive with a focus on where things are placed in the network. The short and easy answer is edge computing is running code and storing data as close to the end user as possible. However, I prefer the long answer with some history, so let's dig into it.

## Where did it all start?

When looking at modern tools like Deno Deploy, Vercel Edge functions or CloudFlare workers, they talk about running the code as close to the end user as possible. Web frameworks now proudly wear the badge "edge ready". These new tools are great additions to the web development tool belt. However, sometimes we talk about this stuff as if it is brand new rather than just building on and improving on what has come before. Edge computing is touted as powerful computing with no latency, but the truth is the edge has been there for a long time. I go there after a few coffees.

%[https://media.giphy.com/media/oZEBLugoTthxS/giphy.gif] 

If we rewind the clocks back to the military-funded Internet that connected four universities in northern America, we can find the first server set up. Servers were introduced as a concept in an [RFC from the Networking Working Group](https://www.rfc-editor.org/rfc/rfc5.html). The RFC laid out instructions on transmitting and receiving data between a server host and a user on the ARPANET (military-funded Internet connecting the four universities). An [IBM 360/91](https://en.wikipedia.org/wiki/IBM_System/360_Model_91) computer provided production computing services to ARPANET users, the first internet server. Since then, hardware and software have changed, but this setup is still essential how servers run today. However, you don't need to buy them yourself anymore and set them up from scratch, thank god.

As the Internet grew, this initial setup started to run into issues, so CDNs were created. Content delivery networks (CDNs) began in the late 90s to serve content closer to the end users. CDNs would be positioned in key locations worldwide and cache web content, images, video and more. Traditional servers or data centres would be at one or more locations, and each request would be routed to the server. With CDNs, the content is distributed across the CDNs network and traffic is routed and optimised to the closest server in the CDN.

CDNs are the start of edge computing, your storing content as close as possible to the user. However, you could only store static content like HTML, CSS, images, and videos on a CDN. Dynamically generated content still came from the main servers.

In the early 2000s, these networks evolved and could host applications leading to the first edge computing services. You may wonder if it has always been there: why is there such a push for it now? The truth is technology and infrastructure have got a lot better. It's now easier to build for the edge than ever before. Let's keep digging because there is more to the edge network than just CDNs.

## The Rise of the iPhone

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678452602287/6677e0cd-c6a8-44e7-b01c-cc2588236f0c.jpeg align="center")

What are you talking about, Alexander? An iPhone, what has that got to do with edge computing? The adaption and growth of smartphones mean a huge chunk of the human population is walking around with more computing power in their pockets than a base laptop. How is a smartphone part of edge computing? Let's take a closer look at the iPhone. Apple does encryption and biometrics on the phone, saving their main servers from having to do it. Apple deploys, updates and manages this code. The iPhone is the start of Apple's network. Smartphones are part of edge computing. When building an app, you can take advantage of the hardware and functionality of the device. You can process data such as images and video, run ML models and more before anything touches your primary server. If we count smartphones as part of the edge network, what about all those other smart devices in your home?

## IoT

The Internet of things (IoT) stands for physical devices that run software and exchange data across the Internet and with each other. Everything from smart speakers, temperature sensors, air quality monitors and more. All these devices run software, process data, and receive software updates from the companies that manage them. Some IoT devices even run ML models. Edge computing is more than running your website next to your end users. There is no clear interpretation of edge computing, so you could argue I am wrong. iPhones and IoT are not part of the edge network; however, if you step back, all these devices are part of the network and don't just have to be used for pushing and reading data. At its core, edge computing is an approach to architecture, not necessarily a specific technology or tech stack.

## Frameworks on the Edge

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678452955104/d0699db6-9a9d-4f82-b696-c5f7b1af3c0d.png align="center")

Over the past few years, companies and organisations have been rolling out edge functions and edge-ready frameworks so we can run code as close as possible to our users. What does any of this mean, though? Let's break it down by looking at edge functions which start with serverless functions.

Serverless is a way of running code only when it is needed. With a traditional server, you pay for every second it runs, even if it's only being called for a few hours daily. Before I get hit with a tidal wave of sometimes this is what you need, Alexander. Serverless is not required for everything, I agree. But we're talking about history here and what edge computing is. We can save the pros and cons for the next blog post. Serverless functions lead to the rise of only paying for what you use -focusing on writing business logic, not managing servers. AWS Lambda is a popular serverless function provider. I have built a whole API on them. They're great and easy to use. However, they come with a few tradeoffs, including cold starts. As the server is not always running, sometimes, on a request, they have to provision all the resources they need to work, adding to the latency of the request.

Now edge functions combine serverless functions but run them as close as possible to the user on the edge network, unlike traditional serverless functions that still are hosted in one or two data centres. Edge functions get spread out across the edge network. The edge is where serverless and CDNs combine to create fast-running code close to the user. It also removes headaches from setting up and looking after servers. Cold start times for edge functions are also smaller than standard serverless functions.

Now web frameworks such as SvelteKit, Deno's Fresh and many others are taking advantage of the CDNs and edge functions. You can now build websites and apps using these frameworks that run on the edge. The app is not hosted in a primary server somewhere but worldwide on the edge network.

## Why do we need it?

Why do we need edge computing, and why is it so important? The simple answer is speed and data. These days, web apps and sites are growing in size and doing more than ever. Some web apps can be incredibly resource intensive on the end user's machine, and only some people have the latest devices. Running more of the compute on the edge means we use less CPU and memory of the end user's machine. Due to performing more computing on the edge, we can also send less data reducing the bandwidth used. We are preventing the dreaded spinning wheel of death for our end users.

Edge computing is the next evolution of our network. By 2025 the world's data will grow to 175 zettabytes (1 zettabyte is 1 billion terabytes). The increase of IoT devices, smartphones and other equipment sending and receiving data from the cloud will limit the world's bandwidth. We have seen considerable improvements in network technology, but traditional cloud centres might not be able to guarantee acceptable data transfer rates at this current growth. Edge computing is the answer to this problem. By decentralising data and programs across the edge network, we can ensure that we use less bandwidth and transfer rates stay at a reasonable speed. We even see companies building databases that run on the edge network.

Edge computing doesn't mean that everything needs to run on the edge or that regular servers are no longer needed, but you can see its advantages. Let's do a test to see how fast an edge function can be. I will spin up a serverless function on AWS Lambda in Syndey, Australia. Sydney is the closest data centre to where I live. Then I will spin up the same function on Deno Deploy across the edge network. Here is the code:

```javascript
// Deno Code

import { serve } from "https://deno.land/std@0.177.0/http/server.ts";


const json = await JSON.stringify({
            v: 1,
            data: {
                id: "1",
                type: "users",
                properties: {
                    name: "Alexander Karan",
                    age: 32
                }
            }
        });

serve((req: Request) => new Response(json, {status: 200}));
```

```javascript
// AWS Lambda Node

export const handler = async(event) => {
    const response = {
        statusCode: 200,
        body: {
            v: 1,
            data: {
                id: "1",
                type: "users",
                properties: {
                    name: "Alexander Karan",
                    age: 32
                }
            }
        }
    };
    return response;
};
```

Now if I ping both these endpoints from my home town in Perth, Australia, there is a 1ms difference. Hold up? Don't worry; using my home town location is a bad example. Perth is the most isolated city in the world. The closest edge location is almost as far away as the central AWS server in Australia. Let's turn on a VPN and set my location to Germany:

| URL | Min (ms) | Avg (ms) | Max (ms) |
| --- | --- | --- | --- |
| Edge Function | 346.774 | 355.210 | 379.937 |
| Lambda | 622.700 | 666.668 | 767.349 |

Of course, this request has to come back to me in Australia, but you can see the difference between the two functions. The Lambda in Sydney has to go from Syndey to the VPN in Germany and back to me in Perth. The Edge Function gets called from a closer location in Germany.

Let's set my location to the US to get one more test:

| URL | Min (ms) | Avg (ms) | Max (ms) |
| --- | --- | --- | --- |
| Edge Function | 227.001 | 231.335 | 247.544 |
| Lambda | 363.824 | 369.932 | 448.918 |

Once again, the Edge Function is faster as my traffic hits the VPN in the US and then hits an Edge location there rather than returning to Australia. It's still incredible we have web traffic coming from the US and back to Australia that fast. Technology really is cool sometimes.

If you have any questions about what I cover in this post, please message me here or on Twitter. My next post will cover practical uses for edge computing and when you shouldn't use it.