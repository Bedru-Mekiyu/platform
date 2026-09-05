# Evently — Modern Event Management & Ticketing Platform

Evently is a full-stack event management and ticketing web application built with **Next.js 14**, **React**, **TypeScript**, **Tailwind CSS**, **MongoDB**, **Clerk**, and **Stripe**. It allows users to discover, create, update, manage, and purchase tickets for events around the globe.

---

## Key Features

- **User Authentication & Profiles**: Secure sign-in, sign-up, and session management powered by Clerk, synchronized to MongoDB via Webhooks.
- **Event Management (CRUD)**: Create, view, update, and delete events with rich details, images, scheduling, pricing, and category tagging.
- **File Uploads**: Drag-and-drop event banner uploading using UploadThing.
- **Search & Filtering**: Real-time event search by title and category filtering with URL query state persistence.
- **Stripe Payments**: Checkout flow powered by Stripe for paid event ticketing and order confirmation via webhooks.
- **Order & Ticket Tracking**: Dedicated dashboard for users to view purchased tickets and event organizers to view order histories.
- **Responsive UI**: Fully responsive interface crafted with Tailwind CSS and accessible Radix UI primitives (Shadcn UI).

---

## Tech Stack

| Domain | Technology |
| --- | --- |
| **Framework** | [Next.js 14](https://nextjs.org/) (App Router & Server Actions) |
| **Language** | [TypeScript](https://www.typescriptlang.org/) |
| **Styling** | [Tailwind CSS](https://tailwindcss.com/) & [Shadcn UI](https://ui.shadcn.com/) |
| **Database** | [MongoDB](https://www.mongodb.com/) & [Mongoose ORM](https://mongoosejs.com/) |
| **Authentication** | [Clerk](https://clerk.com/) |
| **Payments** | [Stripe](https://stripe.com/) |
| **Media Storage** | [UploadThing](https://uploadthing.com/) |
| **Forms & Validation** | React Hook Form & [Zod](https://zod.dev/) |

---

## Project Structure

```text
.
├── app/
│   ├── (auth)/             # Clerk authentication routes (sign-in, sign-up)
│   ├── (root)/             # Main application layout & pages
│   │   ├── events/         # Event details, creation, and modification pages
│   │   ├── orders/         # Event orders table and details
│   │   ├── profile/        # User profile and purchased ticket dashboard
│   │   └── page.tsx        # Homepage with hero section, search & filtering
│   └── api/                # API routes and webhooks (Clerk, Stripe, UploadThing)
├── components/
│   ├── shared/             # Reusable UI components (Header, Footer, Cards, Forms, Search)
│   └── ui/                 # Shadcn Radix UI primitives
├── constants/              # Application default constants
├── lib/
│   ├── actions/            # Server actions for events, categories, orders, users
│   ├── database/           # Database connection utility and Mongoose models
│   ├── validator.ts        # Zod form validation schemas
│   └── utils.ts            # Formatting, error handling, and query string helpers
├── public/                 # Static assets and icons
├── types/                  # TypeScript interface definitions
└── middleware.ts           # Clerk route protection middleware
```

---

## Getting Started

### Prerequisites

Ensure you have the following installed on your machine:
- **Node.js**: v18.x or v20.x
- **npm**: v9.x or later
- A **MongoDB** cluster database URI
- API credentials for **Clerk**, **Stripe**, and **UploadThing**

### Installation

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd evently
   ```

2. **Install dependencies**:
   ```bash
   npm ci
   ```

3. **Configure Environment Variables**:
   Copy `.env.example` to `.env.local` and populate the required keys:
   ```bash
   cp .env.example .env.local
   ```

4. **Run the local development server**:
   ```bash
   npm run dev
   ```
   Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## Environment Variables

Refer to `.env.example` for the complete list of required environment variables:

| Variable Name | Description |
| --- | --- |
| `NEXT_PUBLIC_SERVER_URL` | Base URL of the application (e.g. `http://localhost:3000`) |
| `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY` | Public API key from Clerk Dashboard |
| `CLERK_SECRET_KEY` | Secret API key from Clerk Dashboard |
| `WEBHOOK_SECRET` | Secret for verifying Clerk user sync webhooks |
| `MONGODB_URI` | MongoDB connection string |
| `UPLOADTHING_SECRET` | Secret key for UploadThing file uploads |
| `UPLOADTHING_APP_ID` | Application ID for UploadThing |
| `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY` | Publishable key for Stripe Checkout |
| `STRIPE_SECRET_KEY` | Secret key for Stripe payment processing |
| `STRIPE_WEBHOOK_SECRET` | Webhook signing secret for Stripe checkout events |

---

## Scripts

- `npm run dev`: Starts the Next.js development server with hot-reloading.
- `npm run build`: Compiles and builds the production application.
- `npm run start`: Starts the Next.js production server.
- `npm run lint`: Executes Next.js ESLint verification.
- `npx tsc --noEmit`: Performs TypeScript static type checking.

---

## Continuous Integration

Automated CI/CD is configured via **GitHub Actions** (`.github/workflows/ci.yml`). On every push and pull request to the main branch, the pipeline automatically:
1. Installs project dependencies (`npm ci`).
2. Runs ESLint quality checks (`npm run lint`).
3. Validates TypeScript types (`npx tsc --noEmit`).
4. Executes production build (`npm run build`).

---

## License

This project is open-source and available under the MIT License.
