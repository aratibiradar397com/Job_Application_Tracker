# Job Application Tracker - Mini ATS

A comprehensive Applicant Tracking System (ATS) built with Next.js 14, TypeScript, and client-side persistent storage. Features a modern Kanban board for tracking applications, analytics dashboard with real-time insights, and enhanced user experience with dark mode support.

## 🚀 Project Overview

This application serves as a complete job application management system designed for job seekers to track their application pipeline. Built with modern web technologies, it provides a seamless experience for managing job applications from initial application to final outcome.

### Architecture

The application follows a **client-side first architecture** with:
- **Frontend**: Next.js 14 with App Router for modern React development
- **Storage**: Browser localStorage for persistent data storage (survives page refresh)
- **State Management**: React hooks for local state management
- **Styling**: TailwindCSS with dark/light mode support
- **Type Safety**: Full TypeScript implementation throughout

## ✨ Features

### Core Features
- **Interactive Kanban Board**: Drag-and-drop interface for managing applications across stages (Applied → Interview → Offer → Rejected)
- **Real-time Analytics Dashboard**: Visual insights with interactive charts showing pipeline performance, conversion rates, and trends
- **Complete CRUD Operations**: Add, edit, delete, and track candidate applications with detailed information
- **Advanced Search & Filter**: Filter by status, role, and search functionality across all application data
- **Persistent Storage**: Data survives browser sessions and page refreshes using localStorage
- **Delete Functionality**: Remove applications directly from Kanban board with hover-to-reveal delete buttons
- **Resume Link Integration**: View candidate resumes via provided links with external link indicators

### Enhanced User Experience
- **Dark/Light Mode**: Complete theme switching with system preference detection
- **Toast Notifications**: Success and error feedback for all user actions
- **Responsive Design**: Mobile-first design that works on all screen sizes
- **Modern UI Components**: Custom-built UI component library with consistent styling
- **Loading States**: Proper loading indicators and error handling
- **Cache Busting**: Ensures fresh data loading and prevents stale data issues

## 🏗️ Tech Stack & Libraries

### Core Framework
- **Next.js 14.0.0**: React framework with App Router for modern development
- **React 18**: Latest React with concurrent features
- **TypeScript 5**: Full type safety and enhanced developer experience

### Styling & UI
- **TailwindCSS 3.3.0**: Utility-first CSS framework
- **Lucide React 0.294.0**: Modern icon library
- **clsx 2.0.0**: Conditional className utility
- **tailwind-merge 2.0.0**: Merge Tailwind classes efficiently

### Data Visualization & Interaction
- **Recharts 2.8.0**: Composable charting library for React
- **react-beautiful-dnd 13.1.1**: Beautiful drag-and-drop for lists

### Development Tools
- **ESLint**: Code linting with Next.js configuration
- **PostCSS**: CSS processing
- **Autoprefixer**: CSS vendor prefixing

## 📊 Data Schema & Storage

### LocalStorage Structure

The application uses browser localStorage for data persistence with the following structure:

```typescript
interface StoredApplication {
  _id: string                    // Unique identifier
  candidateName: string          // Full name of candidate
  email: string                  // Contact email
  role: string                   // Position applied for
  yearsOfExperience: number      // Years of relevant experience
  status: 'Applied' | 'Interview' | 'Offer' | 'Rejected'
  appliedDate: Date              // When application was submitted
  lastUpdated: Date              // Last modification timestamp
  location?: string              // Job/candidate location
  salary?: number                // Expected/offered salary
  source?: string                // Where job was found (LinkedIn, etc.)
  notes?: string                 // Additional notes
  resumeLink?: string            // Link to candidate's resume
  phoneNumber?: string           // Contact phone number
}
```

### Storage Keys
- `job_applications`: Array of all application data
- `next_application_id`: Auto-incrementing ID counter

### Default Data
The application initializes with 3 sample applications demonstrating different statuses and data completeness.

## 🛠️ Setup & Installation

### Prerequisites
- Node.js 18+ 
- npm or yarn package manager
- Modern web browser with localStorage support

### Local Development Setup

1. **Clone Repository**
   ```bash
   git clone <repository-url>
   cd job-application-tracker
   ```

2. **Install Dependencies**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Environment Setup** (Optional)
   ```bash
   # Create environment file for any future configurations
   cp .env.local.example .env.local
   ```

4. **Start Development Server**
   ```bash
   npm run dev
   # or
   yarn dev
   ```

