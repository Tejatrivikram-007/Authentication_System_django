Here’s a suggested content for your **GitHub README** to describe your Django project on authentication with decorators:

---

# Django Authentication System with Decorators

## Overview

This Django project implements a **user authentication system** with the use of **decorators** to control access to different views based on the user's authentication status. It ensures that only logged-in users can access specific pages, and only unauthenticated users can access others, such as registration and login.

### Features:
- **User Registration**: Allows new users to create an account using Django's built-in `UserCreationForm`.
- **User Login**: Allows registered users to log in using Django's `AuthenticationForm`.
- **User Logout**: Allows users to log out and clear their session.
- **Access Control via Decorators**: Implements `@auth` and `@guest` decorators for controlling access to views.
  - **`@guest`**: Restricts access to pages like **register** and **login** to unauthenticated users only.
  - **`@auth`**: Restricts access to pages like **home** to authenticated users only.
- **Redirection**: Automatically redirects users to the appropriate pages based on their authentication status (e.g., redirects unauthenticated users to login, and logged-in users to home).

## Installation

### Prerequisites
Ensure you have the following installed:
- **Python 3.x**
- **Django**

### Steps to Run the Project Locally

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Tejatrivikram-007/Authentication_System_django.git
   cd Authentication_System_django
   ```

2. **Create a virtual environment** (recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows, use venv\Scripts\activate
   ```

3. **Install required dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Run migrations**:
   ```bash
   python manage.py migrate
   ```

5. **Start the development server**:
   ```bash
   python manage.py runserver
   ```

6. **Visit** `http://127.0.0.1:8000/` in your browser to see the project in action.

## Authentication Flow

- **User Registration**: 
   - Users can create an account via the **register page**. After registration, they are redirected to the **login page**.
   - **`UserCreationForm`** is used for creating users.

- **User Login**: 
   - Registered users can log in via the **login page**.
   - **`AuthenticationForm`** is used to authenticate users by verifying the username and password.

- **User Logout**: 
   - Logged-in users can log out, which will redirect them to the **login page**.

- **Access Control**: 
   - The **`@guest`** decorator ensures that only unauthenticated users can access the registration and login views.
   - The **`@auth`** decorator ensures that only authenticated users can access the homepage (`/home`).
   - If an authenticated user tries to access the login or register pages, they are automatically redirected to the home page.
   
## Decorators Used

This project uses two custom decorators to manage user access:

### `@guest` Decorator
Restricts access to views for authenticated users. If a user is logged in, they will be redirected to the home page.

Example:
```python
@guest
def register_view(request):
    # Only unauthenticated users can access this view
    pass
```

### `@auth` Decorator
Restricts access to views for unauthenticated users. If a user is not logged in, they will be redirected to the login page.

Example:
```python
@auth
def home(request):
    # Only authenticated users can access this view
    pass
```

## URL Routing

- **`/register/`**: Displays the registration page.
- **`/login/`**: Displays the login page.
- **`/logout/`**: Logs the user out and redirects to the login page.
- **`/home/`**: Displays the home page for authenticated users.

## Code Overview

- **views.py**: Contains all the views for registration, login, logout, and home.
- **middlewares.py**: Contains the custom decorators `@auth` and `@guest` to enforce access control.
- **urls.py**: Maps URLs to their respective views.
- **templates/**: Contains the HTML templates for the registration, login, and home pages.

## Future Enhancements

- **Password Reset**: Add functionality to allow users to reset their password.
- **User Profile**: Allow users to create and update their profiles after logging in.
- **Role-based Access Control**: Implement role-based authentication to restrict access to views based on user roles (e.g., admin, user).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

This content provides a clear, structured explanation of the Django authentication project with decorators. It gives potential collaborators or users enough context to understand the purpose and features of the project, and also how to run it locally.
