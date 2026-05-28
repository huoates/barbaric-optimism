# Download Visual Studio Code

1. **Download VS Code:**
   - Go to the official VS Code website: https://code.visualstudio.com/
   - Click the "Download for Windows" button to get the latest stable build.

2. **Run the installer:**
   - Once the download is complete, run the installer (`VSCodeUserSetup-x.x.x.exe`).
   - Follow the prompts. It's recommended to select "Add "Open with Code" action to Windows Explorer file context menu" and "Add "Open with Code" action to Windows Explorer directory context menu" for convenience.

3. **Launch VS Code:**
   - After installation, launch Visual Studio Code.

# Download Go

1. **Download the Go installer:**
   - Open your web browser and go to the official Go download page: https://golang.org/dl/
   - Download the Windows installer (MSI file). It will typically be named something like `go1.x.x.windows-amd64.msi`.

2. **Run the installer:**
   - Once the download is complete, run the MSI installer.
   - Follow the prompts in the installation wizard. The default settings are usually sufficient.
   - Ensure that the installer adds Go to your system's PATH environment variable. This is usually handled automatically.

3. **Verify the installation:**
   - Open a new PowerShell or Command Prompt window.
   - Type `go version` and press Enter.
   - You should see output similar to `go version go1.x.x windows/amd64`, confirming that Go is installed correctly.


# Install Packwiz

1. **Install Packwiz:**
   - With Go installed, open a new PowerShell or Command Prompt window.
   - Run the following command to install Packwiz:
     ```powershell
     go install github.com/packwiz/packwiz@latest
     ```
   - This command will download and install the latest version of Packwiz.

# Clone the repository using Git in VS Code

1.  **Open VS Code.**
2.  **Open the Source Control view:** Click the Source Control icon in the Activity Bar on the left-hand side (it looks like a Git icon).
3.  **Click "Clone Repository"** or "Clone" if it's the first repository.
4.  When prompted, **paste the repository URL:** `https://github.com/microsoft/Barbaric-Optimism.git`
5.  **Choose a directory** on your local machine where you want to clone the repository. It is recommended to be somehwere like `C:\GitHub\` and outside of your One Drive
6.  After the cloning process is complete, VS Code will ask if you'd like to open the cloned repository. Select **"Open"**.
