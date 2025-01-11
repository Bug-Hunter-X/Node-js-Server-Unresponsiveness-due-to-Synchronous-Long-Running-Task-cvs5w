# Node.js Server Unresponsiveness

This repository demonstrates a common issue in Node.js where a server becomes unresponsive due to a long-running synchronous operation within the request handler. The provided `server.js` demonstrates the problem, while `server-fixed.js` shows a solution using asynchronous operations.

## Problem

The `server.js` file creates a simple HTTP server. However, the request handler includes a `while` loop that keeps the CPU busy for 5 seconds.  During this time, the server is unable to respond to any other requests, leading to unresponsiveness.

## Solution

The `server-fixed.js` file demonstrates a solution that avoids blocking the event loop by using asynchronous operations.  It utilizes `setTimeout` to simulate a long-running task without blocking the main thread.

## How to reproduce the problem

1. Clone the repository.
2. Navigate to the project directory.
3. Run `node server.js`.
4. Open multiple browser tabs and attempt to access `http://localhost:3000`.  Notice that only one request will be processed until the long task completes.

## How to test the solution

1. Run `node server-fixed.js`.
2. Open multiple browser tabs and access `http://localhost:3000`.  You will find that all requests are handled concurrently without delays.