5. **Access Application**
   - Open [http://localhost:3000](http://localhost:3000)
   - Data persists automatically in browser localStorage
   - No database setup required!

### Production Build

```bash
# Build for production
npm run build

# Start production server
npm start
```

### Deployment Options

#### Vercel (Recommended)
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel
```

#### Netlify
```bash
# Build static export
npm run build

# Upload dist folder to Netlify
```

#### Docker
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "start"]
```

## 🔗 API Endpoints

The application provides RESTful API endpoints for data operations:

- `GET /api/applications` - Fetch all applications with optional query filters
- `POST /api/applications` - Create new application entry
- `GET /api/applications/[id]` - Get specific application by ID
- `PUT /api/applications/[id]` - Update existing application
- `DELETE /api/applications/[id]` - Delete application by ID
- `GET /api/analytics` - Get computed analytics and metrics data

*Note: All endpoints work with localStorage as the data source, ensuring client-side persistence.*

## 📁 Project Structure

```
src/
├── app/                          # Next.js App Router
│   ├── api/                      # API Routes
│   │   ├── applications/         # Application CRUD endpoints
│   │   │   ├── route.ts          # GET, POST /api/applications
│   │   │   └── [id]/route.ts     # GET, PUT, DELETE /api/applications/[id]
│   │   ├── analytics/route.ts    # Analytics data endpoint
│   │   └── health/route.ts       # Health check endpoint
│   ├── kanban/                   # Kanban board page
│   │   └── page.tsx
│   ├── analytics/                # Analytics dashboard page
│   │   └── page.tsx
│   ├── globals.css               # Global styles
│   ├── layout.tsx                # Root layout with navigation
│   └── page.tsx                  # Homepage
├── components/                   # React Components
│   ├── ui/                       # Reusable UI components
│   │   ├── Badge.tsx             # Status badges
│   │   ├── Button.tsx            # Button component
│   │   ├── Card.tsx              # Card containers
│   │   ├── Input.tsx             # Form inputs
│   │   └── index.ts              # Component exports
│   ├── ApplicationCard.tsx       # Individual application card
│   ├── ApplicationForm.tsx       # Add/edit application form
│   ├── AnalyticsDashboard.tsx    # Analytics charts and metrics
│   ├── KanbanBoard.tsx           # Drag-and-drop board
│   ├── Navigation.tsx            # App navigation header
│   ├── SearchAndFilter.tsx       # Search and filter controls
│   └── ThemeToggle.tsx           # Dark/light mode toggle
├── lib/                          # Utility libraries
│   ├── database.ts               # MongoDB connection (legacy)
│   ├── storage.ts                # localStorage utilities
│   └── utils.ts                  # General utilities
├── models/                       # Data models
│   └── Application.ts            # Mongoose schema (legacy)
└── types/                        # TypeScript definitions
    └── global.d.ts               # Global type declarations
```

## 🎯 Usage Guide

### Adding Applications
1. Navigate to the Kanban board
2. Click "Add Application" button
3. Fill in candidate details and job information
4. Submit to add to "Applied" column

### Managing Application Pipeline
1. **Drag & Drop**: Move cards between columns to update status
2. **Edit Details**: Click on application cards to view/edit information
3. **Delete Applications**: Hover over cards to reveal delete button
4. **View Resume**: Click "View Resume" link if provided

### Analytics & Insights
1. Navigate to Analytics dashboard
2. View real-time metrics and charts
3. Use refresh button for latest data
4. Analyze conversion rates and trends

### Search & Filter
1. Use search bar to find specific candidates or roles
2. Apply status filters to narrow results
3. Combine search and filters for precise results

## 🚀 Recent Enhancements

### ✅ Completed Features
- **Persistent Storage**: Full localStorage integration replacing MongoDB dependency
- **Delete Functionality**: Hover-to-reveal delete buttons on application cards
- **Resume Links**: Direct links to candidate resumes with external indicators
- **Real-time Analytics**: Live updating metrics and charts
- **Toast Notifications**: Success/error feedback for all user actions
- **Dark Mode**: Complete theme switching with system preference detection
- **Enhanced UI**: Modern component library with consistent styling

### 🔄 Architecture Migration
- **From**: MongoDB Atlas + Mongoose ODM
- **To**: Client-side localStorage with TypeScript interfaces
- **Benefits**: 
  - No database setup required
  - Instant data persistence
  - Offline functionality
  - Simplified deployment
  - No external dependencies

## 🔮 Future Enhancements

- **File Upload**: Resume upload and preview functionality
- **Export Features**: PDF export for analytics and application data
- **Authentication**: User accounts and secure access
- **Multi-user Support**: Team collaboration features
- **Email Integration**: Automated notifications and reminders
- **Advanced Analytics**: Predictive insights and reporting
- **Mobile App**: React Native companion app
- **Integration APIs**: Connect with job boards and ATS systems

## 🤝 Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

demo video -https://drive.google.com/file/d/1Mv_8uCoeYft5qZ3hSuNMmtZ_KytkEe1R/view?usp=sharing