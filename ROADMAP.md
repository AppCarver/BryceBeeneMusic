## Project: BryceBeeneMusic — Site Cleanup + Band Docs System

### Overview section (brief paragraph)
This project has two tracks running in parallel:
- Track 1: Clean up and stabilize the existing Firebase-hosted public website
- Track 2: Build a plain-text, Markdown-based band documentation system (band-docs/)
  that will eventually be accessible to band members through the existing site.
The two tracks converge in Phase 3 when band-docs is surfaced through a
Firebase-authenticated member portal.

### 🔴 IMMEDIATE — Security & Cleanup (do before anything else)

- [x] Rotate the credential found in firebase_config.conf in Firebase console
- [x] Delete firebase_config.conf from the repo (git rm firebase_config.conf)
- [x] Add firebase_config.conf to .gitignore
- [x] Verify the rotated credential is not hardcoded anywhere else in the project

### 🟡 TRACK 1 — Website Cleanup (existing site)

#### Archive (move to _archive/, do not delete yet)
- [x] admin-login.html — archived
- [x] setup-data.html — archived
- [x] firebase-check.html — archived
- [x] QUICK_REFERENCE.md — archived
- [x] SITE_AUDIT_REPORT.md — archived
- [x] Delete images/howdy_maam.jpg — done

#### Minor Fixes
- [ ] Delete images/howdy_maam.jpg — orphaned, not referenced in any HTML
- [ ] Add missing favicon files: favicon-32x32.png, favicon-16x16.png, safari-pinned-tab.svg
- [ ] Fix site.webmanifest icon paths — currently point to root, should point to images/

#### Documentation
- [ ] Rewrite README.md — replace current one-liner with a real project overview
- [ ] Confirm firebase.json hosting.ignore list is current after archive moves

### 🔵 TRACK 2 — Band Docs System

#### Phase 1 — Local Foundation (VS Code + Markdown, no web yet)

Goal: A complete, working documentation system on the local machine.
Useful immediately, even before any web work begins.

##### Folder Structure
- [x] Create band-docs/ in project root
- [x] Create band-docs/songs/
- [x] Create band-docs/songs/chord-charts/
- [x] Create band-docs/songs/number-charts/
- [x] Create band-docs/songs/_index.md
- [x] Create band-docs/setlists/
- [x] Create band-docs/setlists/_template.md
- [x] Create band-docs/gigs/
- [x] Create band-docs/gigs/_template.md
- [x] Create band-docs/rehearsals/
- [x] Create band-docs/rehearsals/_template.md
- [x] Create band-docs/roster/
- [x] Create band-docs/roster/band-members.md
- [x] Create band-docs/roster/fill-ins.md
- [x] Create band-docs/README.md

##### Templates to Create
- [x] Chord-over-lyric chart template
- [x] Nashville Number System chart template
- [x] Setlist template
- [x] Show-day info sheet template
- [x] Rehearsal plan template

##### First Real Content
- [ ] Populate songs/_index.md with current active song list
- [ ] Create at least one complete chord chart from a real song
- [ ] Create at least one complete number chart from a real song
- [ ] Create a setlist file for the next upcoming gig
- [ ] Create a gig info sheet for the next upcoming gig

##### Git Setup
- [ ] Initialize or confirm git repo is tracking band-docs/
- [ ] Confirm .gitignore is not accidentally excluding band-docs/
- [ ] Make first commit of band-docs/ structure

##### Phase 1 Complete When:
- [ ] band-docs/ folder is fully scaffolded
- [ ] All five templates exist and are usable
- [ ] At least one real song has both a chord chart and a number chart
- [ ] The next gig has a setlist and info sheet
- [ ] Everything is committed to git

#### Phase 2 — Online and Shareable (Firebase Hosting, no logins yet)

Goal: Band members can view files via a URL. No authentication yet.
Uses the existing Firebase Hosting setup.

- [ ] Add viewer.html to project root — universal Markdown renderer using Marked.js
- [ ] Add portal.html to project root — simple file browser/nav page listing band-docs
- [ ] Add basic style.css for portal and viewer pages
- [ ] Wire Marked.js (CDN, no build step) to render .md files in the browser
- [ ] Confirm band-docs/ files are not excluded in firebase.json hosting.ignore
- [ ] Test viewer.html?file=band-docs/songs/_index.md renders correctly
- [ ] firebase deploy and verify live at existing domain
- [ ] Share URL with trusted band members (no login required at this stage)

##### Phase 2 Complete When:
- [ ] Any .md file in band-docs/ is viewable in a browser via viewer.html?file=
- [ ] portal.html provides navigation to songs, setlists, gigs, rehearsals, roster
- [ ] Site is deployed and accessible at the existing Firebase domain

#### Phase 3 — Logins and Access Control (Firebase Auth)

Goal: Individual login per band member. Portal is private.

- [ ] Enable Email/Password auth in Firebase console
- [ ] Create index/login page (or add login to existing portal.html)
- [ ] Create js/auth.js — auth state guard that runs on all protected pages
- [ ] Wrap portal.html and viewer.html behind auth check
- [ ] Create Firebase Auth accounts for each active band member
- [ ] Create Firebase Auth account for band leader / admin
- [ ] Update firestore.rules if needed to reflect member access patterns
- [ ] Test login, view, and logout flow on desktop and mobile
- [ ] Document how to add/remove member accounts in README.md

##### Phase 3 Complete When:
- [ ] Unauthenticated users are redirected to login
- [ ] Each band member has individual credentials
- [ ] Any member can log in and view all band-docs content
- [ ] Accounts can be disabled instantly when someone leaves

#### Phase 4 — Notifications and Polish

Goal: Members know when content has been updated. Portal feels finished.

- [ ] Create Firestore collection: changelog
- [ ] Fields per doc: date, message, author
- [ ] Add "What's New" panel to portal.html that reads from changelog collection
- [ ] Write a simple process doc: how to update the changelog after a deploy
- [ ] Update firestore.rules to allow authenticated reads of changelog
- [ ] Add download buttons/links in viewer.html for .md files
- [ ] Test full flow: deploy → update changelog → member logs in → sees update
- [ ] Optional: add mobile-friendly CSS pass to portal and viewer pages

##### Phase 4 Complete When:
- [ ] Members see a changelog panel on login showing recent updates
- [ ] Files are downloadable from the viewer
- [ ] The portal is usable on a phone

### Notes
- [ ] All band-docs content is plain Markdown — no third-party band management apps
- [ ] All web code is plain HTML/CSS/JS — no frameworks, no build pipeline
- [ ] Firebase Hosting, Auth, and Firestore are the only backend services used
- [ ] band-docs/ is editable in VS Code and deployable via firebase deploy
- [ ] This roadmap is a living document — check off items as they are completed
