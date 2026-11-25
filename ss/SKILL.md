---
name: ss
description: Grab the latest screenshot from the owner's machine (macOS, Windows, or Linux) and look at it. Use when the owner says /ss or asks to look at their latest screenshot.
---

# ss

1. Detect the OS from the runtime line (macOS, Windows, Linux).
2. Look for the newest image (png, jpg, jpeg) in the folders for that OS, newest modified time wins:
   - macOS: the folder from `defaults read com.apple.screencapture location` if set, else ~/Desktop. Names start with "Screenshot" or "Screen Shot".
   - Windows: %USERPROFILE%\\Pictures\\Screenshots, then %USERPROFILE%\\OneDrive\\Pictures\\Screenshots, then Desktop.
   - Linux: ~/Pictures/Screenshots, ~/Pictures, then Desktop (use xdg-user-dir PICTURES / DESKTOP if available).
   Example (macOS/Linux): `ls -t <folder>`. Example (Windows): `dir /o-d /b <folder>`.
3. Load the file with `view_image` using its full path.
4. Reply briefly with what you see and act on any text sent with /ss. If none, describe it in one or two lines and ask what they want.
5. If the newest file is older than about 10 minutes, say so with its time.
6. If no folder has one, say which folders you checked and ask where screenshots are saved.
7. Never move, delete, or edit the file.
