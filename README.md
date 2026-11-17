# Uptime monitor

A GitHub Actions job checks a list of addresses every 5 minutes, from outside the server. Each must answer HTTP 200 without an error page. A failed check is retried once after 60 seconds; if it fails twice, the run fails and GitHub emails the account that last changed the schedule.

- The addresses are kept in the repository secret `UPTIME_URLS` (one per line) and are never printed. The error-page text is in `UPTIME_ERROR_TEXT`.
- GitHub can start scheduled runs 5 to 15 minutes late.
- A monthly keepalive commit (`.keepalive`) stops GitHub from switching the schedule off after 60 days without a commit.
