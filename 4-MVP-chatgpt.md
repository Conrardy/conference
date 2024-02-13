
:prfocus
:prsln

```
given this context create an MVP. 

Problem : find a conference in a list and browse a single track of talks or workshops following a timeline.

Example :
Choose "Agile Tour Monpellier 2024" in the list of conference
Browse in "Grand hall" tracks and get "Keynote, 9:15 - 10:00", "How to use IA 10:10-10:55"

Describe step by step to create this MVP.
```

# MVP Development Plan for Event Management Platform

This document outlines the development plan for a Minimum Viable Product (MVP) of an event management platform. The MVP will enable users to find a conference from a list and browse a single track of talks or workshops following a timeline.

## Step 1: Define MVP Features

1. **Conference List Display**: Display a list of all available conferences.
2. **Conference Selection**: Allow users to select a conference (e.g., "Agile Tour Montpellier 2024").
3. **Tracks Display**: Show available tracks for the selected conference (e.g., "Grand Hall").
4. **Timeline View**: Display the timeline of talks or workshops for the selected track.

## Step 2: Choose Technology Stack

- **Frontend**: Angular and TailwindCSS.
- **Backend**: Firebase Firestore for data storage, Firebase Authentication for user management.
- **Deployment**: GitHub Actions for CI/CD, Vercel for hosting.

## Step 3: Set Up the Development Environment

1. **Initialize Angular Project**: Create a new project and integrate TailwindCSS.
2. **Firebase Project Setup**: Create a project, set up Firestore, and enable Authentication.

## Step 4: Develop the Application

### Frontend Development

- **Conference List Component**: Create a component to list conferences, fetching data from Firestore.
- **Track Selection Component**: Display tracks for a selected conference, fetching data from Firestore.
- **Timeline Component**: Show the timeline for a selected track, fetching session details from Firestore.

### Backend Development

- **Database Schema**:
    - Conferences collection with fields for name, date, location.
    - Tracks sub-collection with fields for track name.
    - Sessions sub-collection with fields for session title, start time, and end time.
- **Seed Database**: Populate Firestore with initial data, including "Agile Tour Montpellier 2024".

## Step 5: Implement Authentication (Optional)

- **User Authentication**: Use Firebase Authentication for sign-in functionality.

## Step 6: Testing

- **Unit Testing**: Write tests for Angular components and services.
- **Integration Testing**: Test frontend integration with Firebase.
- **User Acceptance Testing**: Manual testing based on user scenarios.

## Step 7: Deployment

1. **Configure GitHub Actions**: Set up workflows for automated testing and deployment.
2. **Deploy to Vercel**: Automate deployments through Vercel integration with GitHub.

## Step 8: Launch and Monitor

- **Launch the MVP**: Make the application publicly available.
- **Monitor and Collect Feedback**: Use analytics and feedback tools to improve the MVP.


