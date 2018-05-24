# DisableWinTracking
This program cannot run correctly from a file path that contains Cyrillic characters. Make sure to run it from your root folder (usually C:/ ) so that you don't get runtime errors.

You can either:

A. Run the binary uploaded to the Release tab as an Administrator and select which options you'd like

B. Install Python and the dependencies listed below and run the script from an elevated command prompt and select which options you'd like
Silent

Either can be run with the -silent argument as of v3.1. This will perform all available options of the version you're using.

You still need to run it as administrator.

Dependencies

This is only to run the script from source, download the exe here

    Tested on Python 2.7
    wxPython -- GUI (Tested with wxPython=Phoenix)
    PyWin32
    Windows 10 (Duh)

Methods Used
Telemetry

Set the AllowTelemetry string in HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\DataCollection to 0
DiagTrack Log

Clears and disables writing to the log located in C:\ProgramData\Microsoft\Diagnosis\ETLLogs\AutoLogger
Services

You can delete or disable the 2 services below:

    DiagTrack Diagnostics Tracking Service
    dmwappushsvc WAP Push Message Routing Service

Action:

    Delete: Remove both services
    Disable: Set the Start registry key for both services to 4 (Disabled) Located at HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\

HOSTS

Append known tracking domains to the HOSTS file located in C:\Windows\System32\drivers\etc
IP Blocking

Blocks known tracking IPs with the Windows Firewall. The rules are named TrackingIPX, replacing X with the IP numbers.
Windows Defender

Disables the following:

    Automatic Sample Submission
    Delivery Optimization Download Mode

WifiSense

Disables the following:

    Credential Share
    Open-ness

OneDrive

Runs C:\Windows\SysWOW64\OneDriveSetup.exe /uninstall (64 bit) or
C:\Windows\System32\OneDriveSetup.exe /uninstall (32 bit)

Also disables registry entries that keep the OneDrive Icon pinned to your Windows Explorer list: OneDrive Example Image
Delete Services vs Disable Services?

Selecting "Disable" will simply stop the services from being able to run. Selecting the "Delete" choice will completely delete the tracking services.
