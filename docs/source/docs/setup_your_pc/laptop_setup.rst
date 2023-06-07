Laptop Setup
=========================
.. tags:: installation

List of softwares to install:

For Bureautique
------------------------------
- Office 365 all softwares (Outlook, Teams, PowerPoint, Excel, Word)
- Notepadd++
- Chrome, Firefox, Edge
- Bitwarden
- 7zip
- Foxit Reader / Acrobat Reader
- XMind
- PowerToys
- Slack
- Zoom

.. code::

    winget install -e --id Notepad++.Notepad++

    $Path = $env:TEMP; $Installer = 'chrome_installer.exe'; Invoke-WebRequest -Uri 'http://dl.google.com/chrome/install/375.126/chrome_installer.exe' -OutFile $Path\$Installer; Start-Process -FilePath $Path\$Installer -Args '/silent /install' -Verb RunAs -Wait; Remove-Item -Path $Path\$Installer

    winget install -e --id Mozilla.Firefox

    winget install -e --id Bitwarden.Bitwarden

    winget install --id=7zip.7zip  -e

    winget install --id=Foxit.FoxitReader  -e

    winget install -e --id Adobe.Acrobat.Reader.32-bit

    winget install -e --id Microsoft.PowerToys

    winget install -e --id SlackTechnologies.Slack

    winget install -e --id Zoom.Zoom

For Coding
------------------------------
- WSL
- Windows Terminal
- Python
- Anaconda
- MobaXterm
- Putty
- Git
- TortoiseGit
- VS Code
- Gitui

.. code::

    winget install -e --id Microsoft.WindowsTerminal

    winget install --id=Mobatek.MobaXterm  -e

    winget install -e --id PuTTY.PuTTY

For Data Analyst
------------------------------
- Power BI
- Power BI External Tools
- Just Color Picker
- Alteryx
- Knime
- Tableau Software 

winget install -e --id Microsoft.PowerBI

winget install -e --id Tableau.Desktop