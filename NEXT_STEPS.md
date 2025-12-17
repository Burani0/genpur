# GenPur Strapi CMS - Next Steps Guide

## Current Status
- ✓ Strapi backend installation in progress
- ⏳ Installing dependencies (this may take 5-10 minutes)

## Once Installation Completes

### Step 1: Start Strapi Server

Open a terminal and run:
```bash
cd c:\Users\THINKPAD\OneDrive\Desktop\genpur\backend
npm run develop
```

This will:
- Build the admin panel
- Start the server on http://localhost:1337
- Automatically open the admin panel in your browser

###Step 2: Create Admin Account

When Strapi opens in your browser:
1. Fill in the form to create your first admin user:
   - First Name: (your name)
   - Last Name: (your name)
   - Email: (your email for login)
   - Password: (strong password - save this!)
2. Click "Let's start"

### Step 3: Create Content Types

#### A. Create Category Content Type

1. In the left sidebar, click **"Content-Type Builder"**
2. Click **"Create new collection type"**
3. Enter Display name: `Category`
4. Click **"Continue"**

5. Add fields:

   **Field 1 - Name:**
   - Click "Text"
   - Name: `name`
   - Type: Short text
   - Click "Advanced Settings"
   - Check "Required field"
   - Click "Finish"

   **Field 2 - Slug:**
   - Click "UID"
   - Name: `slug`
   - Attached field: name
   - Click "Finish"

   **Field 3 - Color:**
   - Click "Text"
   - Name: `color`
   - Type: Short text
   - Click "Finish"

6. Click **"Save"** (top right)
7. Wait for server to restart

#### B. Create Article Content Type

1. Click **"Create new collection type"**
2. Enter Display name: `Article`
3. Click **"Continue"**

4. Add fields one by one:

   **Field 1 - Title:**
   - Click "Text"
   - Name: `title`
   - Type: Short text
   - Check "Required field"
   - Click "Finish"

   **Field 2 - Slug:**
   - Click "UID"
   - Name: `slug`
   - Attached field: title
   - Click "Finish"

   **Field 3 - Excerpt:**
   - Click "Text"
   - Name: `excerpt`
   - Type: Long text
   - Click "Finish"

   **Field 4 - Content:**
   - Click "Rich text"
   - Name: `content`
   - Check "Required field"
   - Click "Finish"

   **Field 5 - Featured Image:**
   - Click "Media"
   - Name: `featuredImage`
   - Type: Single media
   - Check "Required field"
   - Click "Finish"

   **Field 6 - Published Date:**
   - Click "Date"
   - Name: `publishedDate`
   - Type: date
   - Check "Required field"
   - Click "Finish"

   **Field 7 - Author:**
   - Click "Text"
   - Name: `author`
   - Type: Short text
   - Click "Advanced Settings"
   - Default value: `GenPur CBO Team`
   - Click "Finish"

   **Field 8 - Category (Relation):**
   - Click "Relation"
   - Select "Category" from dropdown on right side
   - Select relation type: **Article has one Category** (left side: many to one)
   - Click "Finish"

   **Field 9 - CTA Text:**
   - Click "Text"
   - Name: `ctaText`
   - Type: Short text
   - Click "Advanced Settings"
   - Default value: `Help Us Create More Success Stories`
   - Click "Finish"

   **Field 10 - CTA Link:**
   - Click "Text"
   - Name: `ctaLink`
   - Type: Short text
   - Click "Advanced Settings"
   - Default value: `donate.html`
   - Click "Finish"

   **Field 11 - Meta Description:**
   - Click "Text"
   - Name: `metaDescription`
   - Type: Long text
   - Click "Finish"

5. Click **"Save"** (top right)
6. Wait for server to restart

### Step 4: Configure Permissions

1. In left sidebar, click **"Settings"**
2. Under "USERS & PERMISSIONS PLUGIN", click **"Roles"**
3. Click on **"Public"**

4. Find **"Article"** section:
   - Check: `find`
   - Check: `findOne`

5. Find **"Category"** section:
   - Check: `find`
   - Check: `findOne`

6. Click **"Save"** (top right)

### Step 5: Add Categories

1. In left sidebar, click **"Content Manager"**
2. Click **"Category"**
3. Click **"Create new entry"** (top right)

Create these categories:

**Category 1:**
- Name: `Success Stories`
- Slug: `success-stories` (auto-generated)
- Color: `#7bc143`
- Click **"Save"** then **"Publish"**

**Category 2:**
- Name: `Education`
- Slug: `education`
- Color: `#f39c12`
- Click **"Save"** then **"Publish"**

**Category 3:**
- Name: `Livelihood`
- Slug: `livelihood`
- Color: `#3498db`
- Click **"Save"** then **"Publish"**

### Step 6: Add Thomas's Article

1. Click **"Article"** in Content Manager
2. Click **"Create new entry"**

Fill in the fields:

- **Title**: `Overcoming Obstacles: Thomas's Bright Future in the Classroom and Beyond`
- **Slug**: (auto-generated: `overcoming-obstacles-thomas-s-bright-future-in-the-classroom-and-beyond`)
- **Excerpt**: `Meet Thomas, a remarkable 17-year-old who is redefining what's possible, proving that every child deserves the chance to shine.`
- **Content**: Copy the full article text from article4.html (the main content paragraphs)
- **Featured Image**: Click "Add more media" → Upload thomas4.jpg from your img folder
- **Published Date**: `2025-12-04`
- **Category**: Select "Success Stories"
- **Author**: `GenPur CBO Team` (already filled)
- **CTA Text**: `Help Us Create More Success Stories Like Thomas`
- **CTA Link**: `donate.html`
- **Meta Description**: `Read about Thomas's inspiring journey from facing challenges to thriving in school with GenPur's support`

Click **"Save"** then **"Publish"**

### Step 7: Test the API

Open your browser and go to:
```
http://localhost:1337/api/articles?populate=*
```

You should see JSON data with Thomas's article!

## Troubleshooting

**If Strapi won't start:**
```bash
cd c:\Users\THINKPAD\OneDrive\Desktop\genpur\backend
npm install
npm run build
npm run develop
```

**If you forget your admin password:**
- The easiest way is to create a new admin user by running the server and going to the registration page

**If API returns empty data:**
- Make sure articles are "Published" not "Draft"
- Check that permissions are set correctly for Public role

## What's Next After This

Once you've completed these steps, I'll help you with:
1. Updating the frontend (get-involved.html) to fetch articles from Strapi
2. Creating a dynamic article.html page
3. Testing the full integration
4. Deploying to production

## Keep This Terminal Open

Once you run `npm run develop`, keep that terminal window open. Strapi needs to run continuously for the website to fetch article data.

To stop Strapi: Press `Ctrl+C` in the terminal

To start again: Run `npm run develop` from the backend folder
