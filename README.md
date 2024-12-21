# Firebase Data Race Condition with Multiple Listeners

This repository demonstrates an uncommon error in Firebase: a race condition caused by having multiple real-time listeners attached to the same data path.  This can lead to unexpected data inconsistencies and behavior, as changes to the data might not be processed correctly.

## Problem

The `bug.js` file showcases the problem.  Two `on('value')` listeners are added to the same Firebase database path.  Due to the asynchronous nature of data updates and the potential for listener callbacks to run in unpredictable order, actions performed in each listener might observe different data states, leading to issues.  Data inconsistencies may occur, and the intended operations might not function as expected.

## Solution

The `bugSolution.js` file provides a solution. Instead of using multiple listeners, it uses a single listener and performs all necessary actions within a single callback.  This prevents race conditions because the data is always processed in the correct order, ensuring data consistency.  More efficient data handling is also achieved by reducing the number of listener callbacks.