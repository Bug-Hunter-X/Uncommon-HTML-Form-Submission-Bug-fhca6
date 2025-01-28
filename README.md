# Uncommon HTML Form Submission Bug

This repository demonstrates a subtle bug related to HTML form submissions and the `preventDefault()` method.  The issue arises from a misunderstanding of event order and how `preventDefault()` interacts with form submission.

## Bug Description

Even with `event.preventDefault()` in place to prevent default form submission behavior, the form *appears* to submit under certain conditions, leading to unexpected page reloads.

## How to Reproduce

1. Clone this repository.
2. Open `bug.html` in your web browser.
3. Fill out the form and click "Submit".
4. Observe that the console logs 'Form submitted!', but the page still reloads unexpectedly (if the default action of a submit button is to reload the page)  This is the uncommon behavior.  The expected behavior is that the page will not reload.

## Solution

The solution lies in ensuring that any asynchronous operations (like AJAX calls) needed to handle the form submission are completed *before* the default action is prevented.  In `solution.html`, the default action is prevented after an asynchronous operation(simulated via a delay using `setTimeout`) is finished.
