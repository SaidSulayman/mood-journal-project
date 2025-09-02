# Mood Journal 📓✨


A modern, privacy-focused web application for tracking your daily mood and journaling. Built with a React frontend and a Node.js/Express backend, it provides a clean, intuitive interface for users to log their emotional well-being over time.


![Mood Journal App Screenshot](https://via.placeholder.com/800x400.png?text=Mood+Journal+App+Screenshot) *// Replace with an actual screenshot path*


## 🚀 Features


- **Daily Mood Logging:** Quickly select your mood from a colourful spectrum of emotions (e.g., happy, sad, anxious, energetic).
- **Rich Journal Entries:** Add detailed notes, thoughts, and reflections to each daily log.
- **Visual Insights:** View your mood history through interactive charts and calendars to identify patterns and trends over time.
- **Data Privacy First:** Your journal entries are yours alone. They are stored securely and never shared.
- **Responsive Design:** A seamless experience on desktop, tablet, and mobile devices.
- **Search & Filter:** Easily find past entries by date, mood, or keywords.


## 🛠️ Tech Stack


### Frontend
-   **React** t (v18) – Component-bas UI library
-   **React Router r DOM – Client-si routing
-   **Chart.js / Recharts – For data visualization (mood charts)
-   **CSS-in-JS (Styled-components or Emotion)** OR **Tailwind d CSS – F styling
- Axios – HTTP client for API requests


### Backend
-   **Node.js** - Runtime environment
-   **Express.js** - Web application framework
-   **JWT (jsonwebtoken)** - For user authentication
-   **bcryptjs** - For password hashing


### Database
-   **MongoDB with Mongoose** - NoSQL database for flexible data storage of user entries.


### Deployment
-   **Frontend:** Vercel / Netlify
-   **Backend:** Heroku / Railway / DigitalOcean App Platform
-   **Database:** MongoDB Atlas (cloud)


## 📦 Installation & Local Development


Follow these steps to set up the project locally on your machine.


### Prerequisites
-   Node.js (v16 or higher)
-   npm or yarn
-   A MongoDB database (local or MongoDB Atlas)


### 1. Clone the Repository
```bash
git clone https://github.com/your-username/mood-journal-app.git
cd mood-journal-app
```


### 2. Backend Setup
```bash
# Navigate to the backend directory
cd backend


# Install dependencies
npm install


# Create a .env file in the /backend directory
touch .env
```
Populate the `.env` file with your environment variables:
```env
PORT=5000
MONGODB_URI=your_mongodb_connection_string_here
JWT_SECRET=your_super_secret_jwt_key_here
NODE_ENV=development
```


### 3. Frontend Setup
```bash
# Navigate to the frontend directory (from the root)
cd frontend


# Install dependencies
npm install


# Create a .env file in the /frontend directory
touch .env
```
Populate the `.env` file:
```env
REACT_APP_API_BASE_URL=http://localhost:5000/api
```


### 4. Run the Application
**Start the Backend Server:**
```bash
cd backend
npm run dev  # Runs the server with nodemon for development
```


**Start the Frontend Development Server:**
```bash
cd frontend
npm start  # Runs the app on http://localhost:3000
```
The frontend should automatically open in your browser. The backend API will be available on `http://localhost:5000`.


## 🗄️ API Endpoints


| Method | Endpoint | Description | Authentication |
| :--- | :--- | :--- | :--- |
| `POST` | `/api/auth/register` | Registers a new user | Public |
| `POST` | `/api/auth/login` | Logs in a user | Public |
| `GET` | `/api/entries` | Gets all entries for the logged-in user | Private (JWT) |
| `POST` | `/api/entries` | Creates a new journal entry | Private (JWT) |
| `GET` | `/api/entries/:id` | Gets a single entry by ID | Private (JWT) |
| `PUT` | `/api/entries/:id` | Updates an existing entry | Private (JWT) |
| `DELETE` | `/api/entries/:id` | Deletes an entry | Private (JWT) |
| `GET` | `/api/entries/stats/overview` | Gets mood statistics for charts | Private (JWT) |


## 🧪 Testing


**Backend Tests:**
```bash
cd backend
npm test  # Runs tests using Jest/Mocha
```


**Frontend Tests:**
```bash
cd frontend
npm test  # Launches the test runner (React Testing Library)
```


## 🚢 Deployment


This app is configured for easy deployment on modern platforms.


1.  **Backend:**
    -   Ensure your `MONGODB_URI` and `JWT_SECRET` are set in your hosting platform's environment variables.
    -   Deploy the `backend` folder to Heroku/Railway.


2.  **Frontend:**
    -   Update the `REACT_APP_API_BASE_URL` in the frontend's environment variables to point to your live backend URL (e.g., `https://my-mood-journal-api.herokuapp.com/api`).
    -   Build the project: `npm run build`
    -   Deploy the `build` folder to Netlify or Vercel.


## 🤝 Contributing


Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/your-username/mood-journal-app/issues).


1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request


Please ensure your code follows the existing style and all tests pass.


## 📄 License


This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.


## 🙏 Acknowledgments


-   Icons provided by [React Icons](https://react-icons.github.io/react-icons/).
-   Charting library [Chart.js](https://www.chartjs.org/).
-   Inspiration from mental health and wellness communities.


---


**⭐ Star this repo if you found it helpful!**