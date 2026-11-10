# Leave Intelligent Assistant (LIA)

Free, no-backend filing agent. One static page (`index.html`), no build step, no paid services.

## Run
- Open `index.html` in a browser, or
- Enable **GitHub Pages** (Settings > Pages > Deploy from branch > `main` / root) to get a live link.

## Workflow
1. Employee types `/leave` or `/overtime`, fills the predefined fields, submits.
2. Filing is routed automatically to the employee's manager (Pending).
3. Manager opens **Approvals** and approves or rejects (comment required on reject).
4. **Approved**
   - Leave: posted to the **Calendar**, leave balance deducted (8 hrs = 1 day).
   - Overtime: posted to the Calendar, OT hours computed (actual time outside the shift).
5. **Rejected**: employee sees it under **My filings** and can *Correct and resubmit* or *Cancel*.
6. Employee, Manager and HR view data in **Reports** (filter, balances, OT totals) and **Export CSV**.

## Commands
| Command | Fields |
|---|---|
| `/leave` | leave type, actual date (optional to-date for a range, weekends can be skipped), actual start/end time, reason (optional) |
| `/overtime` | shift date, shift start/end, actual date, actual start/end, reason (mandatory) |
| `/my`, `/balance`, `/help` | list my filings, show balances, help |

## Roles (demo)
Kwesi Amante (Employee) reports to approver Marie-Cris Betis; Jan Derek Buquid (Employee) reports to approver Hartell Torres; Margarita De la Torre is HR (view/export all). Use the "Acting as" dropdown.
Employees see their own filings, managers see their team, HR sees everything.

## Notes
Data is stored in the browser (localStorage) so the demo needs no server. To make it multi-user,
swap the `save()` and load logic for a free backend such as Google Sheets (Apps Script) or Supabase's free tier.
