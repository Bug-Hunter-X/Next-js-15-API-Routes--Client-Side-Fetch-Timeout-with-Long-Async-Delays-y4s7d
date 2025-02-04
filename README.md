# Next.js 15 API Routes: Client-Side Fetch Timeout with Long Async Delays

This repository demonstrates a potential issue in Next.js 15 where client-side fetch requests can timeout when interacting with API routes containing `async` functions that have significant delays, even if the server successfully processes the request.

## Problem Description

The `pages/api/data.js` API route simulates a long delay (2 seconds) using `setTimeout`.  The `pages/index.js` component fetches data from this API route. If the network is slow or the delay is sufficiently long, the client-side fetch can timeout before receiving a response, resulting in a network error in the client, despite the API route eventually completing successfully.

## Solution

The solution involves implementing a timeout on the client-side fetch request using a `AbortController` and adjusting the timeout accordingly. 
