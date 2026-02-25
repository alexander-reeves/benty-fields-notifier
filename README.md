# Benty Fields Notifier

Daily GitHub Actions email reminder for the Benty Fields arXiv page.

This project sends you a daily email with a button to open:

- https://www.benty-fields.com/daily_arXiv

It is useful if you want a simple, serverless reminder without running your own backend.

## How it works

- GitHub Actions runs on a daily cron schedule.
- A manual trigger is also available for instant testing.
- The workflow sends an email using Gmail SMTP via `dawidd6/action-send-mail`.

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

The manual run uses a subject line starting with `TEST:` so test emails are easy to spot.

## Daily schedule

Current schedule:

- `0 8 * * *` (08:00 UTC every day)

If you want another time, edit the `cron` value in `.github/workflows/benty-reminder.yml`.

## Gmail notes

For Gmail SMTP, use a Google App Password:

- Enable 2-Step Verification on your Google account.
- Generate an App Password for Mail.
- Use that App Password as `GMAIL_PASSWORD`.

## Customization ideas

- Change subject/body text in the workflow.
- Point the button to another page.
- Add multiple recipients (comma-separated in `RECIPIENT_EMAIL`).
