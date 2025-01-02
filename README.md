# setTimeout Closure in TypeScript Loop

This repository demonstrates a common issue encountered when using `setTimeout` within a loop in TypeScript (and JavaScript). The problem arises due to how closures interact with the loop variable.

## The Bug

The `printNumbers2` function attempts to print numbers 1 through 5 using `setTimeout` to simulate asynchronous behavior. However, it unexpectedly prints '6' five times.

## The Reason

The closure created by the `setTimeout` callback function captures the value of `i` *after* the loop has completed.  By the time the `setTimeout` callbacks finally execute, `i` is 6, and this value is printed five times.  This is because `setTimeout` is asynchronous, and the loop completes before the `setTimeout` callbacks have a chance to run.

## The Solution

The solution involves using a closure that immediately captures the value of `i` within the loop iteration using an immediately invoked function expression (IIFE).