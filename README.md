# Next.js Contact Form with Server Actions

A full-stack contact form built with Next.js Server Actions and MongoDB — no API routes needed.

## Features

- Form submission using Next.js Server Actions (no API routes)
- MongoDB database integration with Mongoose
- Contact status management (new, read, replied)
- Cached contact statistics with `unstable_cache`
- Cache revalidation with `revalidateTag`
- Auto redirect to contacts page after successful submission
- Responsive UI with Shadcn UI components

## Tech Stack

- **Next.js 15** — App Router, Server Actions
- **MongoDB** — Database
- **Mongoose** — ODM for MongoDB
- **Shadcn UI** — UI component library (Radix + Neutral)
- **Tailwind CSS** — Styling

## Getting Started

### Prerequisites

- Node.js 18+
- MongoDB installed and running locally

### Installation

1. Clone the repo
```bash
   git clone https://github.com/rifaz07/nextjs-contact-form.git
   cd nextjs-contact-form
```

2. Install dependencies
```bash
   npm install
```

3. Create a `.env.local` file in the root
```
   MONGODB_URL=mongodb://localhost:27017/contact-form-demo
```

4. Run the development server
```bash
   npm run dev
```

5. Open [http://localhost:3000](http://localhost:3000)

## Project Structure
```
├── actions/
│   └── index.js         # Server Actions (createContact, getContacts, updateContact, getContactStats)
├── app/
│   ├── page.js          # Home page with contact form
│   └── contacts/        # Contacts admin page
├── components/
│   └── contact-form.jsx # Contact form component
├── lib/
│   └── db.js            # MongoDB connection
├── models/
│   └── contact.js       # Mongoose Contact model
```

## How It Works

1. User fills out the contact form (name, email, subject, message)
2. On submit, a Next.js Server Action receives the FormData directly
3. Data is validated and saved to MongoDB
4. User is automatically redirected to `/contacts`
5. Admin can view all contacts and update their status (new → read → replied)
6. Contact stats are cached using `unstable_cache` and revalidated on every status update

## Key Concepts Demonstrated

- **Server Actions** — runs server-side code directly from form submissions without API routes
- **FormData** — native browser API used to collect and send form field values
- **unstable_cache** — Next.js caching for expensive DB queries
- **revalidateTag** — invalidates specific cache entries after data mutations
- **useRouter** — programmatic navigation after form submission
