# SuccessMap

SuccessMap is a Windows desktop app for Customer Success Managers. It helps you plan, run and report on **success plans**: the outcomes you have agreed with each customer, broken down into CTAs (calls to action) and tasks, with the dates, owners, meetings and evidence that go with them.

Everything runs on your own computer. Your data stays in one local file, there is no account to create and no cloud service to connect to.

This repository publishes the ready-to-run Windows builds. **Download them from the [Releases page](../../releases/latest).** The source code lives in a separate private repository.

## What you can do with it

- **See your whole portfolio.** Every plan with its health, progress and overdue work, plus headline counts across all your customers.
- **Keep accounts organised.** Owners, customer contacts, renewal dates, contract values, health, and how often you expect to meet each customer, with a warning when a meeting is overdue.
- **Start plans quickly.** Five built-in playbooks (onboarding, QBR preparation, renewal cycle, health recovery, adoption) or your own templates, with dates counted from the plan start.
- **Run the work.** CTAs and tasks with statuses, priorities, internal and customer owners, due dates, repeating tasks, bulk date changes, a Kanban board and a Gantt timeline. Work with open dependencies cannot be closed out of order, and On Hold work is kept out of progress and overdue counts.
- **Prove it is working.** Measurable success criteria with targets and evidence, a progress chart against a straight-line pace, plan health history, and a change log of what moved and when.
- **Know what needs you.** A Needs attention view of overdue work, upcoming renewals, overdue meetings, plans behind pace, plans that have gone quiet and items waiting on the customer; a My week view; a Weekly review you can paste into an email; and instant search across everything (Ctrl+K).
- **Capture in the moment.** Quick add (Ctrl+Alt+N) works from anywhere in Windows while SuccessMap is running.
- **Prepare and follow up on meetings.** A meeting log, import of action items from a Word meeting summary (reviewed before anything is applied), a one-click meeting prep briefing, Outlook draft chasers for what customers owe you, and a plain-language status update for the customer. These work for a whole account or, from inside a plan, for just that plan.
- **Separate internal from customer meetings.** Mark each meeting as with the customer or internal only. Internal meetings are left out of the PowerPoint export and PDF report, and do not count as customer contact for the "Last met" and meetings-overdue checks.
- **Keep notes properly.** Timestamped notes on plans, CTAs and tasks, with real dates, a "New" marker for notes you have not seen, the ability to file a plan note onto a task afterwards, and an **Internal / customer-facing** setting on each note so internal notes never appear in customer-facing exports.
- **Report and share.** A PDF plan report, a value snapshot for QBRs and renewals, a PowerPoint export built on your own template, an Excel workbook a customer can fill in, a Markdown portfolio summary, and plan export and import to move a plan to another installation.
- **Stay safe.** Scheduled database backups, a recycle-bin style Trash for everything you delete, and an optional scheduled email digest of overdue and upcoming work.

A guided tour built into the app walks through all of it using sample data, which you can remove with one click when you are ready to use your own.

## Download

Open the [latest release](../../releases/latest) and choose the file for your computer. Most Windows PCs are **x64**; Windows on ARM devices (for example Surface Pro X or Snapdragon laptops) are **arm64**. To check, open Settings > System > About and look at "System type".

| File | Use it when |
|---|---|
| `SuccessMap-Setup-<version>-<arch>.exe` | You can install software. It installs for your user, lets you pick the folder, and keeps itself up to date. The `.blockmap` file next to it is used by the updater; you do not need it. |
| `SuccessMap-Portable-<version>-<arch>.exe` | You cannot or do not want to install. A single file you can run from anywhere, such as a USB stick or a network share. |
| `SuccessMap-<version>-<arch>-nostub.zip` | Neither of the above starts (see Troubleshooting). Unzip it to a folder and run `SuccessMap.exe`. |
| `latest.yml`, `latest-arm64.yml` | The update feeds the app reads. Ignore these. |

You do not need to install .NET or anything else: the app carries everything it needs.

### First run and Windows SmartScreen

The builds are not yet signed with a publisher certificate, so Windows SmartScreen may show "Windows protected your PC" the first time you run one. Choose **More info**, then **Run anyway**. If your organisation blocks unsigned apps, ask your IT team to allow it, or use the unzipped build in a folder you control.

## Requirements

- Windows 10 or 11, x64 or arm64.
- **Optional:** Microsoft Outlook (desktop) to create draft emails and send the digest through Outlook. SMTP is available as an alternative for the digest.
- **Optional:** Microsoft PowerPoint, for the PowerPoint export only. The PDF report, value snapshot and all other exports do not need it.

## Updating

SuccessMap checks for a newer version shortly after it starts, and you can check any time from **About**.

- **Installed (Setup):** downloads the update and offers to restart to finish installing.
- **Portable:** downloads the new file and replaces itself when you restart.
- **Unzipped folder:** downloads the new version and copies it over the folder it is running from, then restarts.

You can also download any release by hand from this page. Your data is not touched by updates.

## Your data and privacy

- Your plans, notes and settings are stored locally in `%LOCALAPPDATA%\SuccessMap\successmap.db`. Nothing is sent anywhere by SuccessMap itself.
- The only network activity is checking this repository for new versions. Emails go through your own Outlook or SMTP server, and only when you ask for them.
- Set a **backup folder** in Settings (ideally on OneDrive or a network drive) on your first day. SuccessMap saves backups of the database there on a schedule while it is running and removes the older ones.
- To move a plan to another computer or share it with a colleague, use **Export plan** and **Import plan**. Each installation is single-user.

## Getting started

1. Install or run SuccessMap and choose **Guided tour** in the sidebar. It offers to load sample accounts so you can explore safely.
2. When you have finished, choose **Remove the sample data and start my own** (also under Settings > General).
3. Add your first account with its contacts and renewal date, create a plan from the closest template, set owners and dates, and log your last meeting so the cadence starts from a real date.
4. Set a backup folder, and if you like the daily reminder, in Settings.

The **Help** page in the app is a full reference with a chapter for every feature, and **Release notes** lists every version.

## Troubleshooting

- **Double-clicking the installer or portable file does nothing.** These use a 32-bit self-extracting launcher. On some Windows on ARM machines, especially managed ones where x86 emulation is switched off, it cannot start. Download the `nostub` zip for your architecture, unzip it, and run `SuccessMap.exe` from the folder.
- **On Windows on ARM, the x64 build usually runs too**, under emulation, if the arm64 single-file portable will not start.
- **The window is blank or the app closes immediately.** Make sure no other copy of SuccessMap is running (check the system tray): they share a local port. Then try again.
- **A SmartScreen or antivirus warning appears.** See First run and Windows SmartScreen above.
- **Outlook drafts or the PowerPoint export do nothing.** They need the desktop versions of Outlook and PowerPoint installed.
- **Where is my data?** `%LOCALAPPDATA%\SuccessMap`. Copy `successmap.db` from there, or use Export plan, to take your work elsewhere.

## Release notes and feedback

Every version, with a plain-English description of what changed, is on the [Releases page](../../releases) and in the app under **Release notes**. Questions and feedback go to the maintainer, Richard Lundgren.
