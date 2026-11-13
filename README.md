# Google-Sheet-CRM-Automation
# Lead Management: Automated Lead Distribution and Sales Tracking Dashboard

Tools: Google Sheets (`QUERY`, Pivot Table)

## Problem
Potential customers (Leads) who registered for a Data Analyst event are collected into one master list. This project does two things: distribute leads evenly among sales reps, and track each rep's progress by contact status.
## Problem
Potential customers (Leads) who registered for a Data Analyst event are collected into one master list. This project does two things: distribute leads evenly among sales reps, and track each rep's progress by contact status.

## Requirement
1. Automatically distribute leads from the master list to individual sales reps.
2. Build a dashboard to track lead management per sales rep, broken down by contact status.

## Data
- `Master Leads` sheet: Timestamp, Full Name, Phone, Occupation, Career Switch Intent, Ticket Type
- `Sales List` sheet: sales rep names and headcount
- Contact status (Tag): Unreachable, In Progress, Contacted, Spam, Win
- Sample data: 199 leads (2023-06-17 to 2023-07-06), names and phone numbers anonymized

## Solution

### 1. Automated Lead Distribution
- Rule: Round robin (leads assigned in turn, each rep receives a near-equal number of leads)
- Method: Google Sheets formulas (MOD + INDEX + FILTER)
- The headcount is counted automatically from the sales list.
- Each lead is assigned a rep based on its position in the list, cycling through the reps in order.
- Each rep has a personal sheet that pulls only their assigned leads.
- Adding a new rep only requires adding a name to the sales list; assignments redistribute automatically.
- Status updates: reps record the Tag in a separate sheet keyed by lead ID, and the dashboard joins it with `XLOOKUP`.
<img width="1632" height="871" alt="image" src="https://github.com/user-attachments/assets/94cd2223-d8b5-4bad-a3c8-640ac9390a34" />

### 2. Tracking Dashboard
- Built in Google Sheets with pivot tables, one per sales rep plus an overall view
- Metrics: total leads assigned, leads by contact status
- Shows the breakdown for each rep side by side, so their progress is easy to compare
- Status "Not Contact Yet" means the lead has no tag yet
<img width="877" height="262" alt="image" src="https://github.com/user-attachments/assets/9c641c4c-e78e-46a2-918b-abfd0992945f" />



- 
