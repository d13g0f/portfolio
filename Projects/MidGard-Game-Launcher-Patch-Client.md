MidGard Game Launcher – Patch & Client Management Tool
# MidGard Game Launcher – Patch & Client Management Tool

## Project Context

This project is a desktop game launcher originally designed for the MidGard Tales of Pirates client.

The launcher acts as the entry point for players before starting the game. Its main purpose is to ensure the client installation is complete and up to date before launching the game executable.

Although initially developed for a Tales of Pirates private server, the architecture allows it to function as a generic game launcher capable of handling update checks, file patching, and client repair workflows.

The launcher was implemented as a Windows desktop application using WPF and integrates directly with a GitHub repository that serves as the patch distribution source.

---

## Launcher Goals

The launcher was designed to solve several practical problems common in private game servers:

• Ensure players always run the latest client version  
• Automatically download updates when new patches are available  
• Provide a repair mechanism for broken installations  
• Simplify the process of starting the game client  
• Provide a single interface for patching, launching, and accessing related resources  

---

## Core Features

### Automatic Update System

When the launcher starts, it checks whether the local client version matches the latest version available in the remote repository.

The update system works by:

1. Retrieving commit history from the client repository.
2. Parsing version identifiers embedded in commit messages.
3. Comparing the latest available version with the locally installed version.
4. Downloading only the files modified in newer commits.

Each commit effectively acts as a patch unit, allowing incremental updates rather than downloading the entire client again.


📷 Screenshot suggestion  
`screenshot-here: launcher update status view`

---

### Incremental Patching

Instead of downloading the entire game client for every update, the launcher downloads only the files that changed in specific commits.

The patch workflow performs the following steps:

• retrieve commit metadata from GitHub  
• identify added or modified files  
• download the new file versions  
• replace outdated files locally  
• remove files deleted in the repository  

This approach reduces download size and allows faster updates for players.


📷 Screenshot suggestion  
`screenshot-here: patching progress interface`

---

### Client Repair System

If the launcher detects that the client installation is incomplete or corrupted (for example, if `system/game.exe` is missing), it automatically triggers a repair workflow.

The repair system downloads a complete archive of the repository and extracts it into the installation directory, restoring all required files.


📷 Screenshot suggestion  
`screenshot-here: repair operation interface`

---

### Game Launch Management

Once the client is verified and up to date, the launcher can start the game executable.

The launcher resolves the client path:


system/game.exe


and launches the process with the required startup parameter:


startgame


This ensures the client starts with the correct configuration and allows the launcher to control when the game can be executed.

---

### User Interface

The launcher interface was implemented using **WPF with XAML**.

The UI is intentionally simple and focused on usability, providing a single screen with the main actions available to the player:

• Start Game  
• Repair Client  
• Open Website  
• Exit Launcher  

The interface also includes a status message panel that displays patching progress and operational messages.


📷 Screenshot suggestion  
`screenshot-here: main launcher window`

---

## Architecture

The launcher follows a small service-based architecture centered around the main WPF window.

### Main Components

**MainWindow**

Acts as the UI controller and workflow coordinator.

Responsibilities include:

• startup initialization  
• triggering update checks  
• managing repair operations  
• launching the game executable  
• updating UI status messages  

---

**PatchService**

Contains the main patching logic.

Responsibilities include:

• detecting available updates  
• applying incremental patches  
• downloading changed files  
• deleting obsolete files  
• performing full repair downloads  

---

**CommitReader**

Responsible for retrieving commit metadata from the GitHub repository using the GitHub API.

This component converts GitHub commit data into internal models used by the patching system.

---

**ClientVersionHandler**

Handles loading and saving the current client version stored locally in:


Version.json


This version value determines whether updates are required.

---

**MessageReporter**

A lightweight event-based system used by background services to send status updates to the UI.

This allows patch operations to report progress without tightly coupling service logic to the interface.

---

## Update System Design

The patching system uses a **commit-driven versioning model**.

Instead of relying on traditional patch manifests, the launcher interprets Git commits as patch entries.

The update flow is:

1. Load local client version from `Version.json`
2. Retrieve commit list from repository
3. Parse version identifiers from commit messages
4. Identify commits newer than the installed version
5. Apply updates sequentially
6. Persist the updated client version

This approach makes it possible to distribute patches directly from a source repository.

---

## Technologies Used

• **C#**  
• **WPF (XAML)**  
• **.NET Framework 4.8**  
• **Octokit (GitHub API client)**  
• **Newtonsoft.Json**  
• **HttpClient**  
• **System.IO.Compression**

---

## Development Challenges

The main challenge in this project was designing a reliable patching workflow that could update the client incrementally without requiring full downloads.

Handling file synchronization between the remote repository and the local client installation required careful sequencing to ensure updates were applied in the correct order.

Another challenge was integrating asynchronous patch operations with the WPF interface while maintaining a responsive UI and clear status reporting.

---

## Outcome

The final result is a functional game launcher capable of managing the full client lifecycle:

• verifying installation integrity  
• applying incremental updates  
• repairing broken installations  
• launching the game client  

The project also provided practical experience in desktop application development, remote repository integration, and building automated patch distribution systems.