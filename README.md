Mercatus

Peer-to-Peer Resource Exchange Platform

Overview

Mercatus is a mobile application for direct resource exchange between people without using money. It enables users to publish what they have and what they need, then match and trade locally through map-based discovery, chat negotiation, and QR-based trade confirmation.

The system is designed for crisis scenarios, resource scarcity, and local communities where fast peer-to-peer exchange is essential.

Core Concept

Eliminate both surplus and shortage of resources by enabling direct barter between users.

Key Features
Barter Marketplace

Users create listings defining what they have and what they need, including quantity, category, and description.

Interactive Map

Geolocation-based discovery of available resources in real time.

In-app Chat

Direct communication between users to negotiate trade conditions.

QR Trade System

Secure trade confirmation using QR code scanning.

Reputation System

User trust score updated after each completed trade.

Reporting System

Community moderation through reports and reputation penalties.

User Profiles

Trade history, reputation score, avatar, and activity statistics.

Localization

English and Ukrainian language support.

Tech Stack

Frontend

React Native (Expo SDK ~54)
TypeScript (strict mode)

Backend

Supabase (PostgreSQL via REST API)

Authentication

Custom hash-based authentication (prototype stage)

Maps

react-native-maps

Camera / QR

expo-camera

Location

expo-location

Data Handling

Base64 image storage in database
Polling-based updates (setInterval)
Architecture
No dedicated backend server (thin-client architecture)
Direct communication with Supabase REST API
Central API layer in supabase.ts
Single-file application structure (App.tsx)
Custom screen-state navigation system
App State Model
screen — active view
user — authenticated user
lang — interface language
selectedResource — active trade context
Database Schema
Users
username
password_hash
reputation (default 50)
avatar (base64)
language preference
Resources
type: have / need
location (latitude / longitude)
urgency level
active status
buyer information (after trade)
Trade History
completed trade records (double-entry system)
Messages
chat linked to resource listings
Reports
user reports and moderation actions
Core Flow
User creates a resource listing
Another user discovers it via map or feed
Chat negotiation takes place (optional)
Seller generates QR code
Buyer scans QR code
Trade is confirmed
Reputation is updated
App Screens
Splash / Login / Register
Home (listings feed)
Map view
Notifications
Profile
Create listing
Active trade screen
Chat
User profile
Setup
Requirements
Node.js 18+
Expo CLI
Supabase project
Installation
npm install
npx expo start --tunnel
Supabase Setup
Run provided SQL schema in Supabase dashboard
Disable RLS (development only)
Limitations
Security
Prototype-level password hashing
Row Level Security disabled
No rate limiting
Scalability
Base64 image storage
Polling instead of real-time sockets
No pagination for listings
Future Improvements
Supabase Realtime WebSockets integration
Secure authentication (bcrypt / Argon2)
External object storage for images
Push notifications
Admin moderation dashboard
Advanced search and filtering
Counter-offer trading system
