#How to: Use CCLog to Debug#

**Symptoms**

No log output of projects based on Framework . 

**Cause**

Cocos has a Debug version for debugging and a Release version for distribution.  Debug version provides log output while no log output from precompiled libraries of Release version.

**Resolution**

To solve this issue and use debug log,  take the following interface description for reference.

cpp : log(“any string”)

lua : release_print(“any string”)

js : console.log("any string")
