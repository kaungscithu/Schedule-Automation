# Schedule-Automation
This Google Apps Script automates the creation of visual, granular employee schedules. It transforms raw shift data into a 15-minute interval heatmap, intelligently placing breaks, lunches, and tasks while balancing "Active Headcount" (HC) throughout the day.

📅 Google Sheets Auto-Scheduler (Smart Placement Engine)
This Google Apps Script automates the creation of visual, granular employee schedules. It transforms raw shift data into a 15-minute interval heatmap, intelligently placing breaks, lunches, and tasks while balancing "Active Headcount" (HC) throughout the day.

🚀 Key Features
Custom Menu Integration: Adds an "Auto-Scheduler" menu to the Google Sheets UI for one-click generation.

Intelligent Placement Logic: * Fixed-Time Scheduling: Respects specific times for meetings or tasks if provided in the source.

Flexible Fallback: If no time is specified, the engine finds the "best" slot based on penalty scoring.

Buffer Awareness: Prevents scheduling breaks too close to the start or end of a shift.

Live Capacity Tracking: * Total HC: Tracks how many people are on shift.

Active HC: Tracks how many people are actually "on the floor" (Total minus those on breaks/lunches).

Visual Formatting: Automatically applies color-coding (Conditional Formatting) for Breaks (Sb), Lunches (Lu), and Work Tasks (We).

Error Reporting: Built-in status column to alert you if a shift falls outside the timeline or if a task couldn't be placed due to conflicts.

🛠 How it Works
Configuration: The script looks for two sheets: Schedule (Source) and 1. Ref (Duration & Code settings).

Timeline Generation: It builds a 30-hour timeline in 15-minute increments starting from 7:00 AM.

Penalty System: When placing flexible tasks, the script calculates a "score" for every possible slot. It chooses the slot with the lowest penalty, considering:

Proximity to the middle of the shift (for lunches).

Existing "Heat" (avoiding placing everyone on break at the same time).

Gap preferences (avoiding back-to-back breaks unless necessary).

Automation: Includes an onEdit trigger—toggle a checkbox in cell D1 of the Schedule sheet to re-run the script instantly.

📋 Requirements
Sheet Names: Must have sheets named Schedule and 1. Ref.

Reference Data: The 1. Ref sheet should contain task codes and their durations (in 15-min blocks) starting at row 11.

🖥 Technical Setup
Copy the code into your Google Sheets Extensions > Apps Script editor.

Refresh your spreadsheet to see the Auto-Scheduler menu.

Ensure your columns match the script's configuration:

Column D: Employee Name

Column F: Shift Start

Column G: Shift End (Optional, defaults to 9 hours)
