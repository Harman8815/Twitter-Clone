# Frontend Documentation

This folder contains the frontend codebase for the **Twitter Clone** application. It is built using **React**, **Vite**, **TailwindCSS**, and **React Query** for state management and API interactions.

---

## Folder Structure

```
frontend/
├── .eslintrc.cjs       # ESLint configuration for linting React code
├── index.html          # Entry HTML file for the Vite app
├── package.json        # Project metadata and dependencies
├── postcss.config.js   # PostCSS configuration for TailwindCSS
├── README.md          # Documentation for the frontend folder
├── tailwind.config.js  # TailwindCSS configuration
├── vite.config.js      # Vite configuration for development and build
├── public/            # Static assets served directly
├── src/               # Source code for the React application
│   ├── App.jsx        # Main application component
│   ├── main.jsx       # Entry point for React application
│   ├── index.css      # Global CSS styles using TailwindCSS
│   ├── components/    # Reusable UI components
│   │   ├── common/    # Common components like Sidebar, Post, etc.
│   │   ├── skeletons/ # Skeleton loaders for better UX
│   ├── hooks/         # Custom React hooks
│   ├── pages/         # Page components for routing
│   │   ├── auth/      # Authentication-related pages (Login, Signup)
│   │   ├── home/      # Home page
│   │   ├── notification/ # Notification page
│   │   ├── profile/   # Profile page and related components
│   ├── utils/         # Utility functions (date formatting, dummy data)
```

---

## File and Folder Descriptions

### **Root Files**

- **`.eslintrc.cjs`**: Configures ESLint for linting React code with recommended rules and React-specific plugins.
- **`index.html`**: The entry HTML file for the Vite app. It includes the root `div` where the React app is mounted.
- **`package.json`**: Contains project metadata, dependencies, and scripts for development, build, and linting.
- **`postcss.config.js`**: Configures PostCSS to use TailwindCSS for styling.
- **`README.md`**: Documentation for the frontend folder.
- **`tailwind.config.js`**: TailwindCSS configuration, including custom themes and dark mode settings.
- **`vite.config.js`**: Vite configuration for the development server and proxying API requests.

### **`public/`**
Contains static assets like images, icons, and other files that are served directly without processing.

### **`src/`** (Main Source Code)

#### **`App.jsx`**
Defines the routes for the app and handles the loading state for the authenticated user.

#### **`main.jsx`**
The entry point for the React application. It sets up the React Query client, React Router, and renders the `App` component.

#### **`index.css`**
Global CSS styles using TailwindCSS, including base, components, and utilities from Tailwind.

#### **`components/`** (Reusable UI Components)
- **`common/`**: Contains shared components like `Sidebar`, `Post`, `RightPanel`, and `LoadingSpinner`.
- **`skeletons/`**: Contains skeleton loaders for better user experience during data loading.

#### **`hooks/`** (Custom React Hooks)
Encapsulates reusable logic, such as `useFollow` and `useUpdateUserProfile`.

#### **`pages/`** (Page Components)
- **`auth/`**: Contains `LoginPage` and `SignUpPage` for user authentication.
- **`home/`**: Contains the `HomePage` component, which displays the main feed.
- **`notification/`**: Contains the `NotificationPage` component for user notifications.
- **`profile/`**: Contains the `ProfilePage` component and related components like `EditProfileModal`.

#### **`utils/`** (Utility Functions and Constants)
- **`date.js`**: Functions for formatting dates.
- **`dummy.js`**: Contains dummy data for testing and development.

---

## How It Works

1. **Development**: Run `npm run dev` to start the Vite development server. The app will be available at `http://localhost:3000`.
2. **Build**: Run `npm run build` to create a production build in the `dist/` folder.
3. **Proxying API Requests**: The Vite server proxies API requests starting with `/api` to the backend server running on `http://localhost:5000`.

---

## **Project Structure Visualization (Mermaid.js)**

![alt text](../Screenshot/image.png)

