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
