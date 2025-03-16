---
{"dg-publish":true,"permalink":"/homelab/backblaze-backup-network-drive/"}
---


The Dokan method still works in 2023. Thanks so much! Some minor adjustments required for me.

```
mirror.exe /r \\fileserver\sharename /l z
```

/r instead of /u worked for me.

After installing the latest release of [DokanSetup.exe](https://github.com/dokan-dev/dokany/releases), I have this setup to run on boot using the Windows Task Scheduler. Here are the instructions.

1. Press "Windows key + R" to open the Run dialog box, and type "taskschd.msc" to open the Task Scheduler.
2. Click "Create Task" on the right-hand side of the window.
3. In the "Create Task" window, give the task a name and select the "Run with highest privileges" option.
4. Click the "Triggers" tab and click "New" to create a new trigger. 
5. Select "At startup" from the "Begin the task" dropdown menu.
6. Click the "Actions" tab and click "New" to create a new action.
7. In the "New Action" window, select "Start a program" as the action type.
8. In the "Program/script" field, enter the path to the mirror.exe file. In my case that is:
    ```
     "C:\Program Files\Dokan\Dokan Library-2.0.6\sample\mirror\mirror.exe"
    ```
9. In the "Add arguments (optional)" field, add:
    ```
     /r \\fileserver\sharename /l z
    ```

Replace fileserver and sharename with the actual SMB share names, and "z" is the drive letter you wish to use.

10. Click "OK" to save the action.

11. Give the task a Name in the General tab. "Map Network Drive with Dokan" for example.

12. At the bottom, choose "Run whether user is logged on or not" and leave "Do not store password" unchecked.

13. Click "OK" again to save the task. It should prompt to enter your password.

14. Restart your computer, and the task should automatically run and map your server as a local drive.

If you want to rename the drive you will need to add another task with action and have a slight delay (have it run on Log On should work). Program/script to be

```
C:\Windows\System32\cmd.exe
```

and Add arguments (optional) to be

```
/c label Z: drivename
```

where drivename is whatever you want it to be.

Some additional notes:

1. After configuring the above, Backblaze throws a "no read-write" error when trying to add the drive in the software. The strange thing is that it does create the .bzvol folder. I found simply trying to click the checkbox 2 or 3 more times eventually works and the drive is selected.

2. The Backblaze software kept crashing when attempting to "scan your hard drives" when it was over my actual LAN network to a separate PC. However, it does work when running Windows inside of a VM directly on the Unraid server (still have to map with Dokan).

3. I set the Backblaze exe's to run as administrator.