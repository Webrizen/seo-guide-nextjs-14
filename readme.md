# Repository Guide for Advanced SEO in Next.js 14

Welcome to the **Advanced SEO Guide for Next.js 14**! This repository is dedicated to helping you configure SEO for your Next.js website with a focus on using the latest features available in Next.js 14. Throughout this guide, you will find step-by-step instructions and best practices for setting up basic to advanced SEO metadata, optimizing Open Graph and Twitter Cards, implementing structured data, and configuring advanced settings for enhanced visibility on search engines and social media.

In this initial phase, we’ll cover the **setup of basic metadata**—the essential tags that ensure your Next.js pages are well-optimized for search engine indexing and display properly on social media. 

### Phase 1: Setting Up Basic Metadata

#### Why Basic Metadata is Important
Basic metadata includes essential tags such as the **title**, **meta description**, **keywords**, and **Open Graph data**. These tags provide search engines and social media platforms with information about your website’s content, helping to increase visibility, improve click-through rates, and ensure your content is displayed attractively across various platforms.

#### Getting Started with Basic Metadata in Next.js 14

In Next.js 14, we use the `metadata` API to define metadata for individual pages directly in each `page.js` or `page.tsx` file. This allows for a clean, scalable approach to handling SEO metadata across your site.

1. **Create or Edit Metadata in `page.js`**

   In each page file, define the `metadata` object. This is where you’ll include all the essential metadata properties.

   ```jsx
   // app/layout.tsx or app/any-page

   export const metadata = {
     title: "Home | Academy",
     description:
       "Academy is a leading Educational coaching institute in Patna, dedicated to providing high-quality education and guidance for UPSC aspirants.",
     keywords: [
       "Educational coaching in Patna",
       "UPSC preparation",
       "Best Educational coaching Bihar",
       "Civil Services Exam preparation",
       "UPSC coaching institute",
     ],
   };
   ```

   **Explanation:**
   - `title`: The main title of your page, ideally around 50-60 characters. For SEO, include primary keywords and your brand name.
   - `description`: A concise summary of the page (under 160 characters) to appear in search results.
   - `keywords`: An array of keywords related to your page content (optional but useful for certain search engines).

2. **Set Default Title and Description Templates**

   To make your metadata consistent and dynamic, use templates for the `title` and `description`. This is especially useful when you have multiple pages that share similar content structures.

   ```jsx
   export const metadata = {
     title: {
       default: "Academy",
       template: "%s | Academy",
     },
     description: {
       default:
         "Academy is a top-rated Educational coaching institute in Patna, offering quality education and expert guidance.",
       template: "%s | Academy",
     },
   };
   ```

   **Explanation:**
   - **Default Titles and Descriptions**: The `default` property sets the default title and description for pages without a specific entry.
   - **Template Strings**: Use `%s` in `template` strings to dynamically replace this placeholder with the specific page title or description. This keeps titles consistent and optimized across the site.

3. **Add Open Graph (OG) Tags for Social Media**

   Open Graph metadata controls how your pages appear when shared on social media platforms like Facebook, LinkedIn, and Twitter. To set Open Graph metadata, add the `openGraph` field to the `metadata` object.

   ```jsx
   export const metadata = {
     openGraph: {
       type: "website",
       url: "https://Academyacademy.com",
       title: "Academy",
       description:
         "A premier Educational coaching institute in Patna, providing guidance and resources for UPSC aspirants.",
       images: [
         {
           url: "https://Academyacademy.com/logo.png",
           width: 500,
           height: 500,
           alt: "Academy Logo",
         },
       ],
       site_name: "Academy",
     },
   };
   ```

   **Explanation:**
   - **type**: The type of object, usually set as `website` for general web pages.
   - **url**: The canonical URL of the page.
   - **title & description**: Reuse your page title and description to ensure consistency across social media platforms.
   - **images**: Specify an image to display in the preview. Include the image’s `width`, `height`, and `alt` attributes for best results.

4. **Twitter Card Setup**

   Twitter Cards allow you to control how your pages look when shared on Twitter. The `card` property determines the card style (e.g., `summary_large_image` for a large preview).

   ```jsx
   export const metadata = {
     twitter: {
       card: "summary_large_image",
       site: "@Academy",
       title: "Academy",
       description:
         "Join Academy to kickstart your Educational journey with quality coaching and guidance.",
       images: ["https://Academyacademy.com/logo.png"],
     },
   };
   ```

   **Explanation:**
   - **card**: Choose the Twitter Card type (`summary_large_image` for a large image preview).
   - **site**: Add your Twitter handle to reinforce your brand identity.
   - **title & description**: Set these to match your page’s title and description.
   - **images**: Provide a URL for an image to appear in the Twitter preview.

