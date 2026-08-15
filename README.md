# House Hunt — the app

A single static page. It talks to Supabase for data, auth and realtime; there is
no server here and no build step.

## What is in this repository

`index.html`, and nothing else. That is deliberate: the pipeline that gathers
the data lives in a separate private project, so a public repository can never
contain scraped listings, API keys or the database.

## About the key in this file

The page contains the Supabase project URL and its **publishable** key. Both are
meant to be public — they identify the project, they do not grant access:

- Nobody can read anything without signing in.
- Sign-in is restricted to an allowlist enforced in the database, so an
  uninvited address cannot even create an account.
- Row Level Security decides what a signed-in person can see and change. The
  property list is read-only to everyone; only the pipeline, using a service
  role key that never leaves the owner's machine, can write it.
- Notes and verdicts can only be created or deleted by the person who made them.

The service role key, the EPC and TfL API keys, the ntfy topic and the Google
service account are all in `.env` on the pipeline machine and appear nowhere in
this repository.

## Updating

Replace `index.html` and push. GitHub Pages redeploys within a minute or so.
