# ecom-micro-ui

This project consists of two main applications: an **Admin Dashboard** for managing products, users, orders, and analytics, and a **Client Application** for browsing products and making purchases.

## 📋 Project Overview

### Architecture
- **Monorepo Structure**: Two independent Next.js applications (admin & client) with shared utilities
- **Admin Dashboard**: Comprehensive management system for e-commerce operations
- **Client App**: Customer-facing storefront for product browsing and purchasing
- **Tech Stack**: Next.js 15, React 19, TypeScript, Tailwind CSS

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ or higher
- pnpm (recommended) or npm

### Installation

```bash
# Install dependencies for admin panel
cd admin
pnpm install

# Install dependencies for client application
cd ../client
pnpm install
```

### Running the Applications

#### Admin Dashboard
```bash
cd admin
pnpm run dev
# Runs on http://localhost:3000
```

#### Client Application
```bash
cd client
pnpm run dev
# Runs on http://localhost:3001 (if port 3000 is taken)
```

### Building for Production

```bash
# Admin
cd admin
pnpm run build
pnpm run start

# Client
cd client
pnpm run build
pnpm run start
```

## 📁 Project Structure

### `/admin` - Admin Dashboard
**Purpose**: Comprehensive management system for e-commerce operations

#### Key Features
- **Dashboard Homepage**: Real-time analytics and metrics
  - Bar charts for sales data
  - Area charts for trends
  - Pie charts for distribution
  - Transaction history
  - Popular products overview
  - Todo list for tasks

- **Products Management** (`/products`)
  - View all products in data table
  - Add new products
  - Edit existing products
  - Manage product categories
  - Image management

- **Users Management** (`/users`)
  - User list with pagination
  - User details page (`/users/[id]`)
  - Add new users
  - Edit user information
  - User profile management

- **Orders Management** (`/payments`)
  - Order tracking
  - Payment status monitoring
  - Order history

#### Components
```
admin/src/components/
├── AddProduct.tsx          # Product creation form
├── AddUser.tsx             # User creation form
├── AddOrder.tsx            # Order creation form
├── AddCategory.tsx         # Category management
├── EditUser.tsx            # User editing form
├── AppSidebar.tsx          # Navigation sidebar
├── Navbar.tsx              # Top navigation bar
├── CardList.tsx            # Reusable card list component
├── TablePagination.tsx     # Pagination for data tables
├── TodoList.tsx            # Task management widget
├── AppAreaChart.tsx        # Area chart visualization
├── AppBarChart.tsx         # Bar chart visualization
├── AppLineChart.tsx        # Line chart visualization
├── AppPieChart.tsx         # Pie chart visualization
├── providers/
│   └── ThemeProvider.tsx   # Dark/light theme support
└── ui/                     # Shadcn UI components (Radix-based)
    ├── button.tsx
    ├── card.tsx
    ├── form.tsx
    ├── input.tsx
    ├── select.tsx
    ├── table.tsx
    ├── sidebar.tsx
    ├── dropdown-menu.tsx
    └── ... (20+ UI primitives)
```

#### Tech Stack
- **Framework**: Next.js 15.3.0 with Turbopack
- **UI Components**: Radix UI + Tailwind CSS (via Shadcn)
- **Forms**: React Hook Form + Zod validation
- **Charts**: Recharts 2.15.2
- **Date Handling**: date-fns
- **Icons**: Lucide React
- **Styling**: Tailwind CSS 4 + Class Variance Authority

### `/client` - Customer Storefront
**Purpose**: Customer-facing e-commerce application for browsing and purchasing products

#### Key Features
- **Product Browsing** (`/products`)
  - Product listing with grid layout
  - Category filtering
  - Featured product section
  - Individual product details page (`/products/[id]`)

- **Shopping Cart** (`/cart`)
  - Persistent cart using Zustand store
  - Cart item management
  - Quantity adjustment
  - Size and color selection

- **Search & Filter**
  - Search bar for product search
  - Category-based filtering
  - Filter component for advanced search

- **Checkout**
  - Shipping form with address input
  - Payment form processing
  - Order confirmation

