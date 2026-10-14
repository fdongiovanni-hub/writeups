# Removing the shortcut arrow on Windows

A quick guide to hiding the shortcut arrow icon on the Windows Desktop by replacing it with a transparent icon via the System Registry.

## How it works

1. **Opened the Registry Editor (`regedit`)**  
   Accesses the Windows central database, which contains all settings, preferences, and configs for the OS and installed programs.

2. **Navigated to the Graphics Management Key**  
   Moved to path:
   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer`  
   The **Explorer** folder manages everything related to the on-screen user interface (including desktop, taskbar, and icon appearances).

3. **Created `Shell Icons`**  
   Added this new folder to provide custom instructions for icon appearances (predefined name), overriding the default Windows rules.

4. **Isolated Element `29`**  
   Created a new string value named **29**, the unique ID that identifies the shortcut link arrow.

5. **Injected the Transparent Icon**  
   Inserted the value:  
   `%windir%\System32\shell32.dll,-50`  
   This tells Windows to pull icon number **-50** (which is a completely transparent, empty square) from the standard icon library (`shell32.dll`) and use it for all shortcut arrows. The arrow is still there, but invisible.

6. **Restarted Windows Explorer**  
   Since Windows does not read the registry in real-time, restarting the `explorer.exe` process (via Task Manager) forces the system to reload the graphics cache and apply the new settings immediately.
