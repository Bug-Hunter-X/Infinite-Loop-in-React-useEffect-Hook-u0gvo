# React useEffect Infinite Loop Bug

This repository demonstrates a common error in React applications involving nested `useEffect` hooks that leads to an infinite loop. The inner `useEffect`'s dependency array incorrectly includes `count`, causing it to re-run whenever `count` updates, leading to a continuous loop. 

## Bug Description
The issue occurs when a `useEffect` hook is placed inside another `useEffect` hook.  The inner `useEffect` uses the count state variable in its dependency array, triggering re-renders even when not intended, leading to the infinite loop. 

## Solution
The solution involves carefully analyzing the dependencies of the inner `useEffect` hook. The correct approach is to remove `count` from its dependency array if the side effect doesn't depend on the current `count`. If it should only run once, the empty array `[]` should be used.