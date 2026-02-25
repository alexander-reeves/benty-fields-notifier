# Benty Fields Notifier

Daily GitHub Actions email reminder for the Benty Fields arXiv page.

This project sends you a daily email with a button to open that day's results page:

- `https://www.benty-fields.com/daily_arXiv_results?date=YYYY-MM-DD`

It is useful if you want a simple, serverless reminder without running your own backend.

## How it works

- GitHub Actions runs on a daily cron schedule.
- A manual trigger is also available for instant testing.
- The workflow sends an email using Gmail SMTP via `dawidd6/action-send-mail`.
- On each run, the workflow builds today's date and links to:
  - `https://www.benty-fields.com/daily_arXiv_results?date=YYYY-MM-DD`

Workflow file:

- `.github/workflows/benty-reminder.yml`

## Setup

1. Create a GitHub repository and push this project.
2. In your repo, go to **Settings -> Secrets and variables -> Actions**.
3. Add these repository secrets:
   - `GMAIL_USER`: your Gmail address
   - `GMAIL_PASSWORD`: your Gmail App Password (not your normal Gmail password)
   - `RECIPIENT_EMAIL`: where reminders should be sent

## Test now (manual run)

1. Open **Actions** in your GitHub repo.
2. Select **Benty Fields Daily Reminder**.
3. Click **Run workflow**.
4. (Optional) Fill the `recipient` input to override `RECIPIENT_EMAIL` for a one-off test.
5. Click **Run workflow** again to start.

The `recipient` field lets you send a one-off test to any address without changing secrets.

## Daily schedule

Current schedule:

- `30 6 * * *` (06:30 UTC every day = 07:30 CET)

If you want another time, edit the `cron` value in `.github/workflows/benty-reminder.yml`.

## Rename it for your own use

You can easily rebrand this project if you want to use it for yourself or share it:

- Change the project title in `README.md` (line 1).
- Change workflow display name in `.github/workflows/benty-reminder.yml`:
  - `name: Benty Fields Daily Reminder`
- Change email sender display name in `.github/workflows/benty-reminder.yml`:
  - `from: Benty Reminder Bot <${{ secrets.GMAIL_USER }}>`
- Update the greeting/body text in `html_body` to your own wording.

## Gmail notes

For Gmail SMTP, use a Google App Password:

- Enable 2-Step Verification on your Google account.
- Generate an App Password for Mail.
- Use that App Password as `GMAIL_PASSWORD`.

## Customization ideas

- Change subject/body text in the workflow.
- Point the button to another page.
- Add multiple recipients (comma-separated in `RECIPIENT_EMAIL`).
- Rename the workflow and sender text to match your own branding.
