# Capstone Submission Tracker

Repo (fork): https://github.com/Lbstrydom/xrwvm-fullstack_developer_capstone
README URL (for grading form): see `readme_url.txt`

Screenshots go in `../screenshots/` using the filenames each lab specifies.
Check items off here as they're completed; note the screenshot filename once captured.

## Module 1 — Static Pages (5 pts)
- [x] Forked repo to Lbstrydom account
- [x] Cloned fork locally (`C:\GIT\xrwvm-fullstack_developer_capstone`)
- [x] Ran Django app on dev server locally (http://127.0.0.1:8000/) — terminal output saved: `django_server.txt`
- [x] Added Bootstrap navigation (Home / About Us / Contact Us, in `frontend/static/*.html`)
- [x] Added About Us static page (`frontend/static/About.html`)
- [x] Added Contact Us static page (`frontend/static/Contact.html`)
- [x] Pushed changes to GitHub fork (commit 7f6ced3, contact update pending push)
- [x] Saved public GitHub URL of About.html — `about_html_url.txt`
- [x] Saved public GitHub URL of Contact.html — `contact_html_url.txt`
- [x] Screenshots captured via Playwright: `screenshots/home.png`, `screenshots/about.png`, `screenshots/contact.png`
- Note: ran locally on Windows, not IBM Cloud IDE — ALLOWED_HOSTS/CSRF_TRUSTED_ORIGINS set to localhost/127.0.0.1 accordingly
- Note: About.html team photos still use the placeholder `person.png` — swap in real images when you have them

## Module 2 — User Management (6 pts)
- [x] Superuser created (`admin` — see `createsuperuser` note below)
- [x] React client built (`server/frontend` — `npm install && npm run build`); settings.py TEMPLATES DIRS / STATICFILES_DIRS updated for frontend/build
- [x] Login view (`djangoapp/views.py: login_user`) + `login/` route + Login.jsx wired up
- [x] Logout view (`djangoapp/views.py: logout_request`) + `logout` route + Home.html logout handler
- [x] Registration view (`djangoapp/views.py: registration`) + `register/` route + `Register.jsx`
- [x] Nav bar shows Login/Register when logged out, username + Logout when logged in (Home.html `checkSession()`)
- [x] Verified end-to-end via Playwright: login as admin, logout, register new user (testuser1) — all confirmed working
- [x] Pushed (commit 40278e0)
- [x] Saved public GitHub URL of Register.jsx — `register_jsx_url.txt`
- [x] Saved curl transcripts: `loginuser.txt`, `logoutuser.txt`
- [x] Screenshots: `screenshots/login-page.png`, `home-loggedin.png`, `home-afterlogout.png`, `register-page.png`, `home-afterregister.png`, `admin-dashboard.png`, `admin-users.png`
- Note: superuser username is `admin` (password given to you in chat only, not recorded here — change it anytime with `manage.py changepassword admin`)

## Module 3 — Back End (12 pts)
- [ ] Node.js/Express + MongoDB service for dealers & reviews, dockerized
- [ ] Sentiment analyzer deployed on Code Engine
- [ ] Django models/views for car make & model
- [ ] Django proxy services integrating dealers & reviews
- [ ] Screenshots per lab instructions

## Module 4 — Dynamic Pages (6 pts)
- [ ] Dealers list page
- [ ] Dealer reviews page
- [ ] Add review page
- [ ] Screenshots per lab instructions

## Module 5 — CI & Containerize (9 pts)
- [ ] CI linting pipeline
- [ ] Run on Cloud IDE
- [ ] Local test of updated app
- [ ] Deploy on Kubernetes
- [ ] Screenshots per lab instructions

## Notes
- Fill in exact screenshot filenames as each lab specifies them (graders match by filename).
