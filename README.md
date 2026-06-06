# Getting Started

## Download Visual Studio Code

1. **Download VS Code:**
   - Go to the official VS Code website: https://code.visualstudio.com/
   - Click the "Download for Windows" button to get the latest stable build.

2. **Run the installer:**
   - Once the download is complete, run the installer (`VSCodeUserSetup-x.x.x.exe`).
   - Follow the prompts. It's recommended to select "Add "Open with Code" action to Windows Explorer file context menu" and "Add "Open with Code" action to Windows Explorer directory context menu" for convenience.

3. **Launch VS Code:**
   - After installation, launch Visual Studio Code.

## Download Go

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


## Install Packwiz

1. **Install Packwiz:**
   - With Go installed, open a new PowerShell or Command Prompt window.
   - Run the following command to install Packwiz:
     ```powershell
     go install github.com/packwiz/packwiz@latest
     ```
   - This command will download and install the latest version of Packwiz.

## Clone the repository using Git in VS Code

1.  **Open VS Code.**
2.  **Open the Source Control view:** Click the Source Control icon in the Activity Bar on the left-hand side (it looks like a Git icon).
3.  **Click "Clone Repository"** or "Clone" if it's the first repository.
4.  When prompted, **paste the repository URL:** `https://github.com/microsoft/Barbaric-Optimism.git`
5.  **Choose a directory** on your local machine where you want to clone the repository. It is recommended to be somehwere like `C:\GitHub\` and outside of your One Drive
6.  After the cloning process is complete, VS Code will ask if you'd like to open the cloned repository. Select **"Open"**.

## Use Packwiz to Export Modpack to Curseforge

1. Open your terminal within VS Code and use `packwiz curseforge export` to export the modpack to a zip file

## Import into Prism Launcher

1. In Prism Launcher - click Add Instance -> Import and point to the newly created .zip file

# Adding and Removing Mods to the Packwiz Project

This section details the process for adding new mods to this Packwiz project, primarily targeting Curseforge.

## Adding Mods from Curseforge

The primary method for adding a mod from Curseforge is using the `packwiz cf add` command. You will need the mod slug, which can be found in the address bar when viewing a mod on the Curseforge website.

```bash
packwiz cf add <mod-slug>
```

**Example:**
If the URL is `https://www.curseforge.com/minecraft/mc-mods/jei`, the mod slug is `jei`.
```bash
packwiz cf add jei
```

## Handling Curseforge Mods Blocking Third-Party Downloads

Sometimes, a Curseforge mod may not allow third-party downloads via API. This is typically discovered when running the development server locally (e.g., the server fails to start or the mod doesn't load). In such cases, replace the Curseforge version with the Modrinth version, which generally allows third-party API connections.

To add a mod from Modrinth, use the `packwiz modrinth add` command:

```bash
packwiz modrinth add <mod-slug>
```

**Example:**
To replace a Curseforge mod with its Modrinth counterpart:
1. Remove the existing Curseforge mod entry (if any) from your `mods/` directory and `pack.toml`.
2. Add the Modrinth version:
   ```bash
   packwiz modrinth add <mod-slug>
   ```

## Adding Specific Mod File Versions

If a specific file version of a mod is required (e.g., adding an older version of a mod), you can use the `packwiz cf add <project-id> <file-id>` command.

*   **Project ID:** Can be found in the "More Details" section of a mod page on Curseforge.
*   **File ID:** Can be found when browsing the specific files for the mod on Curseforge.

```bash
packwiz cf add <project-id> <file-id>
```

**Example:**
```bash
packwiz cf add 32274 2786734
```

## Removing a mod
To remove a mod, use the `packwiz rm <mod-slug>` command.

```bash
packwiz rm <mod-slug>
```

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

# How to Contribute

To merge changes into the project, follow these steps:

1.  **Branch Creation:** Create your branch off the `dev` branch. The `dev` branch contains the latest updates and is usually a few commits ahead of `main`, which is the production branch for the server.

    *   **Branch Naming (Recommendation):** Ideally, name your branch to indicate its purpose. For example, `feature/readme-adding-mods` or `fix/default-configs`. While not strictly critical, this is a general recommendation.

2.  **Link to GitHub Issues:** Link your branch to relevant issue(s) in GitHub. If a branch addresses multiple issues, tag each issue with the branch. Otherwise, stick to one branch per issue to make the resulting Pull Request (PR) easier to digest, approve, and merge.

3.  **Make Your Changes:** Implement your changes in your new feature branch (add functionality, resolve issues, etc.). Make atomic commits to your branch.

4.  **Client-Side Testing:** Test your changes on the client side:

    *   Use `packwiz cf export` to generate the modpack.
    *   Import the resulting pack into a fresh instance within Prism Launcher.

5.  **Open a Pull Request (PR):** Once your changes are complete and tested, open a Pull Request to merge your feature branch into the `dev` branch. Review your changes with contributors.

    *   *(Note: It is currently uncertain if GitHub will auto-associate the PR with your linked issues, but we hope it does!)*

6.  **Server-Side Testing (Post-Merge):** Once your PR is merged into `dev`, the GitHub Actions workflow will build the project and publish it to the `dev` section of GitHub Pages. This makes server-side testing available (refer to the "Running and Testing the Development Server Modpack" section for details).

    *   If you encounter issues while running the server, open new issues for those specific fixes and repeat this contribution process.
