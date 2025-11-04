# 🎨 Farcaster Market

> **Trade NFTs without leaving Farcaster** - A neobrutalism-styled NFT marketplace built as a native Farcaster mini-app.

[![Live Demo](https://img.shields.io/badge/🚀_Live_Demo-fcmarket.xyz-8A63D2?style=for-the-badge)](https://fcmarket.xyz)
[![Contest Entry](https://img.shields.io/badge/💎_Procoin_Contest-5M_$PRO_Prize-FFD700?style=for-the-badge)](https://warpcast.com/procoin)

## 🏆 Contest Submission

**Built for the Procoin Contest** - competing for 5,000,000 $PRO tokens!

- **Submission Date**: June 10, 2024
- **Timeline**: 5 days development
- **Focus**: Native Farcaster experience with zero friction

---

## ✨ Features

### 🔥 Core Functionality

- **🛒 Browse & Buy NFTs** - Seamless purchasing with OnchainKit transactions
- **📝 List Your NFTs** - Auto-detect owned NFTs and list them for sale
- **👤 User Profiles** - Activity tracking, favorites, and social features
- **🔗 Auto-Wallet Connection** - Zero-friction onboarding (no manual wallet setup!)
- **📱 Mobile-First Design** - Perfect experience on mobile devices

### 🎯 Farcaster Integration

- **🆔 Native Authentication** - Auto-login with Farcaster context
- **📢 Social Sharing** - Auto-compose casts for purchases and listings
- **🔄 Real-time Sync** - User data syncs with Farcaster profile
- **🎨 Frame-Native UI** - Feels like part of the Farcaster ecosystem

### ⚡ Technical Highlights

- **🏗️ Base Chain** - Built exclusively on Base for fast, cheap transactions
- **🔌 Real NFT Data** - Alchemy API integration for live NFT collections
- **💾 Persistent State** - Supabase database for user activity and favorites
- **🎭 Neobrutalism Design** - Bold, high-contrast UI that stands out

---

## 🛠️ Tech Stack

### Frontend

- **[Next.js 14](https://nextjs.org)** - React framework with App Router
- **[MiniKit](https://docs.coinbase.com/mini-kit)** - Farcaster mini-app SDK
- **[OnchainKit](https://onchainkit.xyz)** - Coinbase's blockchain UI components
- **[Thirdweb](https://thirdweb.com)** - NFT marketplace contracts and SDK
- **[Tailwind CSS](https://tailwindcss.com)** - Utility-first CSS framework
- **[shadcn/ui](https://ui.shadcn.com)** - Modern UI components
- **[Lucide Icons](https://lucide.dev)** - Beautiful icon library

### Blockchain

- **[Base](https://base.org)** - Ethereum Layer 2 network
- **[wagmi](https://wagmi.sh)** - React hooks for Ethereum
- **[viem](https://viem.sh)** - TypeScript Ethereum library

### Backend & Data

- **[Supabase](https://supabase.com)** - Database and real-time subscriptions
- **[Alchemy NFT API](https://alchemy.com)** - NFT data indexing
- **[Vercel](https://vercel.com)** - Deployment and hosting

---

## 🚀 Quick Start

### Prerequisites

- Node.js 18+ and npm
- Farcaster account for testing
- Base network wallet with some ETH

### 1. Clone Repository

```bash
git clone https://github.com/your-username/farcaster-market.git
cd farcaster-market
npm install
```

### 2. Environment Variables

Create `.env.local` file:

```bash
# Required for core functionality
NEXT_PUBLIC_THIRDWEB_CLIENT_ID=your_thirdweb_client_id
NEXT_PUBLIC_ONCHAINKIT_API_KEY=your_onchainkit_api_key
NEXT_PUBLIC_MARKETPLACE_ADDRESS=0x1170fC1e672C825886C4D4692F017a9AF0a90aEc

# Database (Supabase)
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key

# NFT Data (Alchemy)
NEXT_PUBLIC_ALCHEMY_API_KEY=your_alchemy_api_key

# Optional: Custom domain
NEXT_PUBLIC_URL=https://fcmarket.xyz
```

### 3. Database Setup

```sql
-- Run in Supabase SQL editor
-- (See database-schema.sql for complete setup)

CREATE TABLE users (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  fid INTEGER UNIQUE NOT NULL,
  username TEXT,
  display_name TEXT,
  pfp_url TEXT,
  bio TEXT,
  wallet_address TEXT,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW(),
  last_seen TIMESTAMP DEFAULT NOW()
);

-- Additional tables: activity, user_favorites, nft_collections
-- (Full schema in database-schema.sql)
```

### 4. Development

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to see the app.

### 5. Testing in Farcaster

1. Deploy to Vercel or similar
2. Create a Farcaster frame pointing to your deployment
3. Test the full mini-app experience

---

## 🏗️ Architecture

### Component Structure

```
src/
├── app/                    # Next.js App Router pages
│   ├── page.tsx           # Home/Browse page
│   ├── list/page.tsx      # List NFTs page
│   ├── profile/page.tsx   # User profile page
│   └── providers.tsx      # App-wide providers
├── components/
│   ├── ui/                # shadcn/ui components
│   └── nft/               # NFT-specific components
├── context/
│   └── UserContext.tsx    # Farcaster user management
├── hooks/
│   ├── useMarketplace.ts  # Thirdweb marketplace
│   ├── useUserNFTs.ts     # User's owned NFTs
│   └── useUser.ts         # Farcaster user data
├── lib/
│   ├── supabase.ts        # Database functions
│   ├── nftApi.ts          # NFT data fetching
│   └── sampleNFTs.ts      # Demo data
└── types/                 # TypeScript definitions
```

### Data Flow

1. **User Authentication**: Automatic via Farcaster context + MiniKit
2. **Wallet Connection**: Auto-connect Coinbase Smart Wallet
3. **NFT Data**: Fetch from Alchemy API → Display in UI
4. **Transactions**: OnchainKit → Thirdweb Marketplace → Base chain
5. **Social**: Auto-compose casts via Farcaster Frame SDK

---

## 🎨 Design System

### Neobrutalism Principles

- **High Contrast**: Black borders, bold shadows
- **Chunky Elements**: Thick borders (3-4px), large shadows
- **Bold Typography**: Heavy font weights, uppercase text
- **Vibrant Colors**: Farcaster purple (#8A63D2) with accent colors

### Color Palette

```css
/* Primary */
--primary: #8a63d2; /* Farcaster Purple */
--primary-dark: #6b46c1; /* Dark Purple */
--primary-light: #a78bfa; /* Light Purple */

/* Neobrutalism */
--black: #000000;
--white: #ffffff;
--yellow: #fde047; /* Accent */
--red: #ef4444; /* Error */
--green: #22c55e; /* Success */
```

---

## 📱 User Experience

### Zero-Friction Onboarding

1. User opens mini-app in Farcaster
2. **Auto-authentication** via Farcaster context
3. **Auto-wallet connection** via MiniKit
4. **NFTs auto-populate** from connected wallet
5. Ready to buy/sell immediately!

### Core User Flows

#### Browse & Buy NFTs

1. Browse NFT grid on home page
2. Tap NFT to view details
3. Tap "BUY" → OnchainKit transaction
4. Auto-compose success cast to share

#### List Your NFTs

1. Navigate to "LIST" tab
2. See your owned NFTs auto-populated
3. Select NFT + set price
4. Create listing → Marketplace contract
5. Auto-compose listing announcement

#### Social Integration

- **Purchase Sharing**: "Just bought [NFT] on Farcaster Market! 🎉"
- **Listing Sharing**: "Listed [NFT] for sale! Check it out:"
- **Profile Activity**: Track all marketplace activities

---

## 🚀 Deployment

### Production Deployment

```bash
# Deploy to Vercel
vercel deploy --prod

# Configure custom domain
vercel domains add fcmarket.xyz
```

### Environment Setup

- **Vercel**: Environment variables in dashboard
- **Supabase**: Database tables and RLS policies
- **Custom Domain**: DNS configuration for fcmarket.xyz

### Performance Optimizations

- **Image Optimization**: Next.js Image component
- **Bundle Analysis**: `npm run analyze`
- **Edge Functions**: API routes deployed to edge
- **CDN**: Static assets via Vercel CDN

---

## 🧪 Testing

### Development Testing

```bash
# Type checking
npm run type-check

# Linting
npm run lint

# Build verification
npm run build
```

### User Acceptance Testing

- [ ] Auto-authentication works
- [ ] Wallet connects automatically
- [ ] NFTs load from real API
- [ ] Buy transactions complete
- [ ] Listing creation works
- [ ] Mobile experience smooth
- [ ] Social sharing functions

---

## 🏆 Contest Advantages

### Unique Value Propositions

1. **Zero-Friction UX**: No wallet setup or login required
2. **Native Farcaster Feel**: Integrated, not external
3. **Real Functionality**: Working marketplace, not just concept
4. **Professional Polish**: Production-ready design and code
5. **Mobile-Optimized**: Perfect for mobile-first Farcaster users

### Technical Innovation

- **Auto-Wallet Connection**: Seamless MiniKit integration
- **Real-time NFT Data**: Live API integration
- **Social-First Design**: Built for sharing and community
- **Neobrutalism UI**: Distinctive visual identity

---

## 📊 Metrics & Analytics

### Performance Targets

- **Load Time**: < 2 seconds initial load
- **Transaction Success**: > 95% success rate
- **Mobile Score**: > 90 Lighthouse mobile score
- **Accessibility**: WCAG 2.1 AA compliance

### User Engagement

- Track purchases and listings
- Monitor social sharing rates
- Measure user retention
- Analyze transaction volumes

---

## 🤝 Contributing

### Development Setup

1. Fork the repository
2. Create feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Open Pull Request

### Code Standards

- **TypeScript**: Strict mode enabled
- **ESLint**: Enforced linting rules
- **Prettier**: Code formatting
- **Conventional Commits**: Commit message format

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **Procoin Team** - For hosting the contest and building the Farcaster ecosystem
- **Coinbase** - For MiniKit and OnchainKit tools
- **Thirdweb** - For marketplace infrastructure
- **Base** - For the fast, cheap blockchain infrastructure
- **Farcaster Community** - For inspiration and feedback

---

## 📧 Contact

**Project Link**: [https://fcmarket.xyz](https://fcmarket.xyz)
**Contest Entry**: Built for Procoin Contest 2024
**Developer**: [Your Twitter/Farcaster handle]

---

<div align="center">

**🎯 Trade NFTs without leaving Farcaster**

Built with ❤️ for the Farcaster community

[Live Demo](https://fcmarket.xyz) • [Contest Details](https://warpcast.com/procoin) • [Documentation](https://github.com/your-username/farcaster-market)

</div>
.
