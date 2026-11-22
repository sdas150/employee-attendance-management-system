# Testing guide

Run the scripts in the order listed in the main README.

| Test | Action | Expected result |
|---|---|---|
| 1 | Login with EMP001 | Login successful; one open row created |
| 2 | Login with EMP001 again before logout | Error 50002; no second open row |
| 3 | Logout EMP001 | Logout successful; logout time and hours populated |
| 4 | Logout EMP002 without logging in | Error 50004 |
| 5 | Login with unknown code | Error 50001 |
| 6 | Daily report | Active employees appear; no-punch employees show no recorded session |
| 7 | Monthly report | Session count, days with punches and completed hours appear |
| 8 | Employee history | Sessions in the requested date range appear |

## Notes
- The login/logout examples use the SQL Server machine's local `SYSDATETIME()` value. Confirm the server clock and time-zone policy before real deployment.
- The project records elapsed time. It does not subtract lunch or other breaks.
- A session that crosses midnight is stored under its punch-in date.
- The filtered unique index is a final database-level safeguard against two open sessions for one employee.
