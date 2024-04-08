# Enable Microphone Access On Vesktop for MacOS [Unofficial method created by @SpinnySpiwal on Discord]

# :warning: Warning :warning: 
You should be experienced with macOS and familliar with the terminal to follow this guide.

:warning:  SIP Disable Warning :warning: 
Disabling SIP or System Integrity Protection is dangerous to your machine when disabled and forgotten about. You must re-enable it after.

# Step 1 ~ Open Terminal
Press ⌘ + Space and type "Terminal" and press ⏎ 
You should be greeted with a terminal!

# Step 2 ~ Check if SIP is enabled
In your terminal, copy or type the following:
```sh
csrutil status
```

Then should follow an output:
```
System Integrity Protection status: enabled/disabled.
```

If it says enabled, follow step 3 and 4. If it says disabled, skip to step 5.

# Step 3 ~ Get Into Recovery Mode to Disable SIP.
To disable SIP, you must power off your mac to enter recovery mode.
After you power off your mac, press and hold the power button until you see continue holding for startup options.
Continue holding until the text changes to "Loading startup options..."

You will then see a UI Which shows:
"Macintosh HD" "Settings"
Click Settings. Wait for it to load, and then click a user you know the password for (must be an admin account) and type in the password.

:warning:  SIP Disable Warning :warning: 
Disabling SIP or System Integrity Protection is dangerous to your machine when disabled and forgotten about. You must re-enable it after.

# Step 4 ~ Disabling SIP
Now press these three keys together:
⌘ + ⇧ + T

You should once again be greeted by a terminal.
Type this command out exactly as follows.
```sh
csrutil disable
```
type Y if it asks for yes/no and type a password if it asks for one.

Congratulations, you successfully disabled SIP!

Now type:
```sh
reboot
```
Into your terminal to reboot! And log back in.

# Step 5 ~ Create a backup of TCC.db

Now follow step 1 to open Terminal again.
Now you have opened Terminal again, COPY/PASTE the following:
```sh
cp "~/Library/Application Support/com.apple.TCC/TCC.db" "~/Downloads/TCC.db.bak"
```

```sh
sqlite3 "~/Library/Application Support/com.apple.TCC/TCC.db"
```

Now COPY/PASTE the following:
```sql
insert into access
values
('kTCCServiceMicrophone','dev.vencord.vesktop', 0, 2, 2, 1, null, null, null, 'UNUSED', null, null, 1669648527, 0, 0, 0, 0)
```
And then press enter.

And finally, type:
```sql
.quit
```

# Step 6 ~ Check it's actually working now.
Open Vesktop and try unmuting, it'll work now!
You did it!! Congratulations!

# Step 7 ~ Re-Enable SIP
Follow Step 3 to re-enter Recovery Mode and get back to the terminal.

Now type:
```sh
csrutil enable
```
Again if it asks Y/N type Y and if it asks for a password, enter it.

Now type:
```
reboot
```
And log back in!

Yay! You did it! You officially enabled your Microphone on Vesktop!

If you messed something up, that is not my responsibility. As it says you must have a good understanding of MacOS to follow my guide.
If you need help, contact me on Discord @SpinnySpiwal! Thanks for reading! Also just because it isn't my responsibility does not mean I won't
help you resolve your issue.
