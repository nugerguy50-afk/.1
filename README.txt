ZOMBIE FRUIT FINDER — GITHUB PAGES IMAGE HOST

This package hosts your fruit JPGs using GitHub Pages. It does NOT require Python or a server window to stay open.

FILES
- index.html: optional visual gallery
- manifest.json: auto-generated list of all image filenames
- images/: fruit image files
- Zombie_Fruit_Finder_GitHub_Pages.lua: script configured for GitHub Pages (URL placeholder must be changed)

PUBLISH TO GITHUB PAGES
1. Sign in to https://github.com/ and create a NEW PUBLIC repository, for example: blox-fruit-images.
2. Open the new repository and choose Add file > Upload files.
3. Upload index.html, manifest.json, the images folder, and optionally this README.txt. Keep the images folder and filenames unchanged. You do NOT need to upload the Lua script; keep it on your computer.
4. Click Commit changes.
5. In the repository, open Settings > Pages.
6. Under Build and deployment, select Deploy from a branch; select branch main and folder /(root), then Save.
7. Wait for GitHub Pages to publish. Your site URL will look like:
   https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/
8. Open manifest.json at that address to check it works:
   https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/manifest.json

CONFIGURE LUA
1. Open Zombie_Fruit_Finder_GitHub_Pages.lua in a text editor.
2. Find this line:
   local IMAGE_SERVER = "https://YOUR-USERNAME.github.io/YOUR-REPOSITORY"
3. Replace it with your actual GitHub Pages base URL, without a trailing slash. Example:
   local IMAGE_SERVER = "https://sigmasboy.github.io/blox-fruit-images"
   (Example only; use your actual GitHub username and repository.)
4. Save and run the Lua script in your executor.

HOW IT WORKS
- The Lua script requests /manifest.json from GitHub Pages.
- The manifest in this package lists the included 42 images. If you add images later, upload them to images/ and add their filenames to manifest.json.
- It downloads any missing images from /images/FILENAME.jpg into the executor's local asset folder.
- It uses getcustomasset or getsynasset to display those local images in Roblox.
- Adding a new image to images/ and adding its filename to manifest.json makes it available to the script. The current script only maps fruit names that it knows in FRUIT_IMAGE_FILES; adding a completely new fruit name may also require adding a mapping in the Lua script.

IMPORTANT LIMITATIONS
- GitHub Pages is static hosting; it does not run code or generate a domain instantly. You must create the repository and enable Pages once.
- This is public hosting: anyone with the URL can view/download the images.
- The executor needs an HTTP request method, writefile, makefolder, and getcustomasset or getsynasset for automatic image downloading/loading. Ordinary Roblox ImageLabel URLs do not normally accept arbitrary external image URLs directly.
- The GitHub Pages URL will not work until you publish the repository and replace the placeholder in the Lua script.
