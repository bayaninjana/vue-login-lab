- Overview

This project is a simple login and dashboard system built with Vue 3, Pinia, and Bootstrap 5.
It demonstrates how to authenticate users, store tokens locally, and protect routes using router guards — all working completely offline using a mock API.


- Tech Stack
   -Vue 3 (Composition API)
   -Vue Router
   -Pinia (State Management)
   -Bootstrap 5
   -Mock Offline API (Custom http.js)


- Features

✅ User login with username and password
✅ Mock backend authentication (offline)
✅ Protected /dashboard route
✅ User info display after login
✅ Token stored in localStorage
✅ Logout functionality via navbar

- Sample Credentials
Use these credentials to log in:
Username	Password
admin	     1234
(If you use other credentials, an error message — “Invalid credentials” — will appear.)

- Project Structure
src/
 ├── api/
 │    └── http.js              # Offline mock API
 ├── components/
 │    └── AppNavbar.vue        # Navbar with logout link
 ├── pages/
 │    ├── LoginPage.vue        # Login form
 │    └── DashboardPage.vue    # User info after login
 ├── store/
 │    └── auth.js              # Pinia authentication store
 ├── router/
 │    └── index.js             # Routes + navigation guards
 ├── App.vue
 └── main.js

- Setup & Run Steps
1️⃣ Clone or create a new Vue project
If you haven’t already:

npm init vue@latest vue-login-lab
cd vue-login-lab
npm install

2️⃣ Install dependencies
npm install bootstrap pinia vue-router
3️⃣ Add Bootstrap to your project

In main.js:
import 'bootstrap/dist/css/bootstrap.min.css'
import 'bootstrap'

4️⃣ Replace/add these files

src/api/http.js – your offline mock API
Add pages: LoginPage.vue, DashboardPage.vue
Add store: auth.js
Add router guards in router/index.js

5️⃣ Run the project
npm run dev

- Mock API (src/api/http.js)
export const http = {
  async post(url, body) {
    // Simulate network delay
    await new Promise((r) => setTimeout(r, 500))

    if (url === '/auth/login') {
      if (body.username === 'admin' && body.password === '1234') {
        return {
          data: {
            id: 1,
            username: 'admin',
            firstName: 'Local',
            lastName: 'User',
            email: 'admin@example.com',
            token: 'mock-token-123456'
          }
        }
      } else {
        throw new Error('Invalid credentials')
      }
    }

    throw new Error('Unknown endpoint: ' + url)
  }
}

