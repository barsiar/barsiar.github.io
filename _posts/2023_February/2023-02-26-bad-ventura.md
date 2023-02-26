---
date: 2023-02-26
title: How to Return Edit Mode for Screenshots in MacOS Ventura
---

If you are a MacBook user and rely on screenshots, you might have noticed a change in the way screenshots work after upgrading to macOS Ventura. The edit mode, which was previously accessible with a single click, now requires two additional clicks. This might be frustrating if you are used to the previous workflow.

In this article, we'll show you how to write an AppleScript and replace the standard key combination with this script to restore the "default" behavior.

<!-- more -->

The purpose of an AppleScript is to automate tasks and control applications on a Mac computer. It uses a scripting language to communicate with the operating system and other applications, allowing you to automate repetitive tasks, control the behavior of applications, and access information from the web or other sources. It can be saved as a script file or used in Automator workflows to extend the functionality of your Mac.

## Step 1: Create the AppleScript

Open the Automator tool.

![](/images/Automator.png)

Create new "Quick Action".

Paste the following script into your workflow, replacing my username (`set username to "siarhei"`) with yours (the user's home directory name):

```
set username to "siarhei"
set screenPath to ("/Users/" & username & "/Desktop/Screenshot " & (do shell script "date +'%Y-%m-%d at %H.%M.%S'") & ".png")

do shell script "screencapture -imp \"" & screenPath & "\""

set timeoutSeconds to 5
set endDate to (current date) + timeoutSeconds
try
	tell application "System Events"
		repeat until (exists window "Screenshot" of application process "screencaptureui")
			delay 1
		end repeat
	end tell
	activate
on error errorMessage
	if ((current date) > endDate) then
		return
	end if
end try

-- Click the “Markup” button.

try
	tell application "System Events"
		click UI element 3 of window "Screenshot" of application process "screencaptureui"
	end tell
on error errorMessage
	if ((current date) > endDate) then
		return
	end if
end try

repeat
	try
		tell application "System Events"
			click checkbox 1 of window "Screenshot" of application process "screencaptureui"
		end tell
		exit repeat
	on error errorMessage
		if ((current date) > endDate) then
			return
		end if
	end try
end repeat
```

Save the quick action.

## Step 2: Replace the Standard Key Combination

1. Open the System Settings.
2. Disable the default keyboard shortcut for screenshots in Keyboard -> Keyboard Shortcuts -> Screenshots:
   ![](/images/Disable_Standard_Screenshots.png)
3. Assign a new keyboard shortcut to the Automator script in System Preferences -> Keyboard -> Keyboard Shortcuts -> Services -> General:
    ![](/images/Screenshot_Replacement.png)
4. Give access to the Automator script in System Settings -> Privacy & Security -> Accessibility.

### Conclusion
By following these steps, you can easily restore the "default" behavior of screenshots in macOS Ventura, making it more convenient and efficient to capture and edit screenshots on your MacBook.

The script and the steps described have been tested and verified to work on macOS Ventura.

That's it!