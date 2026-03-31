# LakshAI - AI-Powered Career Coach

LakshAI is a full-stack web application that provides AI-powered career guidance, resume building, cover letter generation, and interview preparation. Built with **Next.js 16**, **React 19**, **TypeScript-free JS**, **Prisma ORM**, **PostgreSQL**, and **Google's Gemini AI**.

![LakshAI Banner](/public/banner.png)

---

## ✨ Features

### 🧠 AI-Powered Career Guidance
- Personalized career advice and insights powered by Google's Gemini 2.5 Flash AI
- Industry-specific recommendations based on your profile

### 📄 Smart Resume Creation
- Build ATS-optimized resumes with AI assistance
- Markdown-based editor with live preview
- AI-powered content improvement for resume sections
- Export resumes as PDF

### 📝 AI Cover Letter Generator
- Generate tailored cover letters based on job descriptions
- Customize by company name, job title, and job description
- Save and manage multiple cover letters

### 🎤 Interview Preparation
- AI-generated technical interview quizzes tailored to your industry and skills
- Multiple-choice questions with 4 options and detailed explanations
- Track performance over time with analytics and charts
- Get AI-generated improvement tips based on wrong answers

### 📊 Industry Insights Dashboard
- Real-time industry trends, salary data, and market analysis
- Covers 50+ industries with 10+ sub-industries each
- Salary ranges by role, growth rates, demand levels
- Top skills and recommended learning paths
- Market outlook (Positive/Neutral/Negative)

### 📈 Progress Tracking
- Visualize interview quiz performance over time
- View assessment history with detailed question breakdowns
- Track improvement with AI-generated tips

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| **Framework** | Next.js 16 (App Router) |
| **Language** | JavaScript (JSX) |
| **UI Library** | React 19 |
| **Styling** | Tailwind CSS, shadcn/ui |
| **Database** | PostgreSQL |
| **ORM** | Prisma |
| **Authentication** | Clerk |
| **AI** | Google Generative AI (Gemini 2.5 Flash) |
| **Background Jobs** | Inngest |
| **Charts** | Recharts |
| **Forms** | React Hook Form + Zod |
| **PDF Export** | html2pdf.js |
| **Markdown** | React Markdown, @uiw/react-md-editor |
| **Notifications** | Sonner |
| **Icons** | Lucide React |

---

## 📁 Project Structure

```
LakshAI/
├── app/
│   ├── (main)/                    # Protected app routes
│   │   ├── dashboard/             # Industry insights dashboard
│   │   ├── resume/                # Resume builder
│   │   ├── interview/             # Interview prep & quizzes
│   │   ├── ai-cover-letter/       # Cover letter generator
│   │   ├── onboarding/            # User onboarding flow
│   │   └── layout.jsx             # Main app layout
│   ├── (auth)/                    # Auth routes (Clerk)
│   ├── api/                       # API routes
│   ├── lib/                       # Utility functions
│   ├── page.js                    # Landing page
│   ├── layout.js                  # Root layout
│   └── globals.css                # Global styles
├── actions/                       # Server actions
│   ├── resume.js                  # Resume CRUD + AI improvement
│   ├── cover-letter.js            # Cover letter generation & management
│   ├── interview.js               # Quiz generation & assessment
│   ├── dashboard.js               # Industry insights
│   └── user.js                    # User profile updates
├── components/
│   ├── ui/                        # shadcn/ui components
│   ├── header.jsx                 # Navigation header
│   ├── hero.jsx                   # Hero section
│   └── theme-provider.jsx         # Dark/light theme
├── data/                          # Static data files
│   ├── features.js                # Feature cards data
│   ├── howItWorks.js              # How it works steps
│   ├── industries.js              # 15 industries with sub-industries
│   ├── faqs.js                    # FAQ data
│   └── testimonial.js             # User testimonials
├── lib/
│   ├── prisma.js                  # Prisma client singleton
│   ├── checkUser.js               # User sync with Clerk
│   ├── utils.js                   # Utility functions
│   └── inngest/                   # Background job setup
│       ├── client.js              # Inngest client
│       └── function.js            # Cron job for industry insights
├── prisma/
│   ├── schema.prisma              # Database schema
│   └── migrations/                # Database migrations
├── public/                        # Static assets
├── middleware.js                  # Clerk auth middleware
├── next.config.mjs                # Next.js config
├── tailwind.config.mjs            # Tailwind config
├── package.json                   # Dependencies
└── README.md
```

---

## 🗄️ Database Schema

The application uses the following Prisma models:

- **User** — Stores user profile (Clerk ID, email, name, industry, bio, experience, skills)
- **IndustryInsight** — Cached AI-generated industry data (salary ranges, trends, skills, outlook)
- **Assessment** — Records of interview quiz attempts with questions and scores
- **Resume** — User's resume content in Markdown format with ATS score
- **CoverLetter** — Generated cover letters linked to specific job applications

---

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ 
- PostgreSQL database
- npm or pnpm

### Environment Variables

Create a `.env` file in the root directory with the following variables:

