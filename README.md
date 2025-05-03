#AI Prompt

## Good Prompt Help
1. Automate repetitive tasks by instructing the AI precisely what to do.
2. Debug faster with AI-generated insights and solutions.
3. Build and optimize workflows effortlessly, letting AI handle the heavy lifting once properly guided.


## Create Saas Prompt
<!-- as a full-stack engineer, build an beautiful AI Agent SaaS website. 
also help me to add a Stripe payment feature, add basic functions/features as a saas website, like user auth, sign-up feature, etc. 
This saas website uses n8n as a backend, it provides an automation saas service. 
Input a company website URL, the saas website provides a service, which will provide a summary of the company's research agent service. Does deep research on a company and creates a report that includes demographic information, funding data, web traffic trends, and competitor analysis.  
will add a feature that also uses Supabase as a backend,  -->

You are a professional full stack engineer, Generate a beautiful SaaS web application using Supabase for backend services (auth, DB, real-time), Stripe for subscription management, and React for the frontend. Include email/password + Google OAuth flows, a free-tier page, a multi-plan pricing page, and a user dashboard that displays remaining ‘AI credits’ with a button to purchase more. Scaffold a placeholder component for an AI-Agent service powered by an n8n workflow (integration details to follow). Ensure webhooks are in place to sync Stripe subscription updates to the Supabase database and credit-balance logic is enforced on each AI call.”

Here are main components:
Authentication & User Management
Sign-Up / Login
Email/password registration and login flows
“Sign in with Google” via OAuth
Profile Dashboard
Display user’s name, email, and remaining AI-credits
“Add Credits” button that links to Stripe checkout

Database & Backend
Supabase
Postgres schema for Users, Subscriptions, Credits ledger, and API call logs
Row-level security to restrict each user to their own data
Realtime listeners for credit-balance changes

Payment & Subscriptions
Stripe Integration
Free tier (0 credits included)
Paid tiers:
Starter: 100 credits for $10/month
Webhook endpoint to sync subscription status + credits top-up
Hosted Stripe Checkout pages

Tiered Pages
Free Tier Page
Description of free plan limits (e.g. “Up to 5 AI queries/day”)
“Upgrade” call-to-action
Paid Tier Page
Pricing table comparing Starter, Pro, Enterprise
Feature matrix (credits, SLA, support channel)
“Subscribe” buttons per tier

Pricing Page
Stand-alone page showcasing all current plans
FAQ section under pricing (billing cycle, credits roll-over, cancellation)

AI Agent Service Integration
Placeholder Component
“Your AI Agent is getting smarter… stay tuned!”
Comment or TODO: “Integrate n8n-driven workflow here for Agent orchestration”
Credits Deduction Logic
On each AI Agent invocation, deduct X credits from user account

Front-End
Responsive React SPA
Component library of your choice (Tailwind, Chakra, ShadCN etc.)
Pages & routes:
Home / Landing
Login / Sign Up
Dashboard (profile + credits)
Free Tier Overview
Paid Plans & Checkout
AI Agent Console (with placeholder)


# n8n workflow to automate ImageGen

https://docs.google.com/document/d/1tGF1OLVgzwSt9MDYjmvG9codDEKgiQu1jWtcrpoBqk8/edit?tab=t.0



```
Users table: Extends the built-in auth.users with additional user information
Subscriptions table: Tracks subscription plans and Stripe integration
Credits table: Manages user credit balances
Credit Transactions table: Logs all credit changes (purchases, usage, etc.)
API Calls table: Tracks API usage and consumption
```

Here's what was set up in your database:

Database Schema:

Users table with metadata
Subscriptions table for tracking plan memberships
Credits table to manage user credit balances
Credit transactions ledger to track all credit changes
API call logs to monitor usage
Security:

Row-Level Security (RLS) policies for all tables
Users can only see and modify their own data
Functions:

add_user_credits() - Adds credits to a user's account
use_user_credits() - Deducts credits when a user makes an API call
handle_new_user() - Creates user profiles automatically on signup
Realtime Updates:

Enabled for credits and credit transactions tables
Allows building live-updating UIs for credit balances


## Authentication Setup:

Enable the authentication providers you want (email/password, Google, etc.)
Configure sign-in redirects in the Supabase dashboard
Stripe Integration:

## Add your Stripe secret key to Supabase
Test the subscription and credit purchase flows
Frontend Development:

## Create account management pages
Build subscription management UI
Implement credit balance display

