# experiment_balboa
Balboa Partner Sub Demo site for Balboa employees to modify front end site code via claude and send data exclusively to that Pendo instance (not available to Pendo employees)

# Experiment Balboa

Balboa's training sandbox for writing and testing Pendo track events.

**Live site:** https://<your-username>.github.io/<repo-name>/

## What it's for
- Practice `pendo.track()` from the browser console
- "Read more" buttons sit inside two shadow DOM layers, mirroring client apps
- Events land in Balboa's dedicated Pendo instance, not client or Pendo data

## How to use it
1. Open the live site and sign in with your name (visitor ID becomes `balboa-your-name`)
2. Open DevTools > Console and run `pendo.enableDebugging()`
3. Fire events, then check the debugger Events tab and Pendo's Track Events page
4. Use Account > Log out to reset the session

## Editing
All app code is in `index.html`. Track event handlers live in the
"TRACK EVENT PRACTICE ZONE" block at the bottom of the file.
