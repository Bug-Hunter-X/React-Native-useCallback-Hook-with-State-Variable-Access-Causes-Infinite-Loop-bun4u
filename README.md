# React Native useCallback Hook Issue: Infinite Loop with State Variable Access

This repository demonstrates a common issue encountered when using the `useCallback` hook in React Native. When a function within `useCallback` accesses a state variable or prop that changes on every render, the function isn't correctly memoized, leading to an infinite loop. 

The `bug.js` file showcases this problem. The `incrementCounter` function, despite being wrapped in `useCallback`, recreates itself every time the state changes because it relies on the `count` state variable. This constant recreation triggers re-renders, creating a cycle. 

The `bugSolution.js` file provides a solution, demonstrating how to correctly memoize the function using dependencies within `useCallback`. By only including the `count` state variable as a dependency when it actually changes, the function is only re-created when necessary.