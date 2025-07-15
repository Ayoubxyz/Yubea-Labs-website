# Yubea Labs Website

A modern, conversion-optimized website for Yubea Labs, a no-code software agency serving service-based businesses in the Gulf region. Built with Astro and Tailwind CSS, fully compatible with Netlify hosting.

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ 
- npm or yarn package manager

### Installation
```bash
# Clone the repository
git clone <repository-url>
cd yubea-labs-website

# Install dependencies
npm install

# Start development server
npm run dev
```

Visit `http://localhost:4321` to view the website locally.

## 📁 Project Structure

```
yubea-labs-website/
├── public/                 # Static assets
│   ├── sitemap.xml        # SEO sitemap
│   ├── robots.txt         # Search engine directives
│   └── site.webmanifest   # PWA manifest
├── src/
│   ├── components/        # Reusable components
│   │   ├── Header.astro   # Navigation header
│   │   ├── Footer.astro   # Site footer
│   │   ├── Hero.astro     # Hero section
│   │   └── SEO.astro      # SEO meta tags
│   ├── layouts/           # Page layouts
│   │   ├── Layout.astro   # Base HTML layout
│   │   └── MainLayout.astro # Main site layout
│   ├── pages/             # Website pages
│   │   ├── index.astro    # Homepage
│   │   ├── services.astro # Services page
│   │   ├── process.astro  # Process page
│   │   ├── testimonials.astro # Testimonials
│   │   ├── faqs.astro     # FAQ page
│   │   ├── contact.astro  # Contact page
│   │   ├── lead-magnet.astro # Lead magnet
│   │   └── success.astro  # Form success page
│   └── styles/
│       └── global.css     # Global styles
├── assets/                # Image assets
├── netlify.toml          # Netlify configuration
└── astro.config.mjs      # Astro configuration
```

## 🛠 Tech Stack

- **Framework**: Astro 5.11.1
- **Styling**: Tailwind CSS
- **Deployment**: Netlify
- **Forms**: Netlify Forms
- **SEO**: Built-in structured data and meta tags

## 📄 Pages Overview

### Homepage (`/`)
- Hero section with value proposition
- Service overview cards
- Yubea Launch Loop™ process
- Call-to-action sections

### Services (`/services`)
- Detailed service packages with pricing
- Client Portal Starter Kit ($499)
- MVP Launch Pack ($799)
- Automation Setup ($299)
- CRM Buildout ($399)
- Add-ons and support options

### Process (`/process`)
- Yubea Launch Loop™ methodology
- 3-step process: Discover → Build → Scale
- Timeline and deliverables

### Testimonials (`/testimonials`)
- Client success stories
- Company logos and metrics
- Social proof elements

### FAQs (`/faqs`)
- Common questions about no-code development
- Pricing and timeline information
- Technical capabilities

### Contact (`/contact`)
- Contact form with Netlify Forms integration
- Calendly booking placeholder
- Contact information and social links

### Lead Magnet (`/lead-magnet`)
- No-Code Readiness Checklist offer
- Lead capture form
- Detailed benefits and testimonials

### Success (`/success`)
- Form submission confirmation
- Next steps and resources
- Additional contact options

## 🎨 Design Features

- **Responsive Design**: Mobile-first approach with Tailwind CSS
- **Modern UI**: Clean, professional design with gradient accents
- **Conversion Optimized**: Strategic CTAs and social proof
- **Gulf Region Focus**: Localized content and cultural considerations
- **Performance Optimized**: Fast loading with optimized assets

## 📧 Forms Integration

The website uses Netlify Forms for lead capture:

### Contact Form
- Location: `/contact`
- Form name: `contact`
- Fields: Name, email, company, phone, service interest, timeline, message, budget
- Redirect: `/success`

### Lead Magnet Form
- Location: `/lead-magnet`
- Form name: `lead-magnet`
- Fields: Name, email, company, role, industry, team size
- Redirect: `/success`

## 🔍 SEO Features

- **Meta Tags**: Comprehensive title, description, and social media tags
- **Structured Data**: Organization and service schema markup
- **Sitemap**: Auto-generated XML sitemap
- **Robots.txt**: Search engine crawling directives
- **Open Graph**: Social media sharing optimization
- **Performance**: Optimized loading and Core Web Vitals

## 🚀 Deployment

### Netlify Deployment

1. **Connect Repository**:
   - Link your Git repository to Netlify
   - Set build command: `npm run build`
   - Set publish directory: `dist`

2. **Environment Variables** (if needed):
   - No environment variables required for basic deployment

3. **Form Handling**:
   - Netlify Forms are automatically detected
   - Form submissions will appear in Netlify dashboard

4. **Custom Domain**:
   - Configure custom domain in Netlify settings
   - Update `site` URL in `astro.config.mjs`

### Build Commands

```bash
# Development
npm run dev

# Production build
npm run build

# Preview production build
npm run preview
```

## 🔧 Customization

### Updating Content

1. **Service Packages**: Edit `/src/pages/services.astro`
2. **Testimonials**: Update `/src/pages/testimonials.astro`
3. **FAQs**: Modify `/src/pages/faqs.astro`
4. **Contact Info**: Update contact details in relevant components

### Styling Changes

- Global styles: `/src/styles/global.css`
- Tailwind configuration: `tailwind.config.js`
- Component-specific styles: Within individual `.astro` files

### SEO Updates

- Meta tags: `/src/components/SEO.astro`
- Sitemap: `/public/sitemap.xml`
- Structured data: Update schema in SEO component

## 📊 Analytics & Tracking

To add analytics:

1. **Google Analytics**: Add tracking code to `Layout.astro`
2. **Facebook Pixel**: Include in head section
3. **Conversion Tracking**: Set up goal tracking for form submissions

## 🔒 Security

- **Form Protection**: Netlify Forms include spam protection
- **HTTPS**: Automatically enabled on Netlify
- **Content Security**: No user-generated content vulnerabilities

## 🐛 Troubleshooting

### Common Issues

1. **Build Failures**:
   - Check Node.js version (18+ required)
   - Clear `node_modules` and reinstall dependencies
   - Verify all imports and file paths

2. **Form Submissions Not Working**:
   - Ensure `data-netlify="true"` attribute is present
   - Check form name matches Netlify dashboard
   - Verify all required fields are properly named

3. **Styling Issues**:
   - Check Tailwind CSS classes are valid
   - Ensure global styles are imported correctly
   - Verify responsive breakpoints

## 📞 Support

For technical support or customization requests:
- Email: hello@yubealabs.com
- Documentation: This README file
- Astro Docs: https://docs.astro.build

## 📝 License

This project is proprietary to Yubea Labs. All rights reserved.

---

Built with ❤️ by Manus AI for Yubea Labs

