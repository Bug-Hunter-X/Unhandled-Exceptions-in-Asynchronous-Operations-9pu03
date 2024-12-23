# Unhandled Exceptions in Asynchronous Dart Operations

This repository demonstrates a common error in Dart where exceptions during asynchronous operations (like network requests or JSON decoding) are not properly handled.  The missing `rethrow` statement can lead to silent failures, making debugging difficult.

## The Problem
The `fetchData` function attempts to fetch data from an API.  If any error occurs (network issues, invalid JSON, etc.), the `catch` block prints an error message but doesn't propagate the exception.  This means that the calling function might not be aware of the failure, leading to unexpected behavior.

## The Solution
Adding `rethrow` to the `catch` block ensures that the exception is propagated back up the call stack.  This allows higher-level functions to handle the error appropriately (e.g., displaying an error message to the user, retrying the operation, or gracefully exiting).