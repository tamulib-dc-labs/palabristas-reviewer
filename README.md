# Whisper Transcript Reviewer

A web application for reviewing VTT files and Whisper / Whisper X JSON transcripts with word-level confidence scoring.

## Using This Template

This repository is a GitHub template. To create your own instance:

1. Click **"Use this template"** button on GitHub (or go to the repository and select "Use this template" > "Create a new repository")
2. Clone your new repository locally
3. Run the setup script:

```bash
npm run setup
```

The setup script will prompt you for:
- **Project title** - Displayed in the header
- **Project subtitle** - Description shown below the title
- **GitHub repository name** - Used for the deployment base path
- **npm package name** - For package.json
- **DaisyUI theme** - Visual theme (synthwave, dark, light, cyberpunk, etc.)
- **Footer text** - Displayed in the footer

4. Add your media files to `public/config.json` (see format below)
5. Install dependencies and start developing:

```bash
npm install
npm run dev
```

## Configuration

### Media Files (config.json)

Add your transcript files to `public/config.json`. Each entry should have:

```json
[
  {
    "audio": "https://example.com/media/audio.m3u8",
    "url": "https://example.com/transcripts/transcript.json",
    "vtt": "https://example.com/vtts/subtitle.vtt",
    "name": "display-name"
  }
]
```

| Field | Required | Description |
|-------|----------|-------------|
| `audio` | Yes | URL to audio/video stream (M3U8, MP4, etc.) |
| `url` | Yes | URL to Whisper X JSON transcript |
| `vtt` | No | URL to VTT subtitle file |
| `name` | Yes | Display name in the dropdown selector |

See `public/config.example.json` for a sample.

### Transcript JSON Format

The transcript JSON files can include optional word-level data with confidence scores:

```json
{
  "word_score_buckets": {
    "Good": 0.85,
    "Neutral": 0.65,
    "Bad": 0.25
  },
  "segments": [...]
}
```

This is useful to add to your pipeline when you have items with particularly bad confidence scores.

If `word_score_buckets` is not included, defaults will be used instead.

## Development

```bash
npm run dev      # Start development server
npm run build    # Build for production
npm run preview  # Preview production build
```

## Deployment

This project is configured for GitHub Pages deployment. The GitHub Actions workflow in `.github/workflows/build.yml` automatically builds and deploys on push to main.

Make sure your repository name in `vite.config.js` matches your GitHub repository name for correct path resolution.

## Themes

This project uses [DaisyUI](https://daisyui.com/docs/themes/) themes. Available themes include:
- light, dark, cupcake, bumblebee, emerald, corporate
- synthwave, retro, cyberpunk, valentine, halloween, garden
- forest, aqua, lofi, pastel, fantasy, wireframe, black
- luxury, dracula, cmyk, autumn, business, acid, lemonade
- night, coffee, winter, dim, nord, sunset

Change the theme in `index.html` by modifying the `data-theme` attribute on the `<html>` element.

## Shout Outs and Acknowledgements

* This work was initially inspired by [edsu](https://github.com/edsu) and his original [whisper-transcript](https://github.com/edsu/whisper-transcript)
* Also, much appreciation to [Jvk Chaitanya](jvk1chaitanya) for they idea of `word_score_buckets`, dynamic scoring, and real time display of word scores.

---

*Originally created for the Oral Histories Edge Grant project.*
