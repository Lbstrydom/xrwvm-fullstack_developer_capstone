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
- [x] Node.js/Express + MongoDB service for dealers & reviews, dockerized
  - Implemented `fetchDealers`, `fetchDealers/:state`, `fetchDealer/:id` in `server/database/app.js` (fetchReviews/fetchReviews/dealer/:id/insert_review were pre-provided)
  - `docker build . -t nodeapp` + `docker compose up` — both containers (mongo, node api) running, data seeded from `data/dealerships.json` and `data/reviews.json`
  - Verified all endpoints locally at http://localhost:3030 — screenshots `node-fetchreviews.png`, `node-fetchdealers.png`
  - Saved curl transcripts: `getdealerreviews.txt`, `getalldealers.txt`, `getdealerbyid.txt`, `getdealersbyState.txt`
  - Pushed (commit 8f8fd82)
- [x] Sentiment analyzer deployed
  - IBM Cloud Code Engine not available in this local environment (no `ibmcloud` CLI/account) — ran `server/djangoapp/microservices` (Flask + NLTK VADER) locally via Docker instead: `docker build . -t senti_analyzer` + `docker run -p 5050:5000 senti_analyzer`
  - Verified `/analyze/Fantastic%20services` → `{"sentiment": "positive"}`
  - Saved curl transcript: `analyzereview.txt`; screenshot (URL + result): `sentiment_analyzer.png`
  - **TODO for you**: if the grading requires an actual Code Engine URL, deploy `server/djangoapp/microservices` there separately and update `sentiment_analyzer_url` in `djangoapp/.env`
- [x] Django models/views for car make & model
  - `CarMake`/`CarModel` models added (`djangoapp/models.py`), migrated via `makemigrations djangoapp` + `migrate --run-syncdb`
  - Registered in Django admin with `CarModelInline` under `CarMakeAdmin` (`djangoapp/admin.py`)
  - `populate.py` seeds 5 makes / 15 models on first call to `get_cars`
  - `get_cars` view + `djangoapp/get_cars` route return combined make/model list as JSON — verified: 5 makes, 15 models
  - Reviewer superuser created per lab spec: username `root`, password `root` (as instructed, for grader admin access)
  - Screenshots: `admin_login.png`, `admin_logout.png` (logged in/out as `root`)
  - Saved curl transcript: `getallcarmakes.txt`
  - Pushed (commit 840bf45)
- [x] Django proxy services integrating dealers & reviews
  - `restapis.py`: `get_request`, `analyze_review_sentiments`, `post_review` — bridges Django to the Node/Mongo backend (`backend_url`) and the sentiment microservice (`sentiment_analyzer_url`), both configured in `djangoapp/.env` (localhost URLs)
  - Views: `get_dealerships` (all/by state), `get_dealer_details`, `get_dealer_reviews` (each review run through sentiment analysis), `add_review` (auth-gated — 403 if anonymous)
  - Routes: `get_dealers`, `get_dealers/<state>`, `dealer/<id>`, `review/dealer/<id>`, `add_review`
  - Verified end-to-end: fetched dealers/dealer/reviews-with-sentiment via curl; confirmed `add_review` returns 403 unauthenticated and 200 when logged in (posted a review, saw it appear via `review/dealer/<id>` with sentiment attached)
  - Pushed (commit a1c9e39)

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
