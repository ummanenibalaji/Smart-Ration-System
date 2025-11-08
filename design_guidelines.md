# Smart Ration System - Design Guidelines

## Design Approach

**Selected Framework**: Material Design 3 with government service adaptations
**Rationale**: Information-dense civic platform requiring trust, accessibility, and efficient data handling across multiple user roles. Material Design provides robust patterns for forms, tables, cards, and data visualization while maintaining a professional, credible aesthetic suitable for government services.

## Typography System

**Font Family**: 
- Primary: Inter (via Google Fonts CDN)
- Monospace: JetBrains Mono (for ration card numbers, booking IDs)

**Type Scale**:
- Headings: 2xl (section headers), xl (card titles), lg (subsections)
- Body: base (primary content), sm (secondary info, metadata)
- Caption: xs (helper text, timestamps, disclaimers)
- Weight Distribution: semibold for headers, medium for buttons/labels, normal for body

## Layout System

**Spacing Primitives**: Tailwind units of 2, 4, 6, 8, 12, 16, 24
- Component padding: p-4 to p-6
- Section spacing: space-y-6 to space-y-8
- Card gaps: gap-4
- Page margins: px-4 md:px-8 lg:px-12

**Grid Structure**:
- Max container width: max-w-7xl mx-auto
- Dashboard layouts: 12-column grid with responsive breakpoints
- Form layouts: max-w-2xl for optimal readability
- Card grids: grid-cols-1 md:grid-cols-2 lg:grid-cols-3

## Component Library

### Navigation
**Primary Navigation** (Citizen App):
- Bottom navigation bar (mobile) with 4-5 icons: Home, Browse Items, My Orders, Profile
- Top app bar with logo, search, and notification bell
- Sidebar navigation (desktop) with collapsible menu groups

**Admin/Shopkeeper Dashboard**:
- Persistent sidebar with hierarchical menu structure
- Top bar with breadcrumbs, search, user profile dropdown
- Quick action floating button (bottom-right) for common tasks

### Cards & Information Display

**Ration Item Cards**:
- Elevated cards with subtle shadow
- Structure: Item image (if available) or icon, item name (text-lg font-semibold), unit price, available stock badge, quota indicator
- Footer: "Add to Cart" button spanning card width
- Grid layout with consistent card heights

**Order Summary Cards**:
- Timeline-style display showing order status progression
- Each card includes: Booking ID (monospace), order date, items list (compact), total amount, status badge, action buttons
- Expandable detail sections

**Quota Display Card**:
- Prominent card on dashboard showing monthly quota
- Progress bars for each item category
- Visual indicators: available (standard), low (warning state), exhausted (disabled state)

### Forms & Input

**Registration/Login Forms**:
- Single-column layout, max-w-md centered
- Input fields: rounded-lg borders, p-3 padding, focus states with ring
- OTP input: 6 individual boxes with monospace font
- Ration card input: formatted with hyphens, auto-uppercase
- Error states below inputs with helper text

**Booking Form**:
- Multi-step process with progress indicator at top
- Step 1: Item selection with quantity steppers
- Step 2: Delivery slot picker (calendar grid + time slots)
- Step 3: Payment method selection (radio cards)
- Step 4: Order confirmation summary
- Sticky footer with total amount and action buttons

### Data Tables

**Stock Management (Shopkeeper)**:
- Responsive table with fixed header
- Columns: Item Name, Current Stock, Quota Allocated, Orders Pending, Actions
- Row actions: icon buttons for edit/approve/dispatch
- Pagination at bottom, show 10/25/50 rows dropdown
- Search and filter controls above table

**Order Management (Admin)**:
- Sortable columns with indicators
- Status badges with icons
- Bulk action checkbox column
- Export to CSV button in header

### Buttons & Actions

**Primary Actions**:
- Filled buttons with medium height (h-10 to h-12)
- Rounded corners (rounded-lg)
- Font: font-medium text-sm
- Icons on left when appropriate (using Heroicons)

**Secondary Actions**:
- Outlined buttons with same dimensions
- Ghost buttons for tertiary actions

