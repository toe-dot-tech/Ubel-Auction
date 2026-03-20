
# 💎 Ubel: Premium Real-Time Auction App

A production-ready, high-end auction marketplace built with **Flutter** and **Supabase**. Ubel demonstrates enterprise-level architecture, real-time data synchronization, and a luxury-focused Material 3 design system.

---

## 📸 App Preview

| Home Screen | Auction Detail | Create Listing |
| :---: | :---: | :---: |
| <img src="https://via.placeholder.com/400x800.png?text=Home+Screen" width="200" /> | <img src="https://via.placeholder.com/400x800.png?text=Detail+Screen" width="200" /> | <img src="https://via.placeholder.com/400x800.png?text=Create+Screen" width="200" /> |

> 
---

## 🚀 Key Features

- **Real-time Bidding**: Instant, live bid updates using Supabase Realtime (WebSockets).
- **Luxury UI/UX**: Custom animations, shimmer loading effects, and smooth page transitions via GoRouter.
- **Dynamic Category Selection**: Interactive grid-based category picking (Art, Collectibles, Memes, etc.).
- **Secure Authentication**: JWT-based authentication with persistent sessions.
- **Media Management**: High-performance image caching and Supabase Storage integration for uploads.
- **Atomic Transactions**: Database-level functions to ensure bid integrity and prevent race conditions.

---

## 🛠 Tech Stack

- **Framework**: Flutter 3.x (latest stable)
- **State Management**: Riverpod 2.x (with Generators & AsyncNotifier)
- **Backend**: Supabase (PostgreSQL, Realtime, Auth, Storage)
- **Routing**: GoRouter (Declarative routing with deep link support)
- **Networking**: Dio + Supabase Flutter SDK
- **Database**: PostgreSQL with Row Level Security (RLS)
- **Local Storage**: Flutter Secure Storage

---

## 🏗 Architecture (Screaming Architecture)

Ubel follows a feature-first **Clean Architecture** pattern to ensure the codebase remains maintainable and scalable.

```text
lib/
├── features/          # Feature-based modules
│   ├── auth/          # Authentication & User onboarding
│   ├── auction/       # Core marketplace & listing logic
│   ├── bidding/       # Real-time bid streams & placement
│   └── profile/       # User management & listing history
├── core/              # Shared theme (AppColors), extensions, & utilities
├── services/          # Supabase client & external API wrappers
└── widgets/           # Global UI components (AppImage, Buttons, etc.)
```

---

## 🚦 Getting Started

### Prerequisites
- Flutter SDK >= 3.0.0
- A Supabase Project ([supabase.com](https://supabase.com))

### Installation

1. **Clone the repository**
   ```bash
   git clone [https://github.com/yourusername/ubel.git](https://github.com/yourusername/ubel.git)
   cd ubel
   ```

2. **Install dependencies**
   ```bash
   flutter pub get
   ```

3. **Database Setup (SQL)**
   Run the following in your Supabase SQL Editor to enable the bidding logic:
   - Apply schema from `database/schema.sql`.
   - Enable **Realtime** for `auctions` and `bids` tables.
   - Deploy the `place_bid()` RPC function for atomic transactions.

4. **Environment Configuration**
   Update your Supabase credentials in `lib/main.dart` (or use a `.env` file):
   ```dart
   await Supabase.initialize(
     url: 'YOUR_SUPABASE_URL',
     anonKey: 'YOUR_ANON_KEY',
   );
   ```

5. **Run the app**
   ```bash
   flutter run
   ```

---

## 🔧 Enterprise-Grade Implementation

### ⚡ Atomic Bidding System
To prevent race conditions where two users bid at the same microsecond, Ubel uses a PostgreSQL function:
- Validates if the auction is still active.
- Ensures the bid is higher than the current price.
- Atomically updates the `current_price` and `bid_count`.

### 🧠 Modern State Management
- **Riverpod Generators**: Used for type-safe, compile-time provider generation.
- **Family Providers**: Efficiently manages state for specific IDs without global pollution.
- **Invalidation Logic**: Uses `ref.invalidate()` for clean manual refreshes (Pull-to-Refresh).

### 🔗 Deep Linking
Configured via **GoRouter** to support universal links:
- `ubel://auction/:id` - Navigate directly to a specific item from a shared link.

---

## 🛡 Security
- **Row Level Security (RLS)**: Users can only update their own listings.
- **Server-Side Validation**: Bids are validated on the database level, not just the UI.
- **Secure Storage**: Sensitive tokens are stored in encrypted local storage.

---

## 🏢 Portfolio Highlight

This project demonstrates expertise in:
- **Real-time Data Architecture** (Supabase/WebSockets)
- **Clean Code & Linting** (Strict analysis options)
- **Complex UI Performance** (Virtualization, Image Caching)
- **Scale-Ready Design** (Riverpod/Clean Architecture)

---

## 🤝 Contributing

1. Fork the Project.
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the Branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

---

## 📄 License
Distributed under the MIT License. See `LICENSE` for more information.

---
**Built with ❤️ by TOE Tech**

