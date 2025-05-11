# ADK Custom Robocopy Right-Click Actions

This repository provides Windows Registry files to add and remove custom “Copy (Robocopy Source)” and “Paste (Robocopy Destination)” options to the context menus for files and folders. These actions leverage the powerful `robocopy` command-line utility for efficient file and folder operations.

## Features

- **Copy (Robocopy Source):** Adds a context menu option for files and folders to set the source path for a `robocopy` operation.
- **Paste (Robocopy Destination):** Adds a context menu option in folder backgrounds to initiate a `robocopy` operation using the previously copied source path and the current folder as the destination.
- **Shift Key Requirement:** Both quick actions are configured to appear only when holding down the `Shift` key while right-clicking, helping to keep your context menus clean.

## Script Flow

The following diagram illustrates the flow of the copy and paste actions:

[![Mermaid Flowchart Top-Down of ADK-QuickRobocopy](/images/mermaid-1.svg)](https://mermaid.live/edit#pako:eNqFVF1v2jAU_StXfukmAQuBdEkeNg0Co6V8DDpNW8KDlzjEahJHtqOWIaT-kO3P9ZfMONBmK2rzEOUq55x7fO6VtyhkEUEuilN2GyaYS7j2ghzU88n_KgiHBV0nstlPaXgjYEhT8m7I0ojwFTSbH6C3PVsmNJZnMCYbmHMiBIk-7iqFnoLAdyI0su8HaJmwW3i4_91nxQbeLNhPFqqvtw_3f2BWSMryAK0qal9zPMXRJpYkJaEUp7mPJE-TBv43TiWBJSt5SGCOZQKSwTXJCu1_VTM3ZZoyVH1GNCKve6u4n09EQ3OogoEeDm_WnJV5VGU0eimjUT2ji1pGcyzUIV4M6UKTLk-EdIL8yLrUrPFWB3IIaZ8LDO6okOJobFw3duUvCI7-iTTmLHsW6pVGT7YHIBXgUa5MMb456k7qulN_UeZwtAkx40-EVQ1_mNPsObzWfKoxc99TOajT_-9tVv2uirkuvvhzXAoCfZZlOI_UbFhWyFUtgEPjhe9RUaR4A3o9YqUq1JsL2YIB54wfOItKtjbag8CytmGvTBY10JrTCLmSl6SBMsIzvC_Rdi8bIJmQjATIVZ8RiXGZygAF-U7RCpz_YCw7MtUKrhPkxjgVqiqLCEviUbzm-AlCcrWxfbWrErmO6WgN5G7RHXJNs93q2B3Ttm2r6xhGp9tAG-R2nZbhmIZtWef2uWm_t3YN9Et3NVq2ZTq2YVndttGxrXangUhE1Swn1R2jr5rdX_Asabo)

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
