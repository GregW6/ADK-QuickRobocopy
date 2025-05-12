# ADK Custom Robocopy Right-Click Actions

This repository provides Windows Registry files to add and remove custom “Copy (Robocopy Source)” and “Paste (Robocopy Destination)” options to the context menus for files and folders. These actions leverage the powerful `robocopy` command-line utility for efficient file and folder operations.

## Prerequisites

-   **Windows Operating System:** These registry modifications and scripts are designed for Windows.
-   **Robocopy:** The `robocopy` command-line utility must be available on your system. It is included by default in most modern Windows versions.
-   **PowerShell Core:** The scripts are executed using `pwsh`. You need to have PowerShell Core installed and accessible via the `pwsh` command. This is different from the default Windows PowerShell.

## Features

- **Robocopy: Add to List:** Adds a context menu option for files and folders to add their paths to a temporary list for a multi-item `robocopy` operation.
- **Robocopy: Clear List:** Adds a context menu option in folder backgrounds to clear the temporary list of items to be copied.
- **Robocopy: Paste:** Adds a context menu option in folder backgrounds to initiate a `robocopy` operation using all paths in the temporary list as sources and the current folder as the destination.
- **Shift Key Requirement:** All quick actions are configured to appear only when holding down the `Shift` key while right-clicking, helping to keep your context menus clean.

## Script Flow

The following diagram illustrates the flow of the copy and paste actions:

[![Mermaid Flowchart Top-Down of ADK-QuickRobocopy](/images/mermaid-1_flow.svg)](https://mermaid.live/edit#pako:eNqdVttu00AQ_ZXRStBUSkqaC0n9ALS5tPQakt4dHrb2Jl6wvdbaEYQoEh8CP8eXsF6PHedWKvJizeyZ2Zkzk2PPiCVsRgwycsU3y6Eyguv20Af1e_UKbqnk9Mll0GYj7vOICz9MDjPIIIpjXqunCBKn9hQK-rG7m_pEUIh9ItiNfVl4l7vsTVe4NpPQ52MnKrVcbn2FI0l9y0lgh-ZNuHwc5uM-J6ij2c7A4aNoB87YFHqShSGz38-Tw5Y5JANHfIM_P3_1xZOwRDA14NC2IRJwzsPoz8_fcBXEDQ4JJmyrGH3xgLnMisLnYrOgjnkYBMy3YSAm0mLQo5ET466ZF-iiEddVyU-4zV5a0IKwhKsjan0dSzFRN22j7XgDbdxfT4AVnTzH38ccfz0aRgwKadW7G6g73UDdhrAMfzbT_CBnMU3Q-a5ICNP7z80-o0ukhjCSwlvj9cLsCgkdajl5MB5eFnpSWKox3MqrGWJ4CG0uVaVCTtMre2Z_4kNaLoxU2gyD-T6tQ3Kl9Asd307332wrJlT_q_Vem20eBi6dxhS1dBZ1qJrjMtmBjpQiXfEbs0cnIYOW8DyqJq-68YIID29zG_WPEWXL1FLbwlzQ9-ZX5y437jzm2aHfbxj61uAs6mGNGeAjnD5CHnOdvaiarL_TiW9p0VoXMC1P6fmHGYQODZgBX9BTBJc-MdcARYRWuBQ6JDBfaNoLE4hgQ3zq2V8PXoVUNkMWcxS-zyzsLtcflEql5U5X1Psl8rsUrzK-g0PUZW0cofwqAx7U5sa-FqquNvB10tZGB2USK1swmMtyKTS0i0q5AfofarjexTHKpDZOUAQXXZQWA1qZlw74iMKojVNEaOMMNS1PyDnKmDYuUKq0cYnSpI0r1KV8aC-XDpm5RoHRxiCfrY_NauMmlw0jP6FwbaH_JIMuuq-srKLOc4ua89xstonLMo93qDjauEcl0cYDCsSWWpcLekSp2AJe_8cm3OmPFlIkY8ltYkRyworEY9KjsUlmcdiQRA7z2JDEf2WbjejEjYZk6M9VWED9RyG8NFJt4Nghxoi6obImgU0j1uZ0LOkCor4NmGypVY2I0Wg0dQ5izMh3YuzvlZu1ZrVcr9YqlUbj7YE6nRKjVG3U95q1RrlZbZbrjXKtPi-SH_ra_b235Uq9oQCVWrlaqR9Ui4TZXL2iLpKvOv1xN_8L8d4ehg)

## Installation

> [!WARNING]
> Modifying the Windows Registry can cause serious problems if done incorrectly. It is recommended to back up your registry before proceeding.

1.  Download the `Add robocopy quick action.reg` file from this repository.
2.  Double-click the downloaded `.reg` file.
3.  Click “Run” in the security warning dialog.
4.  Click “Yes” in the User Account Control dialog (if prompted).
5.  Click “Yes” in the Registry Editor confirmation dialog.
6.  Click “OK” to acknowledge that the keys and values have been successfully added.

The new context menu options should now be available when you hold `Shift` and right-click on files, folders, or in the background of a folder window.

## Uninstallation

1.  Download the `Remove robocopy quick action.reg` file from this repository.
2.  Double-click the downloaded `.reg` file.
3.  Click “Run” in the security warning dialog.
4.  Click “Yes” in the User Account Control dialog (if prompted).
5.  Click “Yes” in the Registry Editor confirmation dialog.
6.  Click “OK” to acknowledge that the keys and values have been successfully removed.

The custom Robocopy context menu options will be removed.

## Robocopy Parameters

The “Paste (Robocopy)” action uses the following `robocopy` parameters:

-   `/E`: Copy subdirectories, including empty ones.
-   `/COPY:DAT`: Copy Data, Attributes, Timestamps.
-   `/DCOPY:DAT`: Copy Data, Attributes, Timestamps for directories.
-   `/SJ`: Skip Junction points.
-   `/SL`: Copy symbolic links.
-   `/R:2`: Retry failed copies 2 times.
-   `/W:5`: Wait 5 seconds between retries.
-   `/XO`: Exclude older files (copy newer/changed).
-   `/XC`: Exclude identical files (copy newer/changed).
-   `/V`: Verbose output.
-   `/TS`: Include source timestamps in output.
-   `/FP`: Include full path of files in output.
-   `/TEE`: Output to console.
-   `/UNICODE`: Output as Unicode.
-   `/ETA`: Show Estimated Time of Arrival.
-   `/XF "*.*"` and `/XD "*.*"` are used when copying a single file to ensure only the specified file is copied.

## Shift Key Requirement

Remember to hold down the `Shift` key when right-clicking to see the "Copy (Robocopy)" and "Paste (Robocopy)" context menu options.

## License

This project is licensed under the terms found in the [LICENSE](LICENSE) file.