#### Components
```
client/src/components/
├── ProductList.tsx         # Product grid display
├── ProductCard.tsx         # Individual product card
├── ProductInteraction.tsx  # Product interaction logic
├── Categories.tsx          # Category selection
├── Filter.tsx              # Advanced filtering
├── SearchBar.tsx           # Product search
├── ShoppingCartIcon.tsx    # Cart icon with badge
├── PaymentForm.tsx         # Payment processing form
├── ShippingForm.tsx        # Shipping address form
├── Navbar.tsx              # Navigation bar
└── Footer.tsx              # Footer component
```

#### State Management
- **Cart Store** (`src/stores/cartStore.ts`)
  - Built with Zustand for lightweight state management
  - Persistent storage using localStorage
  - Features:
    - Add/remove items from cart
    - Update quantities
    - Track selected sizes and colors
    - Cart total calculations

#### Tech Stack
- **Framework**: Next.js 15.4.5 with Turbopack
- **State Management**: Zustand 5.0.7
- **Forms**: React Hook Form + Zod validation
- **Notifications**: React Toastify
- **Icons**: Lucide React
- **Styling**: Tailwind CSS 4
- **Types**: TypeScript

## 🛠️ Development

### Code Quality
- **Linting**: ESLint 9 configured for Next.js
- **TypeScript**: Strict mode enabled for both apps
- **Styling**: Tailwind CSS with custom configuration

### Environment Setup
Both applications use:
- TypeScript strict mode
- Path aliasing: `@/*` points to `src/`
- ES2017 target for broad compatibility

### Important Configuration

#### Admin `next.config.ts`
- Remote image support from `images.pexels.com`
- Optimized image handling

#### Client `next.config.ts`
- Image optimization for external sources

## 📦 Dependencies Overview

### Shared Dependencies
| Package | Version | Purpose |
|---------|---------|---------|
| React | 19.x | UI library |
| Next.js | 15.x | Framework |
| TypeScript | 5.x | Type safety |
| Tailwind CSS | 4 | Styling |
| Zod | 3-4.x | Schema validation |
| React Hook Form | 7.x | Form management |

### Admin-Specific
- `@tanstack/react-table` - Advanced data tables
- `recharts` - Chart visualizations
- `@radix-ui/*` - UI primitive components
- `next-themes` - Theme management

### Client-Specific
- `zustand` - State management
- `react-toastify` - Notifications

## 🎨 Design System

Both applications use a consistent design system based on:
- **Component Library**: Shadcn UI (Radix-based)
- **Styling**: Tailwind CSS 4
- **Icons**: Lucide React
- **Animations**: tw-animate-css

## 📖 API Integration

The applications are structured to integrate with backend APIs:

### Expected API Endpoints

#### Products
- `GET /api/products` - List all products
- `GET /api/products/[id]` - Get product details
- `POST /api/products` - Create product (admin)
- `PUT /api/products/[id]` - Update product (admin)

#### Users
- `GET /api/users` - List users (admin)
- `GET /api/users/[id]` - Get user details
- `POST /api/users` - Create user (admin)
- `PUT /api/users/[id]` - Update user (admin)

#### Orders/Payments
- `GET /api/orders` - List orders (admin)
- `POST /api/orders` - Create order
- `POST /api/payments` - Process payment

#### Categories
- `GET /api/categories` - List categories
- `POST /api/categories` - Create category (admin)

## 🔐 Security Considerations

- TypeScript strict mode for type safety
- Zod validation for form inputs
- Environment variables for sensitive data
- Next.js built-in security features

## 🚢 Deployment

Both applications are configured for deployment on platforms supporting Next.js:
- Vercel (recommended)
- Netlify
- Docker
- Traditional Node.js hosting

### Build Optimization
- Turbopack enabled for faster builds
- Production-optimized builds with `pnpm run build`

## 📝 Scripts Reference

### Available Commands

**Both Admin & Client Apps**
```bash
pnpm run dev      # Start development server with Turbopack
pnpm run build    # Production build
pnpm run start    # Start production server
pnpm run lint     # Run ESLint
```

## 🤝 Contributing

When developing new features:
1. Maintain TypeScript strict mode compliance
2. Follow the existing component structure
3. Use Shadcn UI components for consistency
4. Validate forms with Zod schemas
5. Run linting before committing

## 📄 License

This project is private. All rights reserved.

## 📞 Support

For questions or issues, contact the development team.

---

**Last Updated**: December 2025
**Node.js Requirement**: 18+
**Package Manager**: pnpm (recommended)
