# BrandBeat Website Migration Project

This repository contains the components of the BrandBeat website project, organized into separate directories for different aspects of the application.

## 📁 Project Structure

```
/
├── CMS/                # Exported CSV files from Webflow CMS
├── frontend/           # Raw exported code from Webflow
├── frontend-astro/     # AstroJS website converted from Webflow exports
└── strapi/             # Strapi headless CMS instance
```

## 🔍 Component Details

### CMS
Contains exported CSV files from the Webflow CMS. These files represent structured content that was managed in Webflow before migrating to Strapi.

**Purpose**: Reference data for migration to Strapi or backup of original content structure.

### frontend
Raw code exported directly from Webflow, containing the original website design and functionality.

**Purpose**: Serves as the source material for the AstroJS conversion and reference for design specifications.

### frontend-astro
A partially converted website using Astro framework, based on the raw Webflow exports. This represents the frontend application that will eventually connect to the Strapi backend.

**Key files and directories**:
- `src/components/` - Reusable UI components organized by page/function
- `src/layouts/` - Page layout templates
- `src/pages/` - Route-based page components
- `public/` - Static assets including CSS and images

**Commands**:
```bash
# Install dependencies
pnpm install

# Start development server
pnpm run dev        # Runs at localhost:4321

# Build for production
pnpm run build      # Output to ./dist/

# Preview production build
pnpm run preview
```

### strapi
A Strapi instance serving as the headless CMS for the project. This manages the content that will be consumed by the frontend-astro application.

**Commands**:
```bash
# Install dependencies
pnpm install

# Seed example data (important first step)
pnpm run seed:example

# Start development server
pnpm run develop    # Admin UI at localhost:1337/admin

# Start production server
pnpm run start

# Build admin panel
pnpm run build
```

## 🔄 Development Workflow

1. **Content Management**: Add/edit content through the Strapi admin interface
2. **Frontend Development**: 
   - Make component changes in the frontend-astro project
   - Connect to Strapi API endpoints to fetch dynamic content
   - Test locally with `pnpm run dev`
3. **Deployment**:
   - Build the Astro frontend with `pnpm run build`
   - Deploy the Strapi instance separately
   - Configure proper environment variables for production

## 🚀 Getting Started

1. Clone this repository
2. Set up Strapi:
   - Navigate to `/strapi`
   - Copy `.env.example` to `.env` (create if needed) and configure variables
   - Run `pnpm install`
   - **Important**: Run `pnpm run seed:example` to populate with test data
   - Run `pnpm run develop`
3. Set up frontend-astro:
   - Navigate to `/frontend-astro`
   - Run `pnpm install`
   - Create a `.env` file with the necessary variables to connect to your Strapi instance
   - Run `pnpm run dev`
4. Access the development sites:
   - Frontend: http://localhost:4321
   - Strapi Admin: http://localhost:1337/admin

## 📦 Package Manager

This project uses **pnpm** as the default package manager. If you prefer to use npm or yarn instead:

### Switching to npm:
1. Delete the `pnpm-lock.yaml` files in both `/frontend-astro` and `/strapi` directories
2. Delete the `node_modules` folders in both directories
3. Run `npm install` in each directory
4. Use `npm run` commands instead of `pnpm run` commands

### Switching to yarn:
1. Delete the `pnpm-lock.yaml` files in both `/frontend-astro` and `/strapi` directories
2. Delete the `node_modules` folders in both directories
3. Run `yarn` in each directory
4. Use `yarn` commands instead of `pnpm run` commands

## ⚠️ Current Limitations

- **Demo status**: Currently, only the `/blog` page is functioning as a demonstration of the Strapi integration
- The rest of the site is abandoned and not in active development
- Ensure your `.env` file in the frontend-astro project has the correct configuration to connect to the Strapi instance

## 💻 Tech Stack

- **Frontend**: 
  - Astro.js
  - HTML/CSS from Webflow
  - Responsive design
- **Backend**:
  - Strapi Headless CMS
  - REST API
- **Database**:
  - Configurable through Strapi (default: SQLite in development)
