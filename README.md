# Map Posters Gallery

A GitHub Pages site showcasing beautiful, minimalist map posters generated using the [maptoposter](https://github.com/orangewise/maptoposter) tool.

**Live Site:** https://orangewise.github.io/maps/

## Overview

This repository automatically generates map posters for various cities using GitHub Actions and deploys them to GitHub Pages. The maps are created using OpenStreetMap data and rendered with different artistic themes.

## Current Cities

- **Haarlem, Netherlands** - Generated with Midnight Blue and Ocean themes

## How It Works

1. **Configuration**: Cities and themes are defined in `cities.json`
2. **Automation**: GitHub Actions workflow automatically generates map posters
3. **Deployment**: Generated maps are deployed to GitHub Pages
4. **Gallery**: A responsive web gallery displays all generated posters

## Available Themes

The maptoposter tool supports 17 different themes:

- `midnight_blue` - Calming blue palette
- `ocean` - Deep ocean tones with white streets
- `autumn` - Warm autumn colors
- `blueprint` - Classic blueprint style
- `contrast_zones` - High contrast zones
- `copper_patina` - Aged copper look
- `feature_based` - Different shades for road types
- `forest` - Natural forest greens
- `gradient_roads` - Roads with gradient effects
- `japanese_ink` - Traditional ink art style
- `monochrome_blue` - Single blue tone
- `neon_cyberpunk` - Vibrant neon colors
- `noir` - Black and white noir style
- `pastel_dream` - Soft pastel colors
- `sunset` - Warm sunset tones
- `terracotta` - Earth tones
- `warm_beige` - Neutral warm palette

## Adding New Cities

To add a new city to the gallery:

1. Edit `cities.json` and add your city:
```json
[
  {
    "city": "Haarlem",
    "country": "Netherlands",
    "themes": ["midnight_blue", "ocean"]
  },
  {
    "city": "Amsterdam",
    "country": "Netherlands",
    "themes": ["neon_cyberpunk", "japanese_ink"]
  }
]
```

2. Update `index.html` to include the new city section in the gallery

3. Commit and push your changes - GitHub Actions will automatically generate the new maps

## Manual Generation

To generate maps locally:

```bash
# Clone the maptoposter tool
git clone https://github.com/orangewise/maptoposter.git

# Install dependencies
cd maptoposter
pip install -r requirements.txt

# Generate a map
python create_map_poster.py --city Haarlem --country Netherlands --theme midnight_blue
```

## GitHub Actions Workflow

The `.github/workflows/generate-maps.yml` workflow runs on all branches and pull requests:

1. **Map Generation** (all branches):
   - Checks out this repository
   - Clones the maptoposter tool
   - Sets up Python and installs dependencies with uv
   - Generates map posters for configured cities
   - Creates the gallery HTML and CSS
   - Uploads generated images as artifacts (90-day retention)
   - Commits images to the branch (except on main and forks)

2. **GitHub Pages Deployment** (main branch only):
   - Configures GitHub Pages
   - Deploys the public gallery to https://orangewise.github.io/maps/

### Accessing Generated Images

- **From any branch**: Download artifacts from the workflow run (available for 90 days)
- **From feature branches**: Images are committed to the `images/` directory
- **From main branch**: Images are deployed to GitHub Pages

## GitHub Pages Setup

To enable GitHub Pages for this repository:

1. Go to Settings > Pages
2. Source: Select "GitHub Actions"
3. The site will be available at `https://[username].github.io/[repo-name]/`

## Credits

- Map generation: [maptoposter](https://github.com/orangewise/maptoposter) by @orangewise
- Map data: © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors
- Fonts: Roboto typeface

## License

See [LICENSE](LICENSE) file for details.