5. **Setting Robots Metadata for Crawling**

   Use the `robots` field to control how search engines interact with your page.

   ```jsx
   export const metadata = {
     robots: {
       index: true,
       follow: true,
       nocache: true,
     },
   };
   ```

   **Explanation:**
   - **index**: Set to `true` to allow indexing.
   - **follow**: Set to `true` to allow crawlers to follow links on this page.
   - **nocache**: Instructs crawlers not to cache the page.

6. **Setting a Canonical URL**

   The canonical URL prevents duplicate content issues. Set it using the `alternates` field with `canonical`.

   ```jsx
   export const metadata = {
     alternates: {
       canonical: "https://Academyacademy.com",
     },
   };
   ```

   **Explanation**: The `canonical` URL helps search engines know the primary version of a page, avoiding penalties for duplicate content.

#### Complete Example of Basic Metadata Configuration

Here’s a consolidated example of the full basic metadata setup:

```jsx
export const metadata = {
  title: {
    default: "Academy",
    template: "%s | Academy",
  },
  description: {
    default:
      "Academy is a top-rated Educational coaching institute in Patna, offering quality education and expert guidance.",
    template: "%s | Academy",
  },
  keywords: [
    "Educational coaching in Patna",
    "UPSC preparation",
    "Civil Services Exam preparation",
    "Best Educational coaching Bihar",
  ],
  openGraph: {
    type: "website",
    url: "https://Academyacademy.com",
    title: "Academy",
    description:
      "Join Academy to kickstart your Educational journey with quality coaching and guidance.",
    images: [
      {
        url: "https://Academyacademy.com/logo.png",
        width: 500,
        height: 500,
        alt: "Academy Logo",
      },
    ],
    site_name: "Academy",
  },
  twitter: {
    card: "summary_large_image",
    site: "@Academy",
    title: "Academy",
    description:
      "Join Academy to kickstart your Educational journey with quality coaching and guidance.",
    images: ["https://Academyacademy.com/logo.png"],
  },
  robots: {
    index: true,
    follow: true,
    nocache: true,
  },
  alternates: {
    canonical: "https://Academyacademy.com",
  },
};
```

This setup will give your Next.js 14 website a solid foundation for SEO. By including these metadata fields, you ensure your pages are well-indexed by search engines and displayed attractively when shared across social media. In future phases, you’ll expand on this setup with structured data, advanced SEO settings, and other techniques to enhance visibility and engagement.

When setting up SEO metadata for a Next.js 14 website that includes **internationalization (i18n)**, you need to consider how metadata should vary across different languages. This approach ensures that each language version of your site is indexed correctly and accessible to users in their preferred language.

Here's a guide on handling basic metadata for internationalized Next.js 14 sites:

---

### Procedure for Adding Metadata with Internationalization in Next.js 14

1. **Install and Configure `next-intl` (or any i18n library)**

   To handle translations, you’ll first need to set up an i18n library, like `next-intl`, which is compatible with the Next.js 14 app router.

   ```bash
   npm install next-intl
   ```

2. **Configure `next-intl` in Your App**

   In your `app/layout.js` or `app/layout.tsx`, initialize `next-intl` for managing translations. Here’s a quick example:

   ```jsx
   import { NextIntlProvider } from 'next-intl';

   export default function Layout({ children }) {
     return (
       <NextIntlProvider messages={{ /* your translations */ }}>
         {children}
       </NextIntlProvider>
     );
   }
   ```

3. **Create Language-Specific Metadata Files**

   For each supported language, create a `messages` JSON file containing all translations for titles, descriptions, and other metadata fields.

   **Example: `messages/en.json`**
   ```json
   {
     "title": "Academy | Home",
     "description": "Academy is a leading Educational coaching institute in Patna.",
     "keywords": ["Educational coaching in Patna", "UPSC preparation", "Civil Services Exam"]
   }
   ```

   **Example: `messages/hi.json`**
   ```json
   {
     "title": "परिपूर्णता अकादमी | होम",
     "description": "परिपूर्णता अकादमी पटना में एक प्रमुख Educational कोचिंग संस्थान है।",
     "keywords": ["Educational कोचिंग पटना", "UPSC तैयारी", "सिविल सेवा परीक्षा"]
   }
   ```

