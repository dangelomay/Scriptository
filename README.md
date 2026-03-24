# Scriptository
Its in the name...
\

# IT Automation & Scripting Repository

## Overview
This repository serves as a centralized, version-controlled vault for IT automation scripts, endpoint management tools, and custom utilities. The primary focus of this collection is to streamline operations, enforce standard configurations, and enable zero-touch remediation via Remote Monitoring and Management (RMM) platforms, specifically **NinjaOne**.

## Repository Contents

### 1. Endpoint Management & Remediation
* **Outlook COM Add-in Remediation (`outlook-addin-kill.ps1`)**
    * **Purpose:** Resolves critical Outlook crashes caused by rogue COM add-ins.
    * **Function:** Runs as SYSTEM to mount offline user registry hives (`NTUSER.DAT`) and force-disables all active Outlook add-ins across the Local Machine and all user profiles. Outputs a formatted remediation report for the RMM activity feed.
* **Enterprise Onboarding Master Script (`enterprise-onboarding.ps1`)**
    * **Purpose:** Cleans and secures new Windows workstation deployments.
    * **Function:** Neutralizes consumer features, disables telemetry, removes bloatware, and stops non-essential background services to establish a baseline enterprise configuration.
* **WinUtil JSON Deployment Script (`winutil-deploy.ps1`)**
    * **Purpose:** Automates the deployment of standard Windows configurations.
    * **Function:** Pulls and applies a customized JSON configuration file for Chris Titus Tech's Windows Utility across multiple managed endpoints silently.

### 2. RMM & Ticketing Automation
* **NinjaOne API Ticket Auto-Resolution (`ninja-auto-resolve.ps1`)**
    * **Purpose:** Enables true zero-touch IT support for common system alerts (e.g., high CPU usage).
    * **Function:** Authenticates with the NinjaOne API to automatically assign a triggered ticket to a specific technician, inject a detailed remediation log into the ticket notes, and close/resolve the ticket without manual intervention.

### 3. Security & Auditing
* **Security Reconnaissance Script (`av-recon.ps1`)**
    * **Purpose:** Audits endpoint security compliance.
    * **Function:** Scans the target endpoint via WMI/Security Center to detect and log exactly which Antivirus and Endpoint Protection products are currently installed and actively running.

### 4. Custom Projects & Utilities
* **Tesla Lock Sound Randomizer (`tesla-lock-chime.py` / `.sh`)**
    * **Purpose:** Custom automation for vehicle media.
    * **Function:** A lightweight script designed for a Raspberry Pi to rotate and randomize `.wav` lock sound files on a connected USB drive for a Tesla vehicle.

## Deployment Notes (NinjaOne)
When deploying these scripts via NinjaOne, pay strict attention to the **Run As** context:
* Scripts modifying `HKEY_CURRENT_USER` or interacting with the active desktop session must be run as **Logged-on User**.
* Scripts modifying `HKEY_LOCAL_MACHINE`, interacting with the NinjaOne API, or mounting offline user profiles (like the Outlook Add-in script) must be run as **System**.

### API Credentials
The `ninja-auto-resolve.ps1` script requires NinjaOne API credentials. **Never hardcode these into the script.** Ensure your Client ID and Client Secret are stored as secure Global Script Variables within your NinjaOne instance (`$env:NINJA_CLIENT_ID` and `$env:NINJA_CLIENT_SECRET`).

## Disclaimer
Always test scripts on a local VM or a small, non-critical test group before deploying them en masse to production endpoints.
