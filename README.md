# Express.js: Handling Empty or Invalid JSON Request Bodies

This repository demonstrates a common issue in Express.js applications where the server fails to correctly handle empty or invalid JSON request bodies.  The problem occurs because `express.json()` doesn't provide explicit error handling for malformed JSON.  This leads to unexpected behavior where an empty object is logged instead of a proper error response.

The `bug.js` file shows the problematic code, and `bugSolution.js` presents a solution that addresses this by adding error handling to properly manage and respond to these scenarios.

## Problem

The default `express.json()` middleware parses JSON requests but doesn't explicitly handle cases where the request body is empty or contains malformed JSON.  This leads to a silent failure and potentially inconsistent application behavior.

## Solution

The solution uses a custom middleware function to wrap `express.json()` and handle errors explicitly.  This middleware intercepts parsing errors, allowing the server to respond with an appropriate error message (e.g., a 400 Bad Request) instead of proceeding with an empty object.