4. **Define Metadata in `page.js` or `page.tsx` with Translations**

   Use `next-intl`'s `useTranslations` hook to access translations for titles, descriptions, and other metadata fields, then set them in the `metadata` object.

   ```jsx
   import { useTranslations } from 'next-intl';

   export const metadata = () => {
     const t = useTranslations();

     return {
       title: t('title'),
       description: t('description'),
       keywords: t('keywords'),
       openGraph: {
         title: t('title'),
         description: t('description'),
         images: [
           {
             url: "/logo.png",
             width: 500,
             height: 500,
             alt: t('title'),
           },
         ],
         site_name: "Academy",
       },
       twitter: {
         card: "summary_large_image",
         title: t('title'),
         description: t('description'),
         images: ["/logo.png"],
       },
       alternates: {
         canonical: "https://Academyacademy.com",
         languages: {
           en: "https://Academyacademy.com/en",
           hi: "https://Academyacademy.com/hi",
         },
       },
     };
   };
   ```

5. **Specify Language-Specific Canonical URLs in Metadata**

   Set up language-specific canonical URLs in the `alternates` field to let search engines know the different versions of your content.

   ```jsx
   alternates: {
     canonical: "https://Academyacademy.com",
     languages: {
       en: "https://Academyacademy.com/en",
       hi: "https://Academyacademy.com/hi",
     },
   },
   ```

6. **Render Metadata Dynamically Based on Locale**

   Ensure that the metadata is dynamically rendered according to the current locale. In Next.js, this can be set up so that when a user visits a specific language route (e.g., `/en` or `/hi`), the corresponding metadata will load for that language.

7. **Dynamic Routing for Localized Pages**

   Create language-specific routes in the `app` directory for different languages, allowing Next.js to automatically apply the correct metadata based on the locale.

   ```plaintext
   app/
   ├── en/
   │   └── page.js  // English page with English metadata
   └── hi/
       └── page.js  // Hindi page with Hindi metadata
   ```

   In each language-specific page, import the respective translations and set metadata.

8. **Fallback for Untranslated Content**

   If a translation for a specific language is missing, you can set a fallback to the default language, such as English, to ensure continuity.

### Complete Example of Metadata with i18n

Here’s the consolidated example that incorporates `next-intl` with Next.js 14 metadata configuration:

```jsx
import { useTranslations } from 'next-intl';

export const metadata = () => {
  const t = useTranslations();

  return {
    title: t('title'),
    description: t('description'),
    keywords: t('keywords'),
    openGraph: {
      type: "website",
      url: "https://Academyacademy.com",
      title: t('title'),
      description: t('description'),
      images: [
        {
          url: "https://Academyacademy.com/logo.png",
          width: 500,
          height: 500,
          alt: t('title'),
        },
      ],
      site_name: "Academy",
    },
    twitter: {
      card: "summary_large_image",
      title: t('title'),
      description: t('description'),
      images: ["https://Academyacademy.com/logo.png"],
    },
    alternates: {
      canonical: "https://Academyacademy.com",
      languages: {
        en: "https://Academyacademy.com/en",
        hi: "https://Academyacademy.com/hi",
      },
    },
  };
};
```

### Key Takeaways

- **Localized Metadata**: Ensure each page has metadata in the appropriate language by using `next-intl` translations.
- **Canonical URLs for Languages**: Use `alternates` to specify language-specific canonical URLs, aiding search engines in understanding language variants.
- **Dynamic Routes for Localized Pages**: Structure your `app` directory to support dynamic language-based routing for better organization and SEO.

By following this approach, you can effectively manage internationalized metadata across different language versions of your Next.js 14 website, ensuring SEO and user experience are optimized for a global audience.

---

# Phase 2: Manifest.json

Here’s a guide on setting up the `manifest.json` file for both internationalized and non-internationalized Next.js 14 sites. The `manifest.json` file is essential for defining your web app’s properties, especially when aiming for Progressive Web App (PWA) support.

### 1. **Manifest for Non-Internationalized Next.js 14 Site**

