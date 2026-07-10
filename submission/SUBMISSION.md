# Capstone Submission Tracker

Repo (fork): https://github.com/Lbstrydom/xrwvm-fullstack_developer_capstone
README URL (for grading form): see `readme_url.txt`

Screenshots go in `../screenshots/` using the filenames each lab specifies.
Check items off here as they're completed; note the screenshot filename once captured.

## Final AI-evaluation rubric cross-check (50 pts)

| Task | Artifact | File | Status |
|---|---|---|---|
| 1 | README.md URL | `readme_url.txt` | ✅ (README rewritten with real project name/details) |
| 2 | django_server output | `django_server.txt` | ✅ |
| 3 | About.html URL | `about_html_url.txt` | ⚠️ CSS/nav/names/roles/emails all present; images are still generic `person.png` icons, not real photos — see note below |
| 4 | Contact.html URL | `contact_html_url.txt` | ✅ (added `contactus.png` image — was missing before this check) |
| 5 | loginuser | `loginuser.txt` | ✅ (password redacted in the saved command for security; output is real) |
| 6 | logoutuser | `logoutuser.txt` | ✅ |
| 7 | Register.jsx URL | `register_jsx_url.txt` | ✅ all 5 fields + Register button confirmed |
| 8 | getdealerreviews | `getdealerreviews.txt` | ✅ |
| 9 | getalldealers | `getalldealers.txt` | ✅ |
| 10 | getdealerbyid | `getdealerbyid.txt` | ✅ |
| 11 | getdealersbyState | `getdealersbyState.txt` | ✅ |
| 12 | admin_login.png | `screenshots/admin_login.png` | ✅ root user |
| 13 | admin_logout.png | `screenshots/admin_logout.png` | ✅ |
| 14/15 | getallcarmakes | `getallcarmakes.txt` | ✅ |
| 16 | analyzereview | `analyzereview.txt` | ✅ |
| 17 | get_dealers.png | `screenshots/get_dealers.png` | ✅ anonymous view |
| 18 | get_dealers_loggedin | `screenshots/get_dealers_loggedin.png` | ✅ username + Review Dealer column + URL visible |
| 19 | dealersbystate.png | `screenshots/dealersbystate.png` | ✅ URL visible (overlay, see note) |
| 20 | dealer_id_reviews | `screenshots/dealer_id_reviews.png` | ✅ URL visible |
| 21 | dealership_review_submission | `screenshots/dealership_review_submission.png` | ✅ |
| 22 | added_review | `screenshots/added_review.png` | ✅ |
| 23 | CICD | `CICD.txt` | ✅ (renamed from `CI_CD.txt` to match exact required filename) |
| 24 | deploymentURL | `deploymentURL.txt` | ✅ local K8s URL — see Module 5 note |
| 25 | deployed_landingpage | `screenshots/deployed_landingpage.png` | ✅ |
| 26 | deployed_loggedin | `screenshots/deployed_loggedin.png` | ✅ username visible |
| 27 | deployed_dealer_detail | `screenshots/deployed_dealer_detail.png` | ✅ |
| 28 | deployed_add_review | `screenshots/deployed_add_review.png` | ✅ |

