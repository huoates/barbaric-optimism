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

# Use Packwiz to Export Modpack to Curseforge

1. Open your terminal within VS Code and use `packwiz curseforge export` to export the modpack to a zip file

# Import into Prism Launcher

1. In Prism Launcher - click Add Instance -> Import and point to the newly created .zip file

# Running and Testing the Development Server Modpack

This section outlines the process for running and testing the **server-side** of the development modpack. While client-side and single-player modpack testing can be done by exporting with `packwiz curseforge export` and loading into Prism Launcher, the primary goal of this section is to confirm that the **server** will be able to start correctly without issues before merging changes into the production branch.

## Automatic Publication to GitHub Pages

After a Pull Request (PR) is merged into the `dev` branch, GitHub Actions automatically publishes the packwiz files to GitHub Pages. This ensures that the `compose.yaml` file always references the latest development version.

## Prerequisites (Windows)

To run the development modpack on Windows, you will need:

1.  **Docker Desktop:** This is essential for running containerized applications. Docker Desktop also assists with the installation and enablement of the Windows Subsystem for Linux (WSL), which is a prerequisite.
2.  **Windows Subsystem for Linux (WSL):** Docker Desktop will guide you through enabling WSL if it's not already active on your system.

## Using Docker Compose with VS Code

The VS Code Docker extension can greatly simplify the process of working with Docker Compose:

*   **GUI for Docker Compose:** The extension provides a graphical user interface (GUI) for interacting with your `compose.yaml` file.
*   **Start and Stop Containers:** You can easily start and stop your Docker containers directly from VS Code, eliminating the need to switch to Docker Desktop.

### Steps to Run the Modpack

1.  **Open `compose.yaml`:** In your repository, right-click on the `compose.yaml` file.
2.  **"Compose Up":** Select the "Compose Up" option from the context menu. This will build and start the services defined in your `compose.yaml`.
3.  **Manage from Docker Tab:** Once started, you can manage the container (start, stop, restart) from the Docker tab located on the left-hand side of VS Code.

### Important Note on Local Changes

The `compose.yaml` file is configured to always point to the `dev` section of GitHub Pages. This means that any changes made to your local branches will **not** be reflected when the modpack is run through Docker Compose until those changes have been merged into the `dev` branch.
