# Yubea Labs Website - Deployment Guide

This guide provides comprehensive instructions for deploying the Yubea Labs website to Netlify, including setup, configuration, and ongoing maintenance.

## 🚀 Netlify Deployment

### Prerequisites

Before deploying, ensure you have:
- A Netlify account (free tier is sufficient)
- The website repository in a Git hosting service (GitHub, GitLab, or Bitbucket)
- Node.js 18+ installed locally for testing

### Step 1: Repository Setup

1. **Push Code to Git Repository**:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Yubea Labs website"
   git remote add origin <your-repository-url>
   git push -u origin main
   ```

2. **Verify Repository Structure**:
   Ensure your repository contains:
   - `package.json` with build scripts
   - `netlify.toml` configuration file
   - `astro.config.mjs` with correct site URL
   - All source files in `src/` directory

### Step 2: Netlify Site Creation

1. **Login to Netlify**:
   - Visit [netlify.com](https://netlify.com)
   - Sign in with your preferred method

2. **Create New Site**:
   - Click "Add new site" → "Import an existing project"
   - Choose your Git provider (GitHub, GitLab, Bitbucket)
   - Authorize Netlify to access your repositories
   - Select the Yubea Labs website repository

3. **Configure Build Settings**:
   ```
   Build command: npm run build
   Publish directory: dist
   ```

4. **Deploy Site**:
   - Click "Deploy site"
   - Wait for initial build to complete (typically 2-3 minutes)

### Step 3: Domain Configuration

1. **Custom Domain Setup**:
   - In Netlify dashboard, go to "Domain settings"
   - Click "Add custom domain"
   - Enter your domain (e.g., `yubealabs.com`)
   - Follow DNS configuration instructions

2. **SSL Certificate**:
   - Netlify automatically provisions SSL certificates
   - Verify HTTPS is working after domain propagation

3. **Update Site Configuration**:
   ```javascript
   // astro.config.mjs
   export default defineConfig({
     site: 'https://yubealabs.com', // Update with your domain
     // ... other config
   });
   ```

### Step 4: Form Configuration

1. **Verify Form Detection**:
   - Check Netlify dashboard under "Forms"
   - Ensure both forms are detected:
     - `contact` form from `/contact` page
     - `lead-magnet` form from `/lead-magnet` page

2. **Form Notifications**:
   - Go to "Forms" → "Notifications"
   - Set up email notifications for form submissions
   - Configure Slack/webhook integrations if needed

3. **Spam Protection**:
   - Enable Akismet spam filtering (optional)
   - Set up honeypot fields if needed

### Step 5: Performance Optimization

1. **Asset Optimization**:
   - Netlify automatically optimizes images
   - Enable "Asset optimization" in site settings
   - Configure compression settings

2. **CDN Configuration**:
   - Netlify CDN is enabled by default
   - Verify global distribution is working

3. **Caching Headers**:
   ```toml
   # netlify.toml
   [[headers]]
     for = "/*"
     [headers.values]
       Cache-Control = "public, max-age=31536000"
   
   [[headers]]
     for = "/*.html"
     [headers.values]
       Cache-Control = "public, max-age=0, must-revalidate"
   ```

## 🔧 Environment Configuration

### Production Environment Variables

If you need environment variables:

1. **Netlify Dashboard**:
   - Go to "Site settings" → "Environment variables"
   - Add variables as needed

2. **Build Context**:
   ```toml
   # netlify.toml
   [context.production.environment]
     NODE_ENV = "production"
   ```

### Branch Deployments

1. **Preview Deployments**:
   - Netlify automatically creates preview deployments for pull requests
   - Configure branch deploy settings in site settings

2. **Branch-specific Configuration**:
   ```toml
   # netlify.toml
   [context.branch-deploy]
     command = "npm run build"
   
   [context.deploy-preview]
     command = "npm run build"
   ```

## 📊 Monitoring & Analytics

### Build Monitoring

1. **Build Notifications**:
   - Set up build failure notifications
   - Configure success notifications if desired

2. **Build Logs**:
   - Monitor build logs for errors
   - Set up log retention policies

### Performance Monitoring

1. **Lighthouse Scores**:
   - Use Netlify's built-in Lighthouse integration
   - Monitor Core Web Vitals

2. **Analytics Integration**:
   ```html
   <!-- Add to Layout.astro head section -->
   <!-- Google Analytics -->
   <script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
   <script>
     window.dataLayer = window.dataLayer || [];
     function gtag(){dataLayer.push(arguments);}
     gtag('js', new Date());
     gtag('config', 'GA_MEASUREMENT_ID');
   </script>
   ```

## 🔄 Continuous Deployment

### Automatic Deployments

1. **Git Integration**:
   - Pushes to main branch trigger automatic deployments
   - Configure branch deployment settings

2. **Build Hooks**:
   - Set up webhook URLs for external triggers
   - Use for CMS integrations or scheduled rebuilds

### Manual Deployments

1. **Drag & Drop**:
   - Build locally: `npm run build`
   - Drag `dist` folder to Netlify dashboard

2. **CLI Deployment**:
   ```bash
   # Install Netlify CLI
   npm install -g netlify-cli
   
   # Login and deploy
   netlify login
   netlify deploy --prod --dir=dist
   ```

## 🛡️ Security Configuration

### Headers Configuration

```toml
# netlify.toml
[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-XSS-Protection = "1; mode=block"
    X-Content-Type-Options = "nosniff"
    Referrer-Policy = "strict-origin-when-cross-origin"
    Content-Security-Policy = "default-src 'self'; script-src 'self' 'unsafe-inline' https://www.googletagmanager.com; style-src 'self' 'unsafe-inline'; img-src 'self' data: https:; font-src 'self' https://fonts.gstatic.com;"
```

### Form Security

1. **Spam Protection**:
   - Enable Netlify's built-in spam filtering
   - Add honeypot fields to forms

2. **Rate Limiting**:
   - Configure submission rate limits
   - Set up IP-based restrictions if needed

## 🔍 SEO Configuration

### Search Console Setup

1. **Google Search Console**:
   - Add and verify your domain
   - Submit sitemap: `https://yubealabs.com/sitemap.xml`

2. **Bing Webmaster Tools**:
   - Add and verify your site
   - Submit sitemap for Bing indexing

### Sitemap Updates

1. **Automatic Updates**:
   - Sitemap is static but can be automated
   - Consider using Astro sitemap integration for dynamic updates

2. **Manual Updates**:
   - Update `/public/sitemap.xml` when adding new pages
   - Resubmit to search engines after changes

## 🚨 Troubleshooting

### Common Deployment Issues

1. **Build Failures**:
   ```bash
   # Check Node.js version
   node --version  # Should be 18+
   
   # Clear cache and rebuild
   rm -rf node_modules package-lock.json
   npm install
   npm run build
   ```

2. **Form Submission Issues**:
   - Verify `data-netlify="true"` attribute
   - Check form names match Netlify dashboard
   - Ensure proper form encoding

3. **Asset Loading Issues**:
   - Check asset paths are relative
   - Verify public folder structure
   - Test with `npm run preview`

### Performance Issues

1. **Slow Loading**:
   - Optimize images before upload
   - Enable Netlify asset optimization
   - Check for large JavaScript bundles

2. **Build Timeouts**:
   - Increase build timeout in Netlify settings
   - Optimize build process
   - Consider build caching

## 📞 Support Resources

### Documentation
- [Netlify Documentation](https://docs.netlify.com/)
- [Astro Documentation](https://docs.astro.build/)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)

### Community Support
- [Netlify Community](https://community.netlify.com/)
- [Astro Discord](https://astro.build/chat)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/netlify)

### Professional Support
- Netlify Pro/Business plans include priority support
- Consider hiring Jamstack specialists for complex customizations

---

## 📋 Deployment Checklist

Before going live:

- [ ] Repository is properly configured and pushed
- [ ] Build succeeds locally with `npm run build`
- [ ] All forms are working and detected by Netlify
- [ ] Custom domain is configured and SSL is active
- [ ] Analytics tracking is implemented
- [ ] SEO meta tags are properly configured
- [ ] Sitemap is submitted to search engines
- [ ] Performance scores are acceptable (Lighthouse)
- [ ] All pages load correctly on mobile and desktop
- [ ] Contact information is accurate
- [ ] Legal pages are included if required
- [ ] Backup and monitoring systems are in place

---

*This deployment guide ensures a smooth launch of the Yubea Labs website with optimal performance, security, and maintainability.*

