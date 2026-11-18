# PicForge AI — Image Studio

React + Express image generator using Cloudflare Workers AI (`flux-1-schnell`).
Every image you generate (or upload) is saved in the **`uploads/`** folder using **multer**.

## Setup (Windows)

```powershell
npm install
```

Create a `.env` file in this folder:

```env
CLOUDFLARE_ACCOUNT_ID=your_account_id
CLOUDFLARE_API_TOKEN=your_api_token
PORT=4000
```

Start frontend + backend together:

```powershell
npm run dev
```

- Frontend: http://localhost:5173
- Backend: http://localhost:4000 (health: http://localhost:4000/api/health)

## Features

- Generate images from any prompt (JPG / PNG / WebP)
- Every image is saved to `uploads/` (multer disk storage); details are kept in `data/images.json`
- Upload your own images into the same folder
- Image history comes from the server, so it survives refresh and browser changes
- Search, delete one image, or clear all (files are removed from `uploads/` too)
- Download, copy prompt, reuse prompt, full-size viewer
- Dark / Light theme (saved in the browser)
- Animations, toast messages, mobile-friendly sidebar

## API

| Method | URL | What it does |
| --- | --- | --- |
| GET | `/api/images` | List saved images |
| POST | `/api/generate` | Generate + save image (`prompt`, `format`) |
| POST | `/api/upload` | Upload an image (`image` file field, max 10 MB) |
| DELETE | `/api/images/:id` | Delete one image |
| DELETE | `/api/images` | Delete all images |
| GET | `/uploads/<file>` | Open a saved image |

Keep your `.env` private. Do not share your API token.