```env
# Database
DATABASE_URL="postgresql://username:password@localhost:5432/lakshai?schema=public"

# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_your_key
CLERK_SECRET_KEY=sk_test_your_key
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/

# Google Gemini AI
GEMINI_API_KEY=your_gemini_api_key

# Inngest (Background Jobs)
INNGEST_EVENT_KEY=your_inngest_event_key
INNGEST_SIGNING_KEY=your_inngest_signing_key
```

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Verma-Himanshu-22/LakshAI.git
   cd LakshAI
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```
   This will also run `prisma generate` automatically via the `postinstall` script.

3. **Set up the database**
   ```bash
   npx prisma migrate dev --name init
   ```

4. **Start the development server**
   ```bash
   npm run dev
   ```

5. **Open your browser**
   Navigate to [http://localhost:3000](http://localhost:3000)

---

## 📋 Available Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server (with Turbopack) |
| `npm run build` | Build for production |
| `npm run start` | Start production server |
| `npm run lint` | Run ESLint |
| `npx prisma migrate dev` | Create and apply a migration |
| `npx prisma generate` | Generate Prisma Client |
| `npx prisma studio` | Open Prisma Studio (database GUI) |

---

## 🔑 Key Features Implementation

### Authentication
- Powered by **Clerk** for secure user authentication
- Middleware protects all routes under `/dashboard`, `/resume`, `/interview`, `/ai-cover-letter`, `/onboarding`
- Automatic user creation in the database on first login via `checkUser()`

### AI Integration
- Uses **Google Gemini 2.5 Flash** model for all AI operations
- Server actions handle AI prompts for:
  - Resume content improvement
  - Cover letter generation
  - Interview quiz generation
  - Industry insights generation
  - Improvement tips based on quiz performance

### Background Jobs
- **Inngest** handles scheduled tasks
- Cron job runs every Sunday at midnight to refresh industry insights for all tracked industries

### UI/UX
- **Dark/Light theme** support with `next-themes`
- **shadcn/ui** components for consistent, accessible UI
- **Responsive design** with Tailwind CSS
- **Toast notifications** with Sonner
- **3D hero image** with scroll reveal and hover glow effects
- **Grid background** with radial gradient overlay

---

## 🌐 Industries Covered

The platform supports 15 major industries, each with 10+ sub-industries:

- Technology (Software, AI/ML, Cybersecurity, Cloud, etc.)
- Financial Services (Banking, FinTech, Investment, etc.)
- Healthcare & Life Sciences (Biotech, Pharma, Telemedicine, etc.)
- Manufacturing & Industrial (Automotive, Aerospace, 3D Printing, etc.)
- Retail & E-commerce (Fashion, D2C, Consumer Electronics, etc.)
- Media & Entertainment (Gaming, Streaming, Social Media, etc.)
- Education & Training (EdTech, Online Learning, Corporate Training, etc.)
- Energy & Utilities (Renewable, Clean Tech, Oil & Gas, etc.)
- Professional Services (Consulting, Legal, HR, Marketing, etc.)
- Telecommunications (5G, Network Infrastructure, Satellite, etc.)
- Transportation & Logistics (EV, Autonomous Vehicles, Aviation, etc.)
- Agriculture & Food (AgTech, Sustainable Farming, Food Production, etc.)
- Construction & Real Estate (Commercial, Residential, Smart Buildings, etc.)
- Hospitality & Tourism (Hotels, Travel Tech, Events, etc.)
- Non-Profit & Social Services (Charitable, Environmental, Humanitarian, etc.)

---

## 🔒 Security

- **Clerk** handles all authentication securely
- Server actions validate user authorization before database operations
- Environment variables for sensitive keys (never committed)
- Protected routes enforced via middleware

---

## 📸 Screenshots

### Landing Page
The landing page features a hero section, feature cards, stats, how-it-works steps, testimonials, FAQ accordion, and a call-to-action section.

### Dashboard
Displays industry-specific insights including salary ranges, growth rate, demand level, top skills, market outlook, key trends, and recommended skills.

### Resume Builder
A full-featured markdown editor with AI-powered content improvement for individual resume sections.

### Interview Prep
Generate industry-specific quizzes, view performance stats, and track progress over time with charts.

### Cover Letter Generator
Create tailored cover letters by providing job title, company name, and job description.

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License.

---

## 👨‍💻 Author

**Himanshu Verma**  
[GitHub](https://github.com/Verma-Himanshu-22)

---

## 🙏 Acknowledgments

- [Next.js](https://nextjs.org/) — The React Framework
- [Clerk](https://clerk.com/) — Authentication & User Management
- [Google Gemini](https://ai.google.dev/) — AI Model
- [Prisma](https://www.prisma.io/) — Database ORM
- [shadcn/ui](https://ui.shadcn.com/) — UI Components
- [Tailwind CSS](https://tailwindcss.com/) — Utility-first CSS
- [Inngest](https://www.inngest.com/) — Background Jobs
- [Recharts](https://recharts.org/) — Charting Library

---

## 📞 Support

For support, please open an issue in the GitHub repository or contact the maintainer.

---

**Built with ❤️ using Next.js, AI, and modern web technologies.**