**FAB (Floating Action Button)**:
- Shopkeeper/Admin dashboards only
- Fixed bottom-right: bottom-6 right-6
- Large circular button with icon

### Status Indicators

**Badges**:
- Pill-shaped with px-3 py-1 padding
- States: Pending, Confirmed, Dispatched, Delivered, Cancelled
- Small text (text-xs font-medium) with icons

**Progress Indicators**:
- Linear progress for quota consumption
- Stepper for order flow (horizontal on desktop, vertical on mobile)
- Circular progress for loading states

### Notifications & Alerts

**Toast Messages**:
- Top-right positioned
- Auto-dismiss after 4 seconds
- Types: Success, Error, Warning, Info
- Include icon and close button

**Banner Alerts**:
- Full-width at page top for important announcements
- Dismissible with action buttons

## Page-Specific Layouts

### Landing/Marketing Page (Pre-Login)

**Hero Section** (h-screen or min-h-[600px]):
- Split layout: Left side with headline, benefits list, dual CTAs ("Get Started" + "Call Us")
- Right side: Hero image showing simplified ration booking interface mockup
- Floating trust badges: "Government Approved" | "Secure Payments" | "10,000+ Users"

**Features Section** (py-16):
- 3-column grid showcasing key features
- Each card: Large icon (h-12 w-12), feature title, 2-3 line description
- Features: Easy Booking, Quota Tracking, Home Delivery, Digital Receipts, Phone Support, Transparent System

**How It Works** (py-16):
- Horizontal timeline with 4 steps (numbered circles connected by lines)
- Step cards with icon, title, description
- Responsive: vertical timeline on mobile

**Social Proof** (py-12):
- 2-column testimonial cards with user photos, quotes, names, locations
- Statistics bar: Orders Completed | Active Users | Partner Shops | Cities Served

**Footer**:
- 4-column layout: About, Quick Links, Contact Info, Download App
- Newsletter signup form inline
- Social media icons
- Government compliance badges

### Dashboard (Citizen)

**Layout**: Sidebar + main content area
- Top stat cards (4-column grid): Current Quota, Active Orders, Total Savings, Next Delivery
- "Quick Book" card with recent items
- Recent orders list (card-based)
- Announcements/updates section

### Browse Items Page

- Filter sidebar (collapsible on mobile): Categories, Price Range, Stock Availability
- Main grid: 3-column item cards
- Sort dropdown: Price, Name, Stock
- Shopping cart summary sticky on desktop (right rail)

### Order Tracking Page

- Order timeline visualization (vertical stepper)
- Map integration placeholder for delivery tracking
- Contact delivery person button
- Order details accordion sections

### Admin Dashboard

- Dense layout with data visualization
- Top KPI cards: Total Users, Active Orders, Stock Levels, Revenue
- Charts section: Orders over time (line graph), Popular items (bar chart)
- Recent activity feed
- Quick actions panel

## Images

**Hero Image**: 
Modern illustration or photo showing a family/individual using a mobile phone with grocery items in background. Should convey trust, ease, and digital convenience. Place on right side of hero section, occupying 50% width on desktop.

**Feature Icons**: 
Use Heroicons for all feature section icons (ShoppingCartIcon, ClipboardDocumentCheckIcon, TruckIcon, ReceiptPercentIcon, PhoneIcon, ShieldCheckIcon)

**Empty States**: 
Simple illustrations for: No orders yet, Cart empty, No items in stock. Use outline style matching Heroicons aesthetic.

## Accessibility & Interaction

- All interactive elements min h-10 (44px touch target)
- Form inputs with visible labels, not just placeholders
- Error messages with aria-live announcements
- Keyboard navigation support for all flows
- Loading states for async operations
- Disabled states clearly differentiated from enabled

## Mobile Considerations

- Bottom navigation priority for primary app
- Collapsible filters and sidebars
- Swipeable card lists for orders/items
- Simplified tables (card view on mobile)
- Sticky headers for forms
- One-handed reachability for CTAs