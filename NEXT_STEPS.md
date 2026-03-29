# Spendly - Next Steps & Feature Roadmap

## Project Overview

Spendly is a Flask-based personal expense tracking application. Current status: **Early Development** - routes and templates are scaffolded but core functionality is not implemented.

---

## Phase 1: Core Infrastructure (Critical - Required First)

### 1. Database Setup (`database/db.py`)
**Status:** Empty stub
**Tasks:**
- [ ] `get_db()` - Return SQLite connection with `row_factory` and foreign keys enabled
- [ ] `init_db()` - Create tables using `CREATE TABLE IF NOT EXISTS`
  - `users` table (id, name, email, password_hash, created_at)
  - `expenses` table (id, user_id, amount, category, description, date, created_at)
  - `categories` table (id, user_id, name, color - optional for custom categories)
- [ ] `seed_db()` - Insert sample development data

### 2. Authentication System
**Status:** Templates exist, routes are placeholders
**Tasks:**
- [ ] Implement POST `/register` - Create user with hashed password
- [ ] Implement POST `/login` - Session-based authentication
- [ ] Implement `/logout` - Clear session and redirect
- [ ] Add password hashing library to `requirements.txt` (bcrypt or argon2-cffi)
- [ ] Add `@login_required` decorator for protected routes

---

## Phase 2: Core Expense Management

### 3. Profile/Dashboard Page (`/profile`)
**Status:** Returns placeholder text
**Tasks:**
- [ ] Create `profile.html` template with dashboard layout
- [ ] Display monthly expense summary
- [ ] Show category breakdown
- [ ] List recent transactions
- [ ] Add navigation to add/edit/delete expenses

### 4. Add Expense (`/expenses/add`)
**Status:** Returns placeholder text
**Tasks:**
- [ ] Create expense form template (or modal)
- [ ] Form fields: amount, category (dropdown), date, description (optional)
- [ ] Implement POST handler to insert into database
- [ ] Add success/error flash messages
- [ ] Redirect to dashboard on success

### 5. Edit Expense (`/expenses/<id>/edit`)
**Status:** Returns placeholder text
**Tasks:**
- [ ] Pre-populate form with existing expense data
- [ ] Implement PUT/PATCH handler
- [ ] Validate ownership (user can only edit their own expenses)
- [ ] Redirect with confirmation message

### 6. Delete Expense (`/expenses/<id>/delete`)
**Status:** Returns placeholder text
**Tasks:**
- [ ] Confirmation dialog before delete
- [ ] Implement DELETE handler
- [ ] Validate ownership
- [ ] Redirect with confirmation message

---

## Phase 3: Enhanced Features

### 7. Category Management
**Tasks:**
- [ ] Define default categories (Food, Transport, Bills, Health, Entertainment, Shopping, Other)
- [ ] Allow users to create custom categories
- [ ] Category icons/colors for visual distinction

### 8. Filtering & Date Range Selection
**Tasks:**
- [ ] Filter expenses by date range (last 7 days, last month, custom range)
- [ ] Filter by category
- [ ] URL query parameters for shareable filtered views
- [ ] Clear filters button

### 9. Data Visualization
**Tasks:**
- [ ] Add Chart.js or similar library
- [ ] Pie chart for category breakdown
- [ ] Bar chart for monthly comparison
- [ ] Line graph for spending trends over time

---

## Phase 4: Polish & Advanced Features

### 10. Form Validation & User Feedback
**Tasks:**
- [ ] Client-side validation in `static/js/main.js`
- [ ] Server-side validation for all inputs
- [ ] Flash message component in templates
- [ ] Error state styling in forms

### 11. Export & Reports
**Tasks:**
- [ ] Export expenses to CSV
- [ ] Generate monthly summary report
- [ ] Print-friendly view

### 12. Budget Alerts (Advanced)
**Tasks:**
- [ ] Set monthly budget per category
- [ ] Visual progress bars showing budget usage
- [ ] Alert when approaching/exceeding budget

---

## File Structure To Implement

```
expense-tracker/
├── app.py                 # Routes (need implementation)
├── database/
│   └── db.py             # Database helpers (NEEDS IMPLEMENTATION)
├── templates/
│   ├── base.html         # Base template with nav/footer
│   ├── landing.html      # Landing page (DONE)
│   ├── login.html        # Login form (DONE)
│   ├── register.html     # Register form (DONE)
│   ├── profile.html      # Dashboard (TODO)
│   └── expenses/
│       ├── add.html      # Add expense form (TODO)
│       └── edit.html     # Edit expense form (TODO)
├── static/
│   ├── css/style.css     # Styles (partially done)
│   └── js/main.js        # Client-side JS (TODO)
└── requirements.txt      # Dependencies (needs bcrypt/argon2)
```

---

## Recommended Development Order

1. **Database** (`db.py`) - Foundation for everything
2. **Authentication** - Register, login, logout, session management
3. **Add Expense** - Core CRUD operation
4. **Dashboard** - View expenses
5. **Edit/Delete** - Complete CRUD
6. **Filtering** - Improve UX
7. **Visualizations** - Make it insightful
8. **Polish** - Validation, export, advanced features

---

## Dependencies to Add

```txt
flask==3.1.3
werkzeug==3.1.6
pytest==8.3.5
pytest-flask==1.3.0
bcrypt==4.1.2          # OR argon2-cffi
python-dotenv==1.0.0   # For environment variables (optional)
```
