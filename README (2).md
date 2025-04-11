
# Automated System for Recording Student Behaviour and Academic Performance

A comprehensive web application for tracking student behavior patterns, academic achievements, and generating insightful educational analytics.

## Overview

The Automated System for Recording Student Behaviour and Academic Performance streamlines assessment workflows for educators and enhances transparency for students. Built with modern web technologies, it provides a seamless interface for behavior tracking, academic performance analysis, file sharing, and comprehensive reporting.

## Key Features

- **Authentication** - Role-based access control with teacher and student portals
- **Dashboards** - Data-driven insights tailored to user roles
- **Course Management** - Create, modify, and organize courses
- **File Management** - Upload, categorize, and share educational materials
- **Student Progress Analytics** - Track attendance, participation, and performance
- **Behavioral Insights** - Monitor and analyze student behavioral patterns
- **Interactive Reporting** - Generate dynamic reports with customizable filters
- **Integrated Calendar** - Schedule classes, assignments, and events
- **Gamified Leaderboard** - Motivate students through achievement recognition
- **Real-time Notifications** - Keep users informed about updates and deadlines

## Tech Stack

### Frontend
- React 18 with TypeScript
- Tailwind CSS with responsive design
- Shadcn/UI for consistent UI elements
- React Context API and TanStack Query for state management
- React Router v6 for routing
- Recharts for data visualization

### Backend
- Supabase PostgreSQL database
- Supabase Auth for authentication
- Supabase Storage for file management
- RESTful API endpoints

## Database Schema

```mermaid
erDiagram
    STUDENTS {
        uuid id PK
        string name
        string email
        string roll_number
        string course
        integer semester
        integer attendance
        integer behavior_score
        string avatar_url
        integer academic_score
        integer participation_score
        integer leaderboard_points
        float cgpa
    }
    
    PERSONALITY_TRAITS {
        uuid id PK
        uuid student_id FK
        integer openness
        integer conscientiousness
        integer extraversion
        integer agreeableness
        integer neuroticism
    }
    
    BEHAVIORAL_INCIDENTS {
        uuid id PK
        uuid student_id FK
        date incident_date
        string type
        string description
        string severity
    }
    
    TEACHING_MATERIALS {
        uuid id PK
        string name
        string description
        string file_url
        string file_type
        integer file_size
        string course
        string uploaded_by
        boolean shared_with_all
        string shared_with_course
    }
    
    NOTIFICATIONS {
        uuid id PK
        string title
        string message
        string type
        string recipient_role
        string recipient_id
        uuid student_id
        boolean read
    }
    
    COURSE_CARDS {
        uuid id PK
        string title
        string description
        string instructor
        string subject
        string color
        string thumbnail_url
        string course
        string created_by
    }
    
    STUDENT_MATERIALS {
        uuid id PK
        uuid material_id FK
        uuid student_id FK
    }
    
    STUDENTS ||--o{ PERSONALITY_TRAITS : has
    STUDENTS ||--o{ BEHAVIORAL_INCIDENTS : records
    TEACHING_MATERIALS ||--o{ STUDENT_MATERIALS : assigned_to
    STUDENTS ||--o{ STUDENT_MATERIALS : accesses
    STUDENTS ||--o{ NOTIFICATIONS : receives
    COURSE_CARDS ||--o{ TEACHING_MATERIALS : contains
```

## Application Architecture

```mermaid
flowchart TD
    subgraph Client
        React[React Application]
        Router[React Router]
        Context[Context API]
        Query[TanStack Query]
        UI[Shadcn/UI Components]
    end
    
    subgraph Server
        Auth[Supabase Auth]
        Storage[Supabase Storage]
        DB[PostgreSQL Database]
        Functions[Database Functions]
    end
    
    React --> Router
    React --> Context
    React --> Query
    React --> UI
    
    Query --> Auth
    Query --> Storage
    Query --> DB
    
    Auth --> Functions
    Storage --> Functions
    DB --> Functions
```

## Data Flow

```mermaid
sequenceDiagram
    actor Teacher
    actor Student
    participant Auth as Authentication
    participant Dashboard as Dashboards
    participant Courses as Course Management
    participant Files as File Management
    participant Analytics as Analytics Engine
    participant DB as Database
    
    Teacher->>Auth: Login
    Auth->>Dashboard: Redirect to Teacher Dashboard
    Teacher->>Courses: Create/Modify Course
    Courses->>DB: Store Course Data
    Teacher->>Files: Upload Materials
    Files->>DB: Store File Metadata
    Files->>Storage: Store File Content
    
    Student->>Auth: Login
    Auth->>Dashboard: Redirect to Student Dashboard
    Student->>Courses: View Available Courses
    Courses->>DB: Fetch Course Data
    Student->>Files: Download Materials
    Files->>DB: Record Access
    Files->>Storage: Retrieve File
    
    Teacher->>Analytics: View Student Performance
    Analytics->>DB: Query Student Data
    DB->>Analytics: Return Performance Metrics
    Analytics->>Dashboard: Display Visual Reports
```

## Getting Started

### Prerequisites
- Node.js 16+ and npm/yarn/bun
- Supabase account and project

### Installation

1. Clone the repository
   ```bash
   git clone https://github.com/yourusername/student-behavior-tracking.git
   cd student-behavior-tracking
   ```

2. Install dependencies
   ```bash
   npm install
   ```

3. Set up environment variables
   ```
   VITE_SUPABASE_URL=your_supabase_url
   VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
   ```

4. Start the development server
   ```bash
   npm run dev
   ```

## Deployment

- **Build Command**: npm run build
- **Framework**: vite
- **Output Directory**: dist

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request
