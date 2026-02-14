# Firebase Integration Guide

## 🚀 Setup Instructions

### 1. Create Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project"
3. Enter project name (e.g., "project-dashboard")
4. Enable Google Analytics (optional)
5. Click "Create project"

### 2. Enable Firestore Database
1. In Firebase Console, go to "Firestore Database"
2. Click "Create database"
3. Choose "Start in test mode"
4. Select a location (e.g., "asia-southeast1")

### 3. Get Firebase Configuration
1. Go to Project Settings → General
2. Scroll down to "Your apps" section
3. Click the web icon (</>)
4. Copy the Firebase configuration object

### 4. Update Firebase Configuration
Replace the placeholder values in `src/lib/firebase.ts`:

```typescript
const firebaseConfig = {
  apiKey: "YOUR_ACTUAL_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

### 5. Firestore Security Rules
Go to Firestore Database → Rules and update:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.time < timestamp.date(2025, 1, 1);
      // For production, use proper authentication rules
      // allow read, write: if request.auth != null;
    }
  }
}
```

## 🔧 Features Implemented

### ✅ Real-time Data Sync
- Automatic updates when projects are added/modified/deleted
- No need to refresh the page
- All connected users see changes instantly

### ✅ Firestore Database
- Projects stored in Firestore
- Automatic timestamps (createdAt, updatedAt)
- Query with ordering by creation date

### ✅ Error Handling
- Loading states
- Error messages
- Graceful fallbacks

### ✅ Type Safety
- TypeScript interfaces for Project and Note
- Type-safe database operations
- IntelliSense support

## 🎯 Usage

The dashboard now automatically:
1. **Loads projects from Firestore** on initial load
2. **Syncs in real-time** when data changes
3. **Persists data** across browser sessions
4. **Handles errors** gracefully

## 📱 Deployment

### Deploy to Vercel (Recommended)
1. Push code to GitHub
2. Connect Vercel to your repository
3. Add environment variables in Vercel dashboard:
   ```
   NEXT_PUBLIC_FIREBASE_API_KEY=your_api_key
   NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
   NEXT_PUBLIC_FIREBASE_PROJECT_ID=your_project_id
   NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
   NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
   NEXT_PUBLIC_FIREBASE_APP_ID=your_app_id
   ```

### Local Development
1. Create `.env.local` file:
   ```
   NEXT_PUBLIC_FIREBASE_API_KEY=your_api_key
   NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
   NEXT_PUBLIC_FIREBASE_PROJECT_ID=your_project_id
   NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
   NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
   NEXT_PUBLIC_FIREBASE_APP_ID=your_app_id
   ```

2. Update `src/lib/firebase.ts` to use environment variables:
   ```typescript
   const firebaseConfig = {
     apiKey: process.env.NEXT_PUBLIC_FIREBASE_API_KEY,
     authDomain: process.env.NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN,
     projectId: process.env.NEXT_PUBLIC_FIREBASE_PROJECT_ID,
     storageBucket: process.env.NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET,
     messagingSenderId: process.env.NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID,
     appId: process.env.NEXT_PUBLIC_FIREBASE_APP_ID
   };
   ```

## 🔒 Security Notes

- **Development**: Current rules allow all access (for testing)
- **Production**: Update security rules to require authentication
- **Environment Variables**: Never commit Firebase keys to Git
- **Data Validation**: Add validation on both client and server side

## 🚀 Next Steps

1. **Authentication**: Add user login/signup functionality
2. **User-specific Data**: Filter projects by user ID
3. **Offline Support**: Add local caching for offline usage
4. **File Upload**: Add file storage for project attachments
5. **Notifications**: Add real-time notifications for task updates