For a standard (non-internationalized) Next.js 14 site, you’ll need a single `manifest.json` file. This file will provide general information about your application.

#### `manifest.json`

```json
{
  "name": "Academy",
  "short_name": "Academy",
  "description": "Academy is a top-rated IAS coaching institute in Patna, offering high-quality education and guidance for UPSC aspirants.",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#ffffff",
  "orientation": "portrait-primary",
  "scope": "/",
  "icons": [
    {
      "src": "/icons/icon-192x192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "/icons/icon-512x512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ],
  "screenshots": [
    {
      "src": "/screenshots/screenshot1.png",
      "sizes": "1080x1920",
      "type": "image/png",
      "label": "Homepage"
    },
    {
      "src": "/screenshots/screenshot2.png",
      "sizes": "1080x1920",
      "type": "image/png",
      "label": "Courses"
    }
  ],
  "lang": "en"
}
```

#### Explanation of Key Fields:

- **name**: Full name of the application.
- **short_name**: A shorter name for display purposes (like on the home screen).
- **description**: A brief description of your application.
- **start_url**: Specifies the initial URL the app opens to.
- **display**: Defines the display mode (e.g., `standalone` for PWA).
- **background_color** and **theme_color**: Set branding colors for the splash screen and address bar.
- **orientation**: Locks the app orientation; here, it’s set to `portrait-primary`.
- **icons**: An array of icons for various device sizes.
- **screenshots**: Optional, provides screenshots of the app for richer results in some search engines.
- **lang**: Sets the default language for the application (e.g., "en" for English).

---

### 2. **Manifest for Internationalized Next.js 14 Site**

For an internationalized Next.js 14 site, you need separate `manifest.json` files for each language, allowing you to define language-specific names, descriptions, and start URLs.

#### Directory Structure

Organize your manifest files in a structure like this:

```plaintext
public/
├── manifest.en.json
├── manifest.hi.json
└── icons/
    ├── icon-192x192.png
    └── icon-512x512.png
```

#### `manifest.en.json` (for English)

```json
{
  "name": "Academy",
  "short_name": "Academy",
  "description": "Academy is a top-rated IAS coaching institute in Patna, offering high-quality education and guidance for UPSC aspirants.",
  "start_url": "/en",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#ffffff",
  "orientation": "portrait-primary",
  "scope": "/en",
  "icons": [
    {
      "src": "/icons/icon-192x192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "/icons/icon-512x512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ],
  "lang": "en"
}
```

#### `manifest.hi.json` (for Hindi)

```json
{
  "name": "प्रयास IAS अकादमी",
  "short_name": "प्रयास IAS",
  "description": "प्रयास IAS अकादमी पटना में एक प्रमुख IAS कोचिंग संस्थान है, जो UPSC उम्मीदवारों के लिए उच्च गुणवत्ता वाली शिक्षा और मार्गदर्शन प्रदान करता है।",
  "start_url": "/hi",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#ffffff",
  "orientation": "portrait-primary",
  "scope": "/hi",
  "icons": [
    {
      "src": "/icons/icon-192x192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "/icons/icon-512x512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ],
  "lang": "hi"
}
```

#### Explanation of Key Differences

- **name** and **description**: Localized for each language.
- **start_url** and **scope**: Begin with the language prefix (e.g., `/en` for English, `/hi` for Hindi).
- **lang**: Specifies the language code to indicate the language version of the manifest.

#### Implementation in Next.js

1. **Dynamic Selection of Manifest File**: Set up your Next.js app to dynamically serve the appropriate `manifest.json` file based on the user’s selected language.

2. **Linking Manifest Files in `app/layout.js`**

   Use a helper function to select the correct manifest based on the locale. Here’s an example:

   ```jsx
   import { useLocale } from 'next-intl';

   export default function Layout({ children }) {
     const locale = useLocale();
     const manifestUrl = locale === 'hi' ? '/manifest.hi.json' : '/manifest.en.json';

     return (
       <>
         <link rel="manifest" href={manifestUrl} />
         {children}
       </>
     );
   }
   ```

3. **Managing Caching and Routing**: Ensure the `manifest.json` files are cached correctly by configuring your server or CDN settings, so users get the right language manifest when they change languages.

---

By following these steps, your internationalized Next.js 14 site can dynamically serve language-specific `manifest.json` files, providing a tailored experience for each language version.

---

# Phase 3: Robots.tsx

