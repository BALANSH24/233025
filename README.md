# Campus Notifications Microservice - Stage 1 & 2 Implementation

## Overview
A responsive React application for displaying campus notifications with priority sorting and modern Material UI design.

## 🎯 Features Implemented

### Stage 1: Priority Notification Algorithm
- **File**: `priority.js`
- **Algorithm**: 
  - Sorts notifications by weight (Placement: 3, Result: 2, Event: 1)
  - Secondary sort by timestamp (newest first)
  - Displays top 10 notifications
  - Uses Bearer token authentication for API access

### Stage 2: React Frontend Application
- **Framework**: React 19.2.5 + Vite
- **Styling**: Material UI (MUI)
- **Routing**: React Router for multi-page navigation
- **Storage**: LocalStorage for tracking viewed notifications

## 🔐 Authentication
- **Method**: Bearer Token in Authorization header
- **Token**: Configured in `.env` file for security
- **Implementation**: Centralized API utility (`src/utils/apiService.js`)

## 📁 Project Structure

```
placement/
├── .env                          # API configuration with token
├── vite.config.js               # Vite config (port 3000)
├── priority.js                  # Priority algorithm with auth
├── package.json                 # Dependencies
├── index.html                   # Entry point
├── src/
│   ├── App.jsx                 # Main app with routing & theme
│   ├── main.jsx                # React DOM entry
│   ├── components/
│   │   ├── AllNotifications.jsx    # All notifications page
│   │   └── PriorityNotifications.jsx # Priority inbox page
│   └── utils/
│       └── apiService.js        # API utility with auth
```

## 🚀 Code Optimizations

### 1. **API Service Utility** (`apiService.js`)
```javascript
- Centralized API handling
- Bearer token authentication
- Error handling and response validation
- Query parameter management
```

### 2. **State Management**
- React hooks (useState, useEffect) for clean state
- LocalStorage for persistent view tracking
- Loading and error states for better UX

### 3. **Performance**
- Efficient re-rendering with proper dependency arrays
- Memoized sorting functions
- Lazy component loading via React Router
- Image optimization with Avatar components

### 4. **UX Improvements**
- Loading spinners during data fetch
- Error alerts for failed requests
- Empty state messages
- Smooth hover animations (scale 1.02)
- Responsive grid layout (xs: 12, sm: 6, md: 4)
- Helper text for form inputs

### 5. **Accessibility**
- Semantic HTML with Material UI
- Color-coded notification types with icons
- Clear visual feedback for viewed notifications
- Keyboard navigation support via MUI

## 🎨 UI Features

### Modern Design
- **App Bar**: Navigation header with brand name
- **Cards**: Hover effects, shadows, rounded borders
- **Icons**: Material icons for notification types
- **Avatars**: Colored badges with icons
- **Chips**: Type badges with color coding
- **Filters**: Dropdown for filtering by type
- **Alerts**: Error and info messages
- **Loading**: Centered loading spinner

### Responsive Design
- **Mobile (xs)**: Full width cards (12 cols)
- **Tablet (sm)**: 2 cards per row (6 cols)
- **Desktop (md)**: 3 cards per row (4 cols)

## 📱 Pages

### 1. **All Notifications**
- Displays all notifications with pagination
- Filter by type (Placement, Result, Event)
- Click to mark as viewed
- Shows error and loading states

### 2. **Priority Inbox** 
- Displays top N priority notifications
- Adjustable N value (1-50)
- Ranks by priority with numbered badges
- Shows error and loading states

## 🔄 Data Flow

```
API (with Bearer Token)
    ↓
apiService.js (fetchNotificationsAPI)
    ↓
Component (AllNotifications/PriorityNotifications)
    ↓
State (notifications, loading, error)
    ↓
UI Rendering
```

## 🛠️ Technologies Used

| Tech | Purpose |
|------|---------|
| React 19 | UI Framework |
| Vite 8 | Build tool & dev server |
| React Router | Page routing |
| Material UI | Component library & styling |
| Material Icons | Icon set |
| Emotion | CSS-in-JS for MUI |

## ⚙️ Configuration Files

### `.env`
```
VITE_API_URL=http://20.207.122.201/evaluation-service/notifications
VITE_API_TOKEN=<YOUR_BEARER_TOKEN>
```

### `vite.config.js`
```javascript
export default defineConfig({
  plugins: [react()],
  server: {
    port: 3000
  }
})
```

## 📊 API Integration

### Endpoint
```
GET http://20.207.122.201/evaluation-service/notifications
Header: Authorization: Bearer <TOKEN>
Params: ?page=1&limit=10&notification_type=Placement
```

### Response Structure
```json
{
  "notifications": [
    {
      "ID": "uuid",
      "Type": "Placement|Result|Event",
      "Message": "string",
      "Timestamp": "YYYY-MM-DD HH:mm:ss"
    }
  ]
}
```

## 🚀 Running the App

### Development
```bash
npm install
npm run dev
# App runs on http://localhost:3000
```

### Build
```bash
npm run build
```

### Priority Script
```bash
node priority.js
# Displays top 10 priority notifications in console
```

## 📝 Key Improvements Made

1. ✅ **Authentication**: Added Bearer token support
2. ✅ **Error Handling**: Comprehensive error messages and UI
3. ✅ **Loading States**: Spinners and placeholders
4. ✅ **Responsiveness**: Mobile, tablet, desktop layouts
5. ✅ **Modern UI**: Material Design with icons and animations
6. ✅ **Code Quality**: Modular components, utility functions
7. ✅ **UX**: Viewed state tracking, filters, priority ranking
8. ✅ **Performance**: Optimized rendering, efficient state
9. ✅ **Accessibility**: Semantic HTML, ARIA labels, keyboard nav

## ⚠️ Current Status

**Frontend**: ✅ Fully functional and responsive
- App running on http://localhost:3001 (port 3000 was in use)
- All pages working
- Error handling displaying correctly
- UI is modern and responsive

**API Authentication**: ⚠️ 401 Unauthorized Error
- API is returning 401 status
- Possible causes:
  - Token might be expired (check token expiration: `exp` field)
  - Token audience mismatch (token audience vs API host)
  - API endpoint might require different authentication
  - CORS issues

**Solution**: 
Please verify and provide:
1. A fresh/valid authentication token
2. Correct API endpoint URL
3. Any additional authentication requirements

## 📦 Dependencies

```json
{
  "dependencies": {
    "react": "^19.2.5",
    "react-dom": "^19.2.5",
    "react-router-dom": "^latest",
    "@mui/material": "^latest",
    "@mui/icons-material": "^latest",
    "@emotion/react": "^latest",
    "@emotion/styled": "^latest"
  },
  "devDependencies": {
    "vite": "^8.0.10",
    "@vitejs/plugin-react": "^6.0.1",
    "eslint": "^10.2.1"
  }
}
```

---

**Status**: Ready for API authentication fix and deployment
