# HTML to React JSX Conversion Guide

## Project Overview

This project has been converted from a static HTML template (Sattiyas - Fashion & Jewelry eCommerce) to a React application using Vite and React Router.

## Project Structure

```
src/
├── components/          # Reusable React components
│   ├── Header.jsx       # Site header with navigation
│   ├── Footer.jsx       # Site footer
│   ├── Preloader.jsx    # Loading animation
│   ├── ScrollToTop.jsx  # Scroll to top button
│   └── ProductCard.jsx  # Product card component
├── pages/               # Page components
│   ├── Home.jsx         # Home page
│   ├── Shop.jsx         # Shop/Products page
│   ├── ProductDetails.jsx # Product detail page
│   ├── About.jsx        # About page
│   ├── Contact.jsx      # Contact page
│   └── ...              # Other pages (Cart, Checkout, etc.)
├── layouts/             # Layout components
│   └── MainLayout.jsx   # Main layout with header/footer
├── data/                # Data files
│   └── products.js      # Product data
├── App.jsx              # Main app with routing
├── main.jsx             # App entry point
└── index.css            # Global styles
```

## Key Changes from HTML to JSX

### 1. HTML Class Attributes
- **HTML:** `class="container"`
- **JSX:** `className="container"`

### 2. Self-Closing Tags
- **HTML:** `<img src="image.jpg">`
- **JSX:** `<img src="image.jpg" />`

### 3. Links
- **HTML:** `<a href="page.html">Link</a>`
- **JSX:** `<Link to="/page">Link</Link>` (using React Router)

### 4. Inline Styles
- **HTML:** `style="color: red;"`
- **JSX:** `style={{ color: 'red' }}`

### 5. Event Handlers
- **HTML:** `onclick="handleClick()"`
- **JSX:** `onClick={handleClick}`

### 6. SVG Attributes
- **HTML:** `stroke-width`
- **JSX:** `strokeWidth` (camelCase)

## Running the Application

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Available Routes

- `/` - Home page
- `/shop` - Product listing
- `/shop-sidebar` - Shop with sidebar
- `/product-details/:slug` - Product details (dynamic)
- `/about` - About page
- `/contact` - Contact page
- `/cart` - Shopping cart
- `/checkout` - Checkout page
- `/wishlist` - Wishlist
- `/blog` - Blog listing
- `/blog-details` - Blog post details
- `/success` - Order success page
- `/home-v2` - Alternative home page (Fashion V2)
- `/home-v3` - Alternative home page (Jewelry)

## Components Created

### Header
- Navigation menu with dropdowns
- Search functionality
- Cart icon
- Mobile menu toggle

### Footer
- Company information
- Quick links
- Contact information
- Social media links

### ProductCard
- Product image
- Product name and price
- Discount badge (if applicable)
- Quick actions (wishlist, view, add to cart)

### Preloader
- Animated loading screen
- Auto-dismisses after load

### ScrollToTop
- Floating button that appears on scroll
- Smooth scroll to top functionality

## CSS and Assets

The original CSS files from the HTML template are still used. Make sure the CSS files are properly linked in `index.html`:

```html
<link rel="stylesheet" href="assets/css/bootstrap.min.css">
<link rel="stylesheet" href="assets/css/fontawesome.min.css">
<link rel="stylesheet" href="assets/css/slick.css">
<link rel="stylesheet" href="assets/css/style.css">
```

## Next Steps

1. **Complete remaining pages:** Convert Cart, Checkout, Wishlist, Blog pages
2. **Add state management:** Implement cart functionality with Context API or Redux
3. **API integration:** Connect to a real backend for products and orders
4. **Form validation:** Add proper form validation for contact and checkout
5. **Image optimization:** Optimize images for better performance
6. **SEO optimization:** Add meta tags and proper heading structure

## Notes

- The application uses the existing CSS from the HTML template
- Product data is currently mocked in `src/data/products.js`
- Images are referenced from the `public/assets/img/` directory
- Font Awesome icons are used throughout the application

## Development Tips

1. Use React DevTools for debugging
2. Check browser console for any warnings or errors
3. Ensure all image paths are correct
4. Test responsive design on different screen sizes
5. Use ESLint to catch potential issues

## Troubleshooting

If you encounter issues:

1. Clear browser cache
2. Delete `node_modules` and run `npm install` again
3. Check that all import paths are correct
4. Ensure CSS files are properly loaded
5. Verify that React Router is properly configured