Here’s a guide on setting up the `robots.txt` file for both **internationalized** and **non-internationalized** Next.js 14 sites. The `robots.txt` file is essential for controlling how search engines crawl and index your site, and it can be tailored to handle multiple languages for internationalized sites.

---

### 1. **`robots.txt` for Non-Internationalized Next.js 14 Site**

For a non-internationalized site, a single `robots.txt` file will suffice.

#### `robots.txt`

```plaintext
# Allow all web crawlers access to the entire site
User-agent: *
Disallow:

# Specify the location of the sitemap
Sitemap: https://academy.com/sitemap.xml
```

#### Explanation:
- **User-agent**: `*` means all crawlers are allowed.
- **Disallow**: Empty, allowing all pages to be crawled.
- **Sitemap**: Specifies the location of the sitemap to help search engines crawl your site effectively.

---

### 2. **`robots.txt` for Internationalized Next.js 14 Site**

For an internationalized site, it’s essential to specify language-specific rules and sitemaps for each locale. This ensures that search engines correctly understand and index the different language versions of your site.

#### Directory Structure (Example)

Organize the language-specific `robots.txt` files as follows:

```plaintext
public/
├── robots.en.txt
└── robots.hi.txt
```

#### `robots.en.txt` (for English)

```plaintext
# Allow all web crawlers access to the English version of the site
User-agent: *
Disallow:

# Specify the English sitemap
Sitemap: https://academy.com/en/sitemap.xml
```

#### `robots.hi.txt` (for Hindi)

```plaintext
# Allow all web crawlers access to the Hindi version of the site
User-agent: *
Disallow:

# Specify the Hindi sitemap
Sitemap: https://academy.com/hi/sitemap.xml
```

#### Explanation:

- **Language-Specific Sitemaps**: Direct search engines to language-specific sitemaps (`/en/sitemap.xml` and `/hi/sitemap.xml`) to improve indexing.
- **Separate `robots.txt` Files**: Different files for each language ensure accurate instructions for each locale, improving visibility and preventing indexing issues.

---

### Serving the Correct `robots.txt` File in Next.js

You can configure Next.js to dynamically serve the appropriate `robots.txt` file based on the user's selected language.

1. **Dynamic Routing of `robots.txt` File**

   In Next.js, you can set up a dynamic API route that serves different `robots.txt` files based on the locale.

   - **Create an API Route**: In your `pages/api/` directory, create `robots.js`.

   ```javascript
   // pages/api/robots.js

   export default function handler(req, res) {
     const { locale } = req.query;

     if (locale === 'hi') {
       res.setHeader('Content-Type', 'text/plain');
       res.send(`# Hindi robots.txt
User-agent: *
Disallow:

Sitemap: https://academy.com/hi/sitemap.xml`);
     } else {
       res.setHeader('Content-Type', 'text/plain');
       res.send(`# English robots.txt
User-agent: *
Disallow:

Sitemap: https://academy.com/en/sitemap.xml`);
     }
   }
   ```

2. **Update the `robots.txt` Link in Your Layout**

   In `app/layout.js`, conditionally set the URL for `robots.txt` based on the locale.

   ```jsx
   import { useLocale } from 'next-intl';

   export default function Layout({ children }) {
     const locale = useLocale();
     const robotsUrl = `/api/robots?locale=${locale}`;

     return (
       <>
         <link rel="robots" href={robotsUrl} />
         {children}
       </>
     );
   }
   ```

This setup will ensure that your Next.js 14 site serves the correct `robots.txt` file depending on the user's language, making it easier for search engines to correctly index each language version.

---

# Phase 4: Sitemaps

---

### 1. **Sitemap Generation for Non-Internationalized Next.js 14 Site**

In an app router-only setup, you can create a single API route in the `app/api` directory for generating the sitemap.

#### Step 1: Install the `sitemap` Package

First, install the `sitemap` package for generating your sitemap.

```bash
npm install sitemap
```

#### Step 2: Create the Sitemap API Route in the `app/api` Directory

In the `app/api` directory, create a `sitemap` route with `route.js` to generate the sitemap dynamically.

```javascript
// app/api/sitemap/route.js
import { SitemapStream, streamToPromise } from 'sitemap';
import { NextResponse } from 'next/server';