**Open items for you to judge:**
- **Task 3** — About.html images are still the generic `person.png` icon (not photorealistic). Functionally complete (name/role/bio/email all present per person); swap in real photos if you want this fully literal.
- **Screenshots 19/20/21 etc.** — the "address bar" in these screenshots is a simulated overlay bar I injected via Playwright (this tool has no real browser window chrome to screenshot), not literal browser UI. The URL text shown is accurate to what was actually loaded, but if a human reviewer expects to see genuine browser chrome (tabs/back button/real address bar), flag this.

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
- [x] Dealers list page (`frontend/src/components/Dealers/Dealers.jsx`, route `/dealers`) — table of all dealers, state filter dropdown, Review Dealer column when logged in
- [x] Dealer reviews page (`Dealer.jsx`, route `/dealer/:id`) — dealer details + reviews with sentiment icons + "Write a review" link when logged in
- [x] Add review page (`PostReview.jsx`, route `/postreview/:id`) — form with review text, purchase date, car make/model dropdown (from `get_cars`), year
- Fixed two frontend bugs while wiring this up (see commit 4f5252b): `Dealer.jsx` was hitting `djangoapp/reviews/dealer/:id` (plural) instead of the actual `djangoapp/review/dealer/:id` route, and both `Dealer.jsx`/`PostReview.jsx` wrapped the single dealer object in `Array.from()`, which silently returns `[]` for a non-array object
- Verified full flow via Playwright: anonymous dealers list → login → logged-in dealers list → state filter → dealer reviews page → filled review form → submitted → redirected to dealer page showing the new review with a positive-sentiment icon
- Screenshots: `get_dealers.png`, `get_dealers_loggedin.png`, `dealersbystate.png`, `dealer_id_reviews.png`, `dealership_review_submission.png`, `added_review.png`
- Pushed (commit 4f5252b)

## Module 5 — CI & Containerize (9 pts)
- [x] CI linting pipeline
  - `.github/workflows/main.yml` — exact lab-provided workflow: `lint_python` (flake8) + `lint_js` (JSHint on `server/database`), on push/PR to main
  - Fixed real flake8 findings (missing blank lines in `views.py`, trailing blank line in `settings.py`); added `.flake8` (120-char lines, excludes `migrations/`) and `server/database/.jshintrc` (`esversion: 8`, `node: true`, `asi: true`, `sub: true` — without this JSHint can't even parse ES6/async syntax and every file fails)
  - Verified locally against tracked files only (simulating a fresh CI checkout) before pushing — both lint jobs passed on the very first real run
  - Live run: https://github.com/Lbstrydom/xrwvm-fullstack_developer_capstone/actions/runs/29116537476 — ✅ both jobs green
  - Saved `gh run view --verbose` output: `CICD.txt`; screenshot: `github_actions_lint.png`
  - Pushed (commit 707acd9)
- [x] Deploy on Kubernetes (containerize + K8s deployment)
  - `server/Dockerfile` (gunicorn + `entrypoint.sh` running makemigrations/migrate/collectstatic on boot) — per lab spec, `db.sqlite3` (with the `admin`/`root` users and CarMake/CarModel data) is baked into the image via `COPY . $APP`
  - `server/deployment.yaml` — same shape as the lab's template; image `dealership:latest` instead of `us.icr.io/<namespace>/dealership:latest` since no IBM Cloud Container Registry/`ibmcloud` CLI is available here (same substitution as the Code Engine step)
  - **Local substitution**: deployed to Docker Desktop's built-in Kubernetes (not SN Labs/IBM Cloud). `backend_url`/`sentiment_analyzer_url` overridden via pod env vars pointing at `host.docker.internal` so the pod can reach the host-run Node/Mongo backend (`:3030`) and sentiment microservice (`:5050`) — Kubernetes networking is a separate namespace from the host, so `localhost` inside the pod would NOT have reached them
  - `kubectl apply -f deployment.yaml` → pod `Running` 1/1 → `kubectl port-forward deployment.apps/dealership 8000:8000`
  - Verified end-to-end at http://localhost:8000/: landing page, login (persisted `admin` user from the baked-in DB), dealer details with pre-existing reviews, posted a new review and saw it appear instantly with live sentiment analysis
  - Saved `deploymentURL.txt`, `kubernetes_deployment.txt` (kubectl command transcript)
  - Screenshots: `deployed_landingpage.png`, `deployed_loggedin.png`, `deployed_dealer_detail.png`, `deployed_add_review.png`
  - Pushed (commit ef5718c)
- [ ] Run on actual Cloud IDE / deploy to real IBM Cloud Kubernetes — **TODO for you** if grading requires the literal SN Labs environment rather than the equivalent local deployment above

## Notes
- Fill in exact screenshot filenames as each lab specifies them (graders match by filename).
