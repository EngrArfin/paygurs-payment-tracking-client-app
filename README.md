# PayGuard – Payment Tracking and Verification System

## Overview

PayGuard is a secure Payment Management and Verification System designed for role-based user authentication, payment request creation, document uploads, and administrative approval workflows. This system supports responsive UI and is fully deployed for online access.

---

## Features

### User Authentication

- Signup, Login, and Logout using Supabase Auth with email/password.
- Role-based access control (Admin and User).

### Payment Management

#### User Features:

- Create payment requests with Title, Amount, and Status.
- Track payment statuses (Pending, Approved, Rejected).

#### Admin Features:

- View all payments submitted by users.
- Approve or reject payment requests and update their statuses.

### Document Upload for Verification

- Users can upload identity verification documents (PDF/JPG/PNG, max size: 5 MB).
- Admin reviews uploaded documents and updates the verification status (Pending, Approved, Rejected).

### Admin Dashboard

- Displays a summary of total payments with status-based breakdowns.
- Includes filters for managing payments by date and status.

### Additional Features (Optional Enhancements)

- Payment Gateway Integration (Stripe/PayPal Sandbox).
- Email notifications for status changes.
- PDF invoice generation for completed payments.
- Admin analytics (charts for payments and status summaries).

---

## Technical Stack

- **Frontend**: React.js, Tailwind CSS, TypeScript
- **Backend**: Next.js API Routes
- **Database**: PostgreSQL / MongoDB
- **Storage**: Supabase Storage for file uploads
- **Deployment**: Vercel

---

## Getting Started

### Prerequisites

- Node.js (>= 18.x)
- PostgreSQL or MongoDB database
- Supabase account
- Stripe or PayPal Sandbox account (optional for payment gateway)

### Environment Variables

Create a `.env.local` file in the root directory and add the following:

```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE=your_supabase_service_role
DATABASE_URL=your_database_connection_url
NEXT_PUBLIC_STRIPE_PUBLIC_KEY=your_stripe_public_key (optional)
STRIPE_SECRET_KEY=your_stripe_secret_key (optional)
```

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/payguard.git
   cd payguard
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Run the development server:

   ```bash
   npm run dev
   ```

4. Access the application at `http://localhost:3000`.

---

## API Details

### Authentication APIs

- **POST** `/api/auth/signup`: User signup
- **POST** `/api/auth/login`: User login
- **POST** `/api/auth/logout`: User logout

### Payment APIs

- **POST** `/api/payments`: Create a payment request
- **GET** `/api/payments`: Retrieve payment requests (admin or user-specific)
- **PUT** `/api/payments/:id`: Update payment status

### Document Upload APIs

- **POST** `/api/documents`: Upload documents
- **GET** `/api/documents`: Fetch uploaded documents
- **PUT** `/api/documents/:id`: Update document verification status

---

## Database Schema

### Users Table

| Column     | Type      | Details                    |
| ---------- | --------- | -------------------------- |
| id         | UUID      | Primary Key                |
| email      | VARCHAR   | Unique                     |
| password   | HASHED    | Encrypted                  |
| role       | VARCHAR   | 'admin' or 'user'          |
| created_at | TIMESTAMP | Timestamp of user creation |

### Payments Table

| Column     | Type      | Details                       |
| ---------- | --------- | ----------------------------- |
| id         | UUID      | Primary Key                   |
| title      | VARCHAR   | Payment title                 |
| amount     | NUMERIC   | Payment amount                |
| status     | VARCHAR   | Default: 'pending'            |
| user_id    | UUID      | Foreign Key (Users table)     |
| created_at | TIMESTAMP | Timestamp of payment creation |

### Documents Table

| Column      | Type      | Details                   |
| ----------- | --------- | ------------------------- |
| id          | UUID      | Primary Key               |
| user_id     | UUID      | Foreign Key (Users table) |
| file_url    | TEXT      | Document storage URL      |
| status      | VARCHAR   | Default: 'pending'        |
| uploaded_at | TIMESTAMP | Timestamp of upload       |

---

## Deployment

1. Build the application:

   ```bash
   npm run build
   ```

2. Deploy to Vercel:

   - Push the code to a GitHub repository.
   - Link the repository to your Vercel account and deploy.

3. Provide the live URL in the submission.

---

## Test Credentials

### Admin Login:

- **Email**: admin@test.com
- **Password**: admin123

### User Login:

- **Email**: user@test.com
- **Password**: user123

---

## Project Submission

1. **Source Code Repository**: Share the GitHub repository link.
2. **Live Application URL**: Hosted project on Vercel or Netlify.
3. **Admin Credentials**: Provide admin login details.
4. **README File**: Include setup instructions, API details, and test credentials.
