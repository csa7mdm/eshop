# LLM Context for Audio Memes Platform

## 1. Project Overview
The Audio Memes Platform is a web and mobile application designed for creating, sharing, and discovering audio-based memes. The platform aims to provide a rich user experience with features for audio manipulation, social sharing, and content discovery.

## 2. Technical Stack

### Backend
- **Framework:** .NET 9
- **Architecture:** Clean Architecture principles
- **Key Libraries/Patterns:** Using xUnit for testing. MediatR for CQRS and Entity Framework Core for ORM are planned.
- **Database:** Database to be decided (e.g., PostgreSQL, SQL Server, SQLite for development).
- **Key Libraries/Patterns:** To be determined (e.g., MediatR for CQRS, Entity Framework Core for ORM, xUnit/NUnit for testing).
- **Database:** To be determined (e.g., PostgreSQL, SQL Server, MongoDB).
- **Deployment:** Docker, Kubernetes (target environment).

### Web Frontend
- **Framework:** React with Next.js
- **State Management:** To be determined (e.g., Redux Toolkit, Zustand, Context API).
- **Styling:** Scalable styling architecture (e.g., Tailwind CSS, CSS Modules, Styled Components).
- **Key Libraries:** To be determined (e.g., Axios for API calls, React Query/SWR for data fetching).

### Mobile App
- **Framework:** Flutter
- **State Management:** To be determined (e.g., Provider, BLoC/Cubit, Riverpod).
- **Key Packages:** To be determined (e.g., http for API calls, shared_preferences for local storage).

## 3. Design Principles
- **User-Centric Design:** Prioritize ease of use and an engaging user experience.
- **Scalability:** Design for growth in users and data.
- **Maintainability:** Write clean, well-documented, and testable code.
- **Modularity:** Develop independent modules for better separation of concerns.
- **Performance:** Optimize for fast load times and smooth interactions.
- **Security:** Implement security best practices throughout the development lifecycle.

## 3.1. Database Schema Design

The following initial schema has been designed for core entities:

### User Entity
- **Id**: `GUID` (Primary Key)
- **Username**: `string` (Unique, Indexed) - For login and display.
- **Email**: `string` (Unique, Indexed) - For communication and account recovery.
- **PasswordHash**: `string` - Hashed version of the user's password.
- **Salt**: `string` - Unique salt used in password hashing for this user.
- **CreatedAt**: `DateTime` (UTC) - Timestamp of user registration.
- **UpdatedAt**: `DateTime` (UTC) - Timestamp of the last profile update.

### MediaItem Entity
- **Id**: `GUID` (Primary Key)
- **UserId**: `GUID` (Foreign Key referencing User.Id, Indexed) - Links to the uploading user.
- **Title**: `string` (Optional) - User-defined title for the media.
- **Description**: `string` (Optional) - User-defined description.
- **FileUrl**: `string` - URL to the actual media file (e.g., in cloud storage).
- **ContentType**: `string` - MIME type of the file (e.g., "audio/mpeg", "audio/wav").
- **FileSize**: `long` (in bytes) - Size of the media file.
- **Duration**: `TimeSpan` - Length of the audio/video content.
- **UploadedAt**: `DateTime` (UTC) - Timestamp of when the file was successfully uploaded and processed.
- **CreatedAt**: `DateTime` (UTC) - Timestamp of entity creation.
- **UpdatedAt**: `DateTime` (UTC) - Timestamp of the last entity update.

### Relationships
- **User to MediaItems**: One-to-Many. A single user can upload multiple media items.

## 4. Known Issues & Edge Cases
- (To be populated as development progresses)
- Example: Audio processing might have limitations with very large files on low-spec devices.

## 5. FAQs for LLM
- **Q: What is the primary goal of the backend authentication service?**
  - A: To securely manage user registration, login, session management, and password recovery. It should support token-based authentication (e.g., JWT).
- **Q: How should feature flags be managed?**
  - A: Implement a feature-flag service. Flags should be short-lived, evaluated server-side where possible, have unique and descriptive names, and include clear rollback strategies.
- **Q: What are the key considerations for the mobile app's local caching strategy?**
  - A: Cache frequently accessed data like user profiles, recently viewed memes, and application settings to improve performance and reduce network requests. Consider cache expiration and invalidation strategies.
- (To be populated with more specific questions as needed)

## 6. Code Generation & Style Guide
- **General:** Follow standard coding conventions for each language/framework.
- **.NET (Backend):**
    - Use C# 12 features where appropriate (assuming .NET 9 defaults to C# 12 or allows its use).
    - Follow Microsoft's C# Coding Conventions.
    - Adhere to Clean Architecture principles (separation of concerns, dependency rule) - initial structure established.
    - Solution and projects created using .NET 9 SDK (net9.0 target framework).
    - Use C# 12 features where appropriate.
    - Follow Microsoft's C# Coding Conventions.
    - Adhere to Clean Architecture principles (separation of concerns, dependency rule).
- **React/Next.js (Frontend):**
    - Use functional components with Hooks.
    - Follow Airbnb JavaScript Style Guide (or a similar established guide).
    - Structure components logically.
- **Flutter (Mobile):**
    - Follow Effective Dart guidelines.
    - Organize widget code for readability and reusability.

## 7. Data Requirements & Third-Party Services
- **Media Storage:** Cloud storage (e.g., AWS S3, Azure Blob Storage, Google Cloud Storage).
- **Analytics:** Analytics platform (e.g., Google Analytics, Mixpanel).
- **Payment Gateway (if E-commerce):** (e.g., Stripe, PayPal).
- **API Keys:** (List any necessary API keys and how to obtain/configure them for local development).

## 8. Environment Setup
- **Backend:** .NET 9 SDK, Docker (optional for local DB).
- **Frontend:** Node.js (latest LTS), npm/yarn.
- **Mobile:** Flutter SDK, Android Studio/Xcode.
- (Provide links to detailed setup guides if available).
