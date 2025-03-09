# UC Transfer Chance Me

A fullstack web application to help prospective UC transfer students estimate their chances of admission based on academic profile, extracurriculars, and other key factors.

## Project Overview

This application uses data from the UC Transfer by Major website, including 25th and 75th percentile GPA ranges for admitted students by major, as well as insights from the Common Data Set to provide personalized admission probability estimates.

## Tech Stack

- **Frontend**: React.js, Next.js, Tailwind CSS
- **Backend**: Express.js, Node.js
- **Database**: MongoDB
- **Deployment**: Vercel

## Project Approach

### 1. Project Planning & Requirements Analysis

#### Define Core Functionality

- User input collection for: GPA, major selection, UC campus selection, completed coursework, extracurricular details, and essay self-assessment
- Algorithm to calculate admission chances based on multiple factors
- Detailed results with personalized recommendations

#### Data Requirements

- UC Transfer by Major GPA percentile data (25th and 75th percentiles)
- Major-specific required and recommended coursework
- Importance weightings for different admission factors
- User account information (if implementing save functionality)

### 2. System Architecture

#### Frontend (React.js, Next.js, Tailwind CSS)

- Server-side rendering with Next.js for better SEO and initial load performance
- Responsive design system using Tailwind CSS
- State management with React Context API or Redux
- Form validation with libraries like Formik or React Hook Form

#### Backend (Express.js, Node.js)

- RESTful API endpoints for data submission and retrieval
- Authentication middleware for user accounts
- Data processing logic for admission chance calculation
- Caching layer for frequently accessed data

#### Database (MongoDB)

Collections for:

- UC admission statistics (GPA ranges by campus and major)
- Course articulation requirements
- User profiles and saved assessments
- Extracurricular activity weightings

#### Deployment (Vercel)

- Continuous integration/deployment pipeline
- Environment configuration for development/production
- API route handling through Vercel serverless functions

### 3. Data Acquisition Strategy

#### UC Transfer Statistics Collection

- Web scraping script to extract data from UC Transfer by Major website
- Data normalization and storage in MongoDB
- Regular update mechanism to keep data current

#### Articulation Requirements

- Compile required and recommended coursework for each UC campus and major
- Create database schema to store this information efficiently
- Implement rules for evaluating course completion impact

### 4. Frontend Implementation

#### Page Structure

##### Landing Page

- App introduction and value proposition
- Call-to-action to begin assessment

##### Multi-step Form

- Step 1: Basic information (selecting UC campus and major)
- Step 2: Academic details (GPA and completed coursework)
- Step 3: Extracurricular activities (with categories and impact ratings)
- Step 4: Essays and personal statement self-assessment

##### Results Dashboard

- Overall admission chance percentage
- Breakdown of factors contributing to the result
- Visual representations (charts/graphs) of standing
- Personalized improvement recommendations

#### UI Components

- Custom form elements (sliders, toggles, multi-selects)
- Progress indicator for multi-step form
- Interactive visualization components for results
- Mobile-responsive layout

### 5. Algorithm Development

#### Admission Chance Calculation

##### GPA Component:

- Calculate percentile standing relative to 25th/75th percentile data
- Weight more heavily for majors where GPA is a stronger predictor

##### Coursework Component:

- Score based on percentage of required courses completed
- Bonus points for recommended courses
- Major-specific weighting

##### Extracurricular Component:

- Scoring system based on leadership roles, duration, and relevance
- Different weights for different types of activities

##### Essay Component:

- Self-assessment scores with calibrated weighting
- Consider providing examples of what constitutes different quality levels

#### Factor Integration

- Weighted average of all components with customized weights by campus
- Confidence interval calculation to show range of possible outcomes
- Normalization against historical admission rates

### 6. Backend Implementation

#### API Endpoints

- `/api/campuses` - List available UC campuses
- `/api/majors/:campusId` - List majors for a specific campus
- `/api/statistics/:campusId/:majorId` - Get admission statistics
- `/api/calculate` - Submit user data and receive chance calculation
- `/api/user/*` - User account management (if implementing)

#### Server-side Logic

- Input validation and sanitization
- Data aggregation from multiple collections
- Algorithm execution for chance calculation
- Result formatting and recommendation generation

### 7. Database Design

#### Collections Schema

- **Campuses**: Information about each UC campus
- **Majors**: Major details with campus relationships
- **AdmissionStats**: GPA percentiles and other statistics by campus/major
- **CourseArticulations**: Required and recommended courses
- **Users**: User profiles and saved assessments (if implementing)

#### Data Relationships

- One-to-many relationship between campuses and majors
- One-to-one relationship between major+campus combinations and admission statistics
- Many-to-many relationship between majors and course articulations

### 8. Testing Strategy

- Unit tests for calculation algorithm components
- Integration tests for API endpoints
- UI component tests with React Testing Library
- End-to-end tests for complete user flows
- Performance testing for database queries and API response times

### 9. Feature Enhancements (Post-MVP)

- User accounts to save and track multiple assessments
- Comparison tool to evaluate chances across different UC campuses
- Historical tracking to show improvement over time
- Community insights from successful transfer students
- Timeline generator for application milestones

### 10. Project Timeline

- Week 1-2: Requirements gathering and system design
- Week 3-4: Data acquisition and database setup
- Week 5-6: Core backend implementation
- Week 7-9: Frontend development and integration
- Week 10-11: Testing and refinement
- Week 12: Deployment and launch

### 11. Development Workflow

- Set up project repositories with proper structure
- Implement database models and seed initial data
- Develop core API endpoints for data retrieval
- Build calculation algorithm and test with sample data
- Create frontend components and forms
- Implement client-side state management
- Connect frontend to backend services
- Add authentication if implementing user accounts
- Conduct thorough testing across devices
- Deploy to Vercel and monitor performance