export async function GET() {
  const smStream = new SitemapStream({ hostname: 'https://academy.com' });

  // Define static paths
  const staticPaths = ['', 'about', 'contact', 'courses']; // Add your static routes here

  // Add static routes to the sitemap
  staticPaths.forEach((path) => {
    smStream.write({ url: `/${path}`, changefreq: 'weekly', priority: 0.8 });
  });

  // Add dynamic routes from your database or CMS
  const blogPosts = await fetchBlogPosts(); // Fetch blog post slugs from your CMS or database
  blogPosts.forEach((post) => {
    smStream.write({ url: `/blog/${post.slug}`, changefreq: 'weekly', priority: 0.8 });
  });

  smStream.end();
  const sitemap = await streamToPromise(smStream);
  return new NextResponse(sitemap.toString(), { headers: { 'Content-Type': 'application/xml' } });
}
```

- **Static Paths**: Add your main static routes directly in the API route.
- **Dynamic Paths**: Fetch dynamic slugs (e.g., blog posts, products) from your database or CMS.

#### Step 3: Access and Submit the Sitemap

The sitemap will be available at `/api/sitemap`. You can submit `https://academy.com/api/sitemap` to search engines.

---

### 2. **Sitemap Generation for Internationalized Next.js 14 Site**

For an internationalized site, you need separate API routes to generate sitemaps for each language.

#### Step 1: Create Multiple API Routes for Different Languages

Set up separate routes for each language in the `app/api` directory.

1. **English Sitemap**: `app/api/sitemap-en/route.js`
2. **Hindi Sitemap**: `app/api/sitemap-hi/route.js`

#### Example: `app/api/sitemap-en/route.js`

```javascript
import { SitemapStream, streamToPromise } from 'sitemap';
import { NextResponse } from 'next/server';

export async function GET() {
  const smStream = new SitemapStream({ hostname: 'https://academy.com/en' });

  // Define English static paths
  const staticPaths = ['', 'about', 'contact', 'courses'];

  staticPaths.forEach((path) => {
    smStream.write({ url: `/en/${path}`, changefreq: 'weekly', priority: 0.8 });
  });

  // Add dynamic routes for English content
  const blogPosts = await fetchBlogPosts('en');
  blogPosts.forEach((post) => {
    smStream.write({ url: `/en/blog/${post.slug}`, changefreq: 'weekly', priority: 0.8 });
  });

  smStream.end();
  const sitemap = await streamToPromise(smStream);
  return new NextResponse(sitemap.toString(), { headers: { 'Content-Type': 'application/xml' } });
}
```

#### Example: `app/api/sitemap-hi/route.js`

```javascript
import { SitemapStream, streamToPromise } from 'sitemap';
import { NextResponse } from 'next/server';

export async function GET() {
  const smStream = new SitemapStream({ hostname: 'https://academy.com/hi' });

  // Define Hindi static paths
  const staticPaths = ['', 'about', 'contact', 'courses'];

  staticPaths.forEach((path) => {
    smStream.write({ url: `/hi/${path}`, changefreq: 'weekly', priority: 0.8 });
  });

  // Add dynamic routes for Hindi content
  const blogPosts = await fetchBlogPosts('hi');
  blogPosts.forEach((post) => {
    smStream.write({ url: `/hi/blog/${post.slug}`, changefreq: 'weekly', priority: 0.8 });
  });

  smStream.end();
  const sitemap = await streamToPromise(smStream);
  return new NextResponse(sitemap.toString(), { headers: { 'Content-Type': 'application/xml' } });
}
```

#### Step 3: Access and Submit Each Sitemap

- **English Sitemap**: `/api/sitemap-en`
- **Hindi Sitemap**: `/api/sitemap-hi`

Submit both URLs to search engines for indexing.

---

### 3. **Keeping the Sitemap Updated for New Slugs**

To keep your sitemap up-to-date with new routes in the Next.js 14 app router:

1. **Fetch Dynamic Data on Each Request**: The sitemap API routes fetch data dynamically from your database or CMS each time they are called. This ensures that new slugs are automatically included without manual updates.

2. **On-Demand Revalidation**: Use on-demand revalidation to keep your sitemap accurate when new content is published.

   ```javascript
   // app/api/revalidate-sitemap/route.js
   import { NextResponse } from 'next/server';

   export async function GET(req) {
     try {
       await res.revalidate('/api/sitemap');
       await res.revalidate('/api/sitemap-en');
       await res.revalidate('/api/sitemap-hi');
       return NextResponse.json({ revalidated: true });
     } catch (err) {
       return NextResponse.json({ revalidated: false, error: err });
     }
   }
   ```

