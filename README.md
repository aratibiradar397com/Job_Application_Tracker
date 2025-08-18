# Job_Application_Tracker
Job Application Tracker (Mini ATS)

A Mini Applicant Tracking System (ATS) built using the MERN stack.
It allows recruiters to manage job applications visually with a Kanban board and get real-time insights through an analytics dashboard.

🚀 Features
🔹 Job Application Tracker (Kanban Board)

Drag-and-drop applications across stages: Applied → Interview → Offer → Rejected

Add new applications with details: Name, Role, Experience, Resume Link

Search & filter by role, status, or experience

All data stored and fetched from MongoDB Atlas

🔹 Analytics Dashboard

📊 Charts (using Recharts / Chart.js)

Bar/Pie charts showing candidates in each stage

Role-based breakdown of candidates

Stat card: Average candidate experience

Auto-updates when database changes

⚡ Tech Stack

Frontend: React (Vite) + TailwindCSS + react-beautiful-dnd / framer-motion
Backend: Node.js + Express
Database: MongoDB Atlas

📂 Project Structure
Job_Application_Tracker/
│── client/          # React frontend
│   ├── src/
│   │   ├── components/   # Kanban, Dashboard, Forms
│   │   ├── pages/        # UI pages
│   │   └── App.js
│── server/          # Node.js backend
│   ├── models/      # MongoDB schemas
│   ├── routes/      # API routes
│   ├── controllers/ # Business logic
│   └── index.js     # Express server
│── README.md

⚙️ Installation & Setup
1️⃣ Clone the repo
git clone https://github.com/aratibiradar397com/Job_Application_Tracker.git
cd Job_Application_Tracker

2️⃣ Install dependencies
# Install backend dependencies
cd server
npm install

# Install frontend dependencies
cd ../client
npm install

3️⃣ Setup environment variables

Create a .env file in server/ with:

MONGO_URI=your_mongodb_connection_string
PORT=5000

4️⃣ Run the project
# Run backend
cd server
npm start

# Run frontend
cd ../client
npm run dev
