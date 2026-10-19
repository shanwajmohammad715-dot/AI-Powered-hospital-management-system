# CareFlow — AI-Powered Hospital Management System (Multi-Doctor Login)

Beginner-friendly educational Flask project for Windows + VS Code. Includes a responsive dashboard, doctor directory, patient records, appointments, billing records, a rule-based symptom information demo, and Excel export.

## Multi-doctor account features
- Administrator account can create one login per existing doctor profile.
- Every doctor has a unique username and password.
- Passwords are stored as hashes, not plaintext.
- Doctors can change their own passwords.
- Doctor accounts see only the patients, appointments, bills and Excel rows created under their own account.
- Administrator can see all records and manage doctor login accounts.
- SQLite database is created automatically as `hospital.db`.

## Windows setup (VS Code)
1. Extract this ZIP to a folder, for example `C:\Users\admin\Desktop\ai_hospital_management_system`.
2. Open VS Code → **File → Open Folder** → choose that extracted folder.
3. Open **Terminal → New Terminal** and confirm the terminal path is the project folder.
4. Check Python: `py --version`
5. Create the environment (first time only): `py -m venv .venv`
6. Install libraries (first time only):
   `.\.venv\Scripts\python.exe -m pip install -r requirements.txt`
7. Create your local environment file:
   `Copy-Item .env.example .env`
   If `.env` already exists, do not overwrite it.
8. Open `.env`, set a long random `SECRET_KEY`, and change `ADMIN_PASSWORD` to a strong password. The initial admin account is created only on the first database initialization.
9. Start the app:
   `.\.venv\Scripts\python.exe app.py`
10. Open Chrome/Edge and visit `http://127.0.0.1:5000`. Keep the terminal running.

## First login
If you have not changed the example settings before first database creation:
- Username: `admin`
- Password: `ChangeAdmin123!`

For security, change this immediately using **Change Password**. If the database was already initialized with a different admin password, use that password. Changing `.env` after the admin user has been created does not automatically reset the database password.

## Create separate doctor accounts
1. Sign in as administrator.
2. Open **Manage Accounts**.
3. Select a doctor profile (sample profiles are included), enter the doctor's full name, unique username, and a temporary password of at least 10 characters.
4. Give the login details to that doctor privately.
5. Doctor signs in using their own account and changes the temporary password from **Change Password**.
6. Create one account per doctor profile. A doctor profile can only be linked to one login account at a time.

## Run again later
Open the same project folder in VS Code and run:
`.\.venv\Scripts\python.exe app.py`
Then open `http://127.0.0.1:5000`. Do not recreate the environment each time.

## Troubleshooting
- If `.venv` is missing, run `py -m venv .venv` from the project folder.
- If packages are missing, run `.\.venv\Scripts\python.exe -m pip install -r requirements.txt`.
- If `Copy-Item .env.example .env` says `.env.example` does not exist, check that VS Code opened the extracted project root. The `.env.example` file must be visible in the Explorer. If `.env` already exists, skip the copy step.
- If port 5000 is busy, stop the previous server with `Ctrl+C`, then retry.

## Important safety limitations
- This is an educational demo, not a production hospital system.
- The symptom helper is rule-based and is not validated medical AI; it cannot diagnose or prescribe.
- Billing is manual record-keeping; no real payment gateway is connected.
- Excel export creates a downloadable snapshot, not a live-synced Excel file.
- Legacy records from an older single-login version have no owner assigned; they are visible to the administrator only, not automatically assigned to a doctor.
- Do not store real patient data until security, privacy, backup, audit-log, access-control, HTTPS, and applicable legal requirements have been professionally reviewed.
- Do not expose Flask's development server to the public internet.