3. **Automate Revalidation via Webhook**: Configure your CMS to call the revalidation endpoint whenever new content is published or updated, ensuring that the sitemap always reflects the latest data.

4. **Incremental Static Regeneration (ISR)**: Use ISR for static pages that are frequently updated, so the sitemap fetches up-to-date slugs when requested.

---

This setup enables you to dynamically generate and manage sitemaps in a Next.js 14 app router-only site, with separate sitemaps for each language version for internationalized sites. By dynamically fetching routes and using revalidation, your sitemaps remain current without manual intervention.


Your setup is almost complete! Here’s a quick checklist to ensure everything is in place and that your **Next.js 14 site** is fully optimized for SEO and indexing:

---

### Final Checklist for SEO and Sitemap Configuration in Next.js 14

1. **Metadata and Open Graph Tags**:
   - [x] **Title & Description**: Ensure each page has a unique title and meta description, leveraging templates where possible.
   - [x] **Open Graph (OG) Tags**: Set up OG tags for social sharing, including image previews for each language if using internationalization.
   - [x] **Twitter Cards**: Set up Twitter Card metadata for better display on Twitter.

2. **`robots.txt` File**:
   - [x] **Single `robots.txt` for Non-i18n Sites**: Ensure it points to the main sitemap.
   - [x] **Language-Specific `robots.txt` for i18n Sites**: Directs search engines to the correct language-specific sitemaps.

3. **Sitemap Configuration**:
   - [x] **Sitemap Generation API Route**: Create a dynamic API route to generate the sitemap based on available routes and content.
   - [x] **Internationalized Sitemaps**: If you have multiple languages, generate separate sitemaps for each language.
   - [x] **Revalidation for Dynamic Updates**: Implement revalidation to ensure new content is reflected in the sitemap immediately after publishing.

4. **PWA & Manifest File**:
   - [x] **Manifest for Non-i18n Sites**: Basic `manifest.json` file with icons, display, and theme color.
   - [x] **Localized Manifests for i18n Sites**: Separate `manifest` files for each language, with language-specific `name`, `short_name`, and `start_url`.

5. **Structured Data (Schema Markup)**:
   - [ ] **Add JSON-LD Structured Data**: Use schema markup (like `WebPage`, `Organization`, `Article`, or `Product`) for key pages to improve visibility in search results.
   - **Note**: Add schema markup directly in the `metadata` objects in Next.js 14 for important pages, such as blog posts, courses, or the home page. This can enhance your site's rich result eligibility on Google.

6. **Internationalization (i18n)**:
   - [x] **Locale-Specific Canonical URLs**: Ensure each language version has a unique canonical URL to avoid duplicate content issues.
   - [x] **Localized Metadata**: Implement language-specific titles, descriptions, and keywords for each page using `next-intl` or similar.

7. **Other Technical SEO Practices**:
   - [x] **Page Speed Optimization**: Use Next.js image optimization (`next/image`), lazy loading, and caching strategies to improve page speed.
   - [x] **Core Web Vitals**: Regularly check and optimize Core Web Vitals (LCP, FID, CLS) to improve user experience and SEO ranking.
   - [x] **Mobile Responsiveness**: Ensure that the site is fully responsive, as mobile-friendliness is a ranking factor.

---

### Additional Tips

- **Webmaster Tools Submission**: Submit your sitemap to **Google Search Console**, **Bing Webmaster Tools**, and **other search engines** to speed up indexing.
- **Monitor Site Performance**: Regularly monitor your site’s indexing status, crawl errors, and search performance in Google Search Console.
- **Testing and Validation**:
  - **Structured Data Testing Tool**: Use Google’s [Rich Results Test](https://search.google.com/test/rich-results) to validate JSON-LD structured data.
  - **robots.txt Validator**: Test your `robots.txt` file for correctness.
  - **PageSpeed Insights**: Use [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) to analyze and optimize page speed, especially for mobile users.

---

With all these elements in place, your Next.js 14 site should be well-optimized for SEO, accessible to search engines, and ready for indexing in multiple languages if you’re using i18n. This setup ensures that your site not only ranks well but also provides a seamless experience for users across different languages and devices.
