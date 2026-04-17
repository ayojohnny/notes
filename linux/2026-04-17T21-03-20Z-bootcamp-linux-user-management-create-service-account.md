# Linux | Account Management - Service Accounts

Service Account:
- user account w/ no login shell
- used solely for running daemon processes (e.g. web servers, db, etc.)

Applications that should be long-running should **never be ran as root**. 
- huge security risk.
- should always be ran as service account (locked down)
