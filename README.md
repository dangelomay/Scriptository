This repository description is crafted to sound like a professional infrastructure engineer’s toolkit. It emphasizes "Trench Engineering"—the ability to build reliable, scalable solutions in messy, real-world MSP environments.

You can copy and paste this directly into your `README.md` file.

---

# MSP-Trench-Toolkit

A curated collection of PowerShell automation scripts designed for enterprise infrastructure management and MSP (Managed Service Provider) maintenance.

### Philosophy: Trench Engineering

In the trenches, you don't always have the luxury of greenfield deployments or enterprise-grade documentation. You have legacy systems, broken configurations, and tight SLAs. This toolkit is built to handle those realities—stripping away the "bloat," automating the manual audits, and providing actionable reporting when the GUI fails you.

These scripts are written to be executed via RMM (specifically **NinjaOne**) with SYSTEM-level privileges, focusing on **proactive remediation** rather than reactive fire-fighting.

---

### Key Categories

#### 1. Hardware & Asset Auditing

* **System Age & Hardware Audit:** Goes beyond standard BIOS strings. Detects true system build (Custom vs. Prebuilt), calculates precise system age since OS installation, and reports OS build versions for fleet compliance.
* **Storage Auditor:** A native PowerShell tool that scans C: drives for "death by a thousand cuts" bloatware and hidden system data (VSS, system logs, cache) to reclaim disk space without 3rd-party tools.

#### 2. Proactive Maintenance & Remediation

* **Stuck Installer Terminator:** A surgical tool to identify and kill frozen installer processes (`msiexec`, `dism`, `TiWorker`, etc.) that block maintenance windows.
* **Wave Browser Annihilator:** A forced-removal script that targets stubborn PUPs (Potentially Unwanted Programs), wipes registry keys, and clears scheduled tasks that attempt to resurrect the browser.
* **System-Wide BitLocker Decryption:** An automated background process to decrypt drives, releasing CPU overhead for high-performance workloads or migrations.
* **NTP Hard-Reset:** A "nuclear" fix for time-drift issues in Domain environments, stripping corrupted registry drift-data and forcing a resync with reliable NTP pools.

#### 3. NinjaRMM Operations

* **User & Admin Audit:** Returns a real-time report of all local/domain profiles, identifies who is currently logged in, flags unauthorized local admin accounts, and enforces standardized "Omnitech" administrator access.
* **Server Downtime Automator:** Logic for policy-level conditions to create high-priority tickets for server downtime, bypassing Level 1 triage to immediately alert senior staff.

---

### Usage & Safety Guidelines

* **Execution:** Most of these scripts require `RunAsAdministrator` or must be deployed via your RMM as `NT AUTHORITY\SYSTEM`.
* **Disclaimer:** These scripts are designed for production infrastructure. While tested in field environments, always run a test-case on a non-critical endpoint before deploying to a global fleet.
* **Philosophy:** These tools are meant to be the "scalpel," not the "sledgehammer." They prioritize data integrity and system stability.

---

### About

Built by an Infrastructure Engineer focused on enterprise-grade architecture, automation, and minimizing technical debt.

* *Built for: Proactive MSP Maintenance*
* *Focus: Stability, Scalability, and Automation*
