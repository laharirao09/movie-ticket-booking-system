# Movie Ticket Booking System Backend

This project is a backend assignment for a movie ticket booking system, built using Python, Django, and Django REST Framework, secured with JWT authentication.

---

## ✅ Deliverables Met

* **Authentication:** Signup, Login, and JWT protection implemented.
* **Models:** `Movie`, `Show`, `Booking` models created with correct relationships.
* **APIs:** All required endpoints (`/movies/`, `/shows/book/`, `/my-bookings/`, `/bookings/cancel/`) are implemented.
* **Business Rules:** Prevention of double-booking, overbooking, and freeing up the seat upon cancellation are enforced in the views.
* **Documentation:** Swagger UI is fully integrated.
* **Bonus Points:** Implemented input validation, security check (user can't cancel others' booking), proper error handling, and concurrency handling via database transactions.

## ⚙️ Tech Stack

* **Python**
* **Framework:** Django
* **API:** Django REST Framework (DRF)
* **Authentication:** Simple JWT (`djangorestframework-simplejwt`)
* **Documentation:** Swagger/OpenAPI (`drf-spectacular`)
* **Database:** SQLite (default Django setup)

## 🚀 Setup Instructions

Follow these steps to get the project running locally:

1.  **Clone the repository:**
    ```bash
    # (Replace with your actual GitHub repository URL after pushing)
    # git clone [https://github.com/yourusername/movie_booking_system.git](https://github.com/yourusername/movie_booking_system.git)
    # cd movie_booking_system
    ```

2.  **Create and Activate Virtual Environment:**
    ```bash
    python -m venv venv
    # On Linux/macOS:
    source venv/bin/activate
    # On Windows (Command Prompt/PowerShell):
    .\venv\Scripts\activate
    ```

3.  **Install Dependencies:**
    *Ensure you have run `pip freeze > requirements.txt` previously.*
    ```bash
    pip install -r requirements.txt
    ```

4.  **Run Migrations:**
    ```bash
    python manage.py migrate
    ```

5.  **Create Superuser (Optional, for Admin access):**
    ```bash
    python manage.py createsuperuser
    ```

6.  **Run the Server:**
    ```bash
    python manage.py runserver
    ```
    The API will be accessible at `http://127.0.0.1:8000/`.

## 📚 API Documentation (Swagger)

The full interactive API documentation is available at:

[http://127.0.0.1:8000/swagger/](http://17.0.0.1:8000/swagger/)

## 🔑 API Flow and Authentication Guide

All protected endpoints require a Bearer JWT token in the `Authorization` header.

### Step 1: User Registration

* **Endpoint:** `POST /signup/`
* **Purpose:** Register a new user.
* **Body:**
    ```json
    {
        "username": "testuser", 
        "email": "test@example.com", 
        "password": "securepassword", 
        "password2": "securepassword"
    }
    ```

### Step 2: Get JWT Token (Login)

* **Endpoint:** `POST /login/`
* **Purpose:** Authenticate and receive JWT tokens.
* **Body:**
    ```json
    {
        "username": "testuser", 
        "password": "securepassword"
    }
    ```
* **Response:** Returns `access` and `refresh` tokens. **Copy the `access` token.**

### Step 3: Use the Token

To call any protected endpoint (e.g., `/my-bookings/`), you must set the `Authorization` header in your request (e.g., using Swagger UI's "Authorize" button or a tool like Postman):

| Key | Value |
| :--- | :--- |
| `Authorization` | `Bearer <ACCESS_TOKEN_FROM_STEP_2>` |

**Example Endpoints Summary:**

| Method | Path | Description | Required Auth |
| :--- | :--- | :--- | :--- |
| `GET` | `/movies/` | List all available movies. | No |
| `GET` | `/movies/{movie_id}/shows/` | List all showtimes for a movie. | Yes |
| `POST` | `/shows/{show_id}/book/` | Book a seat for a show. | Yes |
| `GET` | `/my-bookings/` | View all bookings made by the logged-in user. | Yes |
| `POST` | `/bookings/{booking_id}/cancel/` | Cancel an existing booking. | Yes |

---

### Step 2.3: Final Step: Push to GitHub

This is the very last step. You must upload all your code (including `requirements.txt`, the `README.md`, the `core` folder, and the `booking` folder) to a GitHub repository.

1.  **Initialize Git** (if you haven't already):
    ```bash
    git init
    ```

2.  **Add all files** (tells Git to track your files):
    ```bash
    git add .
    ```

3.  **Commit your work** (saves a version of your work):
    ```bash
    git commit -m "Final submission of Movie Ticket Booking System assignment."
    ```

4.  **Create the Repository on GitHub:** Go to the GitHub website, create a new empty repository, and follow their instructions to link your local project to it (usually by adding a remote and pushing).

5.  **Push the code** (sends the code to GitHub):
    ```bash
    git push -u origin main
    ```

