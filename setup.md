# Job Application Tracker Setup Guide

## Quick Start

1. **Install Dependencies**
   ```bash
   npm install
   ```

2. **Configure Environment**
   - Update `.env.local` with your MongoDB Atlas connection string
   - Replace the placeholder values with your actual credentials

3. **Start Development Server**
   ```bash
   npm run dev
   ```

4. **Seed Sample Data (Optional)**
   - Visit `http://localhost:3000/api/seed` (POST request) to add sample applications
   - Or use the application form to add data manually

## MongoDB Atlas Setup

1. Create account at [MongoDB Atlas](https://cloud.mongodb.com)
2. Create a new cluster (free tier available)
3. Create database user with read/write permissions
4. Get connection string from "Connect" → "Connect your application"
5. Update `.env.local` with your connection string

## Features Ready to Use

✅ **Kanban Board** - Drag & drop applications between stages
✅ **Analytics Dashboard** - Visual insights with charts
✅ **Application Management** - Add, edit, search applications
✅ **Responsive Design** - Works on all devices
✅ **Dark Mode** - Toggle theme in navigation
✅ **Real-time Updates** - Live data synchronization

## API Endpoints

- `GET /api/applications` - Fetch applications
- `POST /api/applications` - Create application
- `PUT /api/applications/[id]` - Update application
- `DELETE /api/applications/[id]` - Delete application
- `GET /api/analytics` - Get analytics data
- `POST /api/seed` - Seed sample data
