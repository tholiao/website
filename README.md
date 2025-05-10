# Thomas Liao's Website

This is the source code to Thomas Liao's public academic website: https://thomasliao.com. It is modified from Jon Barron's website at https://jonbarron.info/. You are welcome to clone this code for your own personal use, just please attribute the source to the original website or to this repo. If you do clone this website, feel free to add an attribution link to your own downstream website in index.html if you want.

## Blog Post Creation & Site Generation Runbook

### 1. Create a new blog post
1. Create a new Markdown file in the `_posts` directory
2. Name it using the format: `YYYY-MM-DD-title.md` (e.g., `2025-05-08-eval-startups.md`)
3. Add front matter at the top of the file:
   ```yaml
   ---
   layout: default     # or post (uses the post.html layout)
   title: "Your Post Title"
   permalink: /custom-url     # optional - creates a custom URL without date structure
   author: Your Name
   ---
   ```
4. Write your content below the front matter using Markdown

### 2. Build the site
1. Run `bundle exec jekyll build` to generate the site
2. The generated HTML files will be in the `_site` directory:
   - Files with a custom permalink will be at: `_site/custom-url.html`
   - Files without a permalink will follow Jekyll's default structure: `_site/YYYY/MM/DD/title.html`

### 3. Preview locally
1. Run `bundle exec jekyll serve` to start a local server
2. View your site at http://127.0.0.1:4000/
3. Use Ctrl+C to stop the server

### 4. Deploy
Push changes to GitHub for automatic deployment or follow your current deployment process.
