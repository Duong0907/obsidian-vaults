**Check the proxy settings:**

1. Press "Windows + R", type "inetcpl.cpl", and click Ok.
2. Select the "Connections" tab and click on "LAN Settings";
3. Uncheck "Automatically detect settings";
4. Also, uncheck the option "Use a proxy server for your LAN..." if checked;
5. Click OK in both windows.

See if the issue is resolved.

**If it persists, reset the network settings as instructed below:**

1. Press "Windows + I" and select "Network & Internet > Advanced network settings";
2. Select "Network Reset";
3. Select "Reset Now", and at the confirmation screen, select "Yes";

<aside>
💡

**Note:** The PC will need to be restarted.

</aside>

1. Now open Start and type cmd;
2. Right-click on "Command Prompt" in the result list and select "Run as administrator";
3. At the Command Prompt, type the following commands one at a time and press Enter:

```json
netsh int ip reset

netsh winsock reset

ipconfig /release

ipconfig /renew

ipconfig /flushdns
```

1. Restart your PC and see if the issue is resolved.