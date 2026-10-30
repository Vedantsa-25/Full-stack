# OnlineCourse — Django Final Project Assessment

A complete, runnable Django course and mock-exam application prepared around the seven visible assessment tasks. It includes the required model/admin implementation, Bootstrap course detail template, `submit` and `show_exam_result` views, URL routes, demo data, and tests.

## Assessment deliverables

| Task | Deliverable in this repository |
|---|---|
| 1 | `onlinecourse/models.py` — Course, Lesson, Question, Choice, Enrollment, Submission |
| 2 | `onlinecourse/admin.py` — admin registrations and inline editing |
| 3 | Capture your own screenshot as `03-admin-site.png` showing **Authentication and Authorization** and **OnlineCourse** on `/admin/` |
| 4 | `onlinecourse/templates/onlinecourse/course_details_bootstrap.html` |
| 5 | `onlinecourse/views.py` — `submit` and `show_exam_result` |
| 6 | `onlinecourse/urls.py` — named paths for `submit` and `show_exam_result` |
| 7 | Run the mock exam, pass it, and capture your own result screenshot as `07-Final.png` |

## Run on Windows (PowerShell)

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
python manage.py migrate
python manage.py seed_demo
python manage.py createsuperuser
python manage.py runserver
```

If PowerShell blocks activation, use Command Prompt instead:

```bat
.venv\Scripts\activate.bat
```

Open these pages:

- Student catalogue: http://127.0.0.1:8000/
- Admin dashboard: http://127.0.0.1:8000/admin/
- Demo course: open the course from the catalogue.

Demo student login: `student` / `Student@12345` (change this password before any real deployment). Create a separate superuser for the admin site.

## Produce the two required screenshots

### Task 3 — Admin site

1. Sign in at `/admin/` using the superuser you created.
2. Confirm the admin index displays the **AUTHENTICATION AND AUTHORIZATION** section and the **ONLINECOURSE** section.
3. Maximize the browser and capture the page. Save it as `03-admin-site.png` in the repository root.

### Task 7 — Successful mock exam

1. Open `/`, select **Python Foundations: Core Concepts**, and open its mock exam.
2. Sign in as `student` with `Student@12345` if prompted.
3. Select the correct options: **def**, **list**, **3**, **==**, **except**.
4. Submit the assessment. The result page should display **Congratulations**, **100%**, and the answer review.
5. Capture the result page and save it as `07-Final.png` in the repository root.

Do not use a fabricated screenshot: capture the actual running application so the evidence matches the submitted code.

## Run tests

```powershell
python manage.py test
```

## Publish to GitHub

Create a new **public** GitHub repository (for example `onlinecourse-final-assessment`), extract this folder, then run these commands from this directory:

```powershell
git init
git add .
git commit -m "Build OnlineCourse final assessment project"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/onlinecourse-final-assessment.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username. After pushing, open each required file on GitHub and copy its browser URL into the corresponding assessment field. Use the file URLs below as patterns:

- `https://github.com/YOUR-USERNAME/onlinecourse-final-assessment/blob/main/onlinecourse/models.py`
- `https://github.com/YOUR-USERNAME/onlinecourse-final-assessment/blob/main/onlinecourse/admin.py`
- `https://github.com/YOUR-USERNAME/onlinecourse-final-assessment/blob/main/onlinecourse/templates/onlinecourse/course_details_bootstrap.html`
- `https://github.com/YOUR-USERNAME/onlinecourse-final-assessment/blob/main/onlinecourse/views.py`
- `https://github.com/YOUR-USERNAME/onlinecourse-final-assessment/blob/main/onlinecourse/urls.py`

## Implementation notes

- Exam submissions are tied to the authenticated student and lesson.
- Only answer IDs belonging to the lesson's exam are accepted.
- Multi-answer questions are graded by exact set matching; a partial or extra selection does not earn the question's points.
- Result pages are restricted to the student who owns the submission.
- The passing threshold is 70%.
- SQLite is configured for a straightforward local setup; no external database is required.

This is a learning/demo configuration. Before production deployment, set a strong secret key, disable debug mode, configure allowed hosts, HTTPS, and secure password handling.
