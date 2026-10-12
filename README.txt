# JEE Rush OS 1.0.1 — Cloud Sync Edition

A responsive JEE chapter-completion and spaced-revision tracker with Supabase cloud sync. It contains no video links, embedded videos, lecture titles, or fixed daily chapter allocation.

## Syllabus
- Physics: 42 entries
- Chemistry: 41 entries
- Mathematics: 41 entries
- Total: 124 entries in the supplied order. The syllabus loads on first launch.

## Chapter completion and revision rules
Each chapter has three initial tasks: lecture, Revision 0 immediately after lecture, and question practice. When all three are checked, the app records the completion timestamp and schedules revisions for +1, +3, +7, +14, and +30 days. Unchecking an initial task reopens the chapter and clears its generated revision cycle.

## Cloud sync
The app uses the existing Supabase project configured in `app.js` and the `public.jee_rush_os_state` table. Authenticated users can sign up or sign in from Manage → Cloud sync. The database table is protected by row-level security so each account can access only its own state. Local changes save immediately and sync automatically while online; a local JSON backup remains available. Use the same Supabase account on PC and Android. If email confirmation is enabled, confirm your email before signing in.

The publishable key in the client is intended for public apps; never place a service-role or secret key in client code. `SUPABASE-SETUP.sql` documents the table and RLS policies. This setup has already been applied to the connected Supabase project for this release.

## Run on Windows
1. Install Node.js 22 or newer.
2. Extract the ZIP.
3. Double-click `start.bat`.
4. The app opens at `http://127.0.0.1:3001`.

## Build the Android APK
Run `android-build.bat` on Windows with Java and Android SDK installed, or push the project folder contents to the repository root and run the **Build JEE Rush OS APK** GitHub Actions workflow. The workflow outputs a debug APK artifact; this source ZIP does not contain a compiled APK.

## Local and offline behavior
The tracker saves locally immediately. Cloud sync requires an internet connection and a signed-in account. If offline, local edits remain on the device and can be synced when reconnected. Export a JSON backup before reinstalling the APK or clearing app data.
