# PurpleLotus 🌸

**Supply Chain Security that ships with your code.**

PurpleLotus finds business logic flaws and multi-step vulnerabilities that traditional tools miss — without drowning you in noise. Built for open source teams who ship fast and can't look away.

## ⚡ Quick Install

### One-Line Install (Recommended)

```bash
curl -fsSL https://purplelotus.space/install.sh | bash
```

This will:
- Download the latest version
- Install Python dependencies
- Fetch live threat feed data
- Set up a local development server

### Manual Installation

```bash
# Clone the repository
git clone https://github.com/your-username/Purple3.git
cd Purple3

# Install Python dependencies
pip3 install -r requirements.txt

# Fetch latest threat data
python3 fetch_attacks.py
python3 fetch_incident_digest.py

# Start local server
python3 -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000) in your browser.

## 📋 Requirements

- **Python 3.8+** - For running threat feed scripts
- **pip3** - Python package manager
- **git** - Version control

### Optional

- **GITHUB_TOKEN** - Environment variable for higher GitHub API rate limits (recommended for frequent updates)

## 🚀 Usage

### Starting the Server

```bash
cd ~/purplelotus/Purple3
./start.sh
```

Or manually:

```bash
python3 -m http.server 8000
```

### Updating Threat Feed Data

The threat feed pulls real-time data from the GitHub Advisory Database:

```bash
# Update supply chain threat feed
python3 fetch_attacks.py

# Update AI incident digest
python3 fetch_incident_digest.py
```

For automated updates, consider setting up a cron job:

```bash
# Edit crontab
crontab -e

# Add this line to update daily at 6 AM
0 6 * * * cd ~/purplelotus/Purple3 && python3 fetch_attacks.py && python3 fetch_incident_digest.py
```

### Using GitHub Token (Optional)

To avoid API rate limits, set a GitHub personal access token:

```bash
export GITHUB_TOKEN="your_github_token_here"
python3 fetch_attacks.py
```

## 📁 Project Structure

```
Purple3/
├── index.html              # Main landing page
├── blogs.html              # Blog listing page
├── threat-feed.html        # Live threat feed page
├── style.css               # Styles
├── install.sh              # Installation script
├── start.sh                # Server launch script
├── requirements.txt        # Python dependencies
├── fetch_attacks.py        # Threat feed fetcher
├── fetch_incident_digest.py # AI incident fetcher
├── data/                   # JSON data files
│   ├── attacks.json        # Supply chain advisories
│   └── blogs.json          # Blog posts metadata
└── blog/                   # Individual blog posts
```

## 🔧 Development

### Adding Blog Posts

1. Create your blog post in the `blog/` directory
2. Update `data/blogs.json` with metadata:

```json
{
  "posts": [
    {
      "title": "Your Blog Title",
      "excerpt": "Brief description...",
      "date": "2025-01-15",
      "tag": "Security",
      "read_time": "5 min read",
      "url": "blog/your-post.html"
    }
  ]
}
```

### Customizing the Threat Feed

Edit the following constants in `fetch_attacks.py`:

```python
DAYS_BACK = 30           # Number of days to look back
PER_PAGE = 50            # Results per API page
MAX_PAGES = 4            # Maximum pages to fetch
RELEVANT_ECOSYSTEMS = {  # Package ecosystems to include
    "npm", "pip", "rubygems", "maven", "nuget", "go", ...
}
```

## 🌐 Deployment

### Vercel (Recommended)

This project is configured for Vercel deployment:

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel
```

### GitHub Pages

```bash
# Push to GitHub
git push origin main

# Enable GitHub Pages in repository settings
# Source: main branch / root
```

### Other Static Hosts

The site is purely static HTML/CSS/JS and can be hosted on:
- Netlify
- Cloudflare Pages
- AWS S3 + CloudFront
- Any static file server

## 🔒 Security Features

- **Live Threat Feed**: Real-time supply chain security advisories from GitHub
- **No LLM Processing**: Direct API data, no AI hallucinations
- **Open Source**: Full transparency, audit the code yourself
- **Privacy-First**: No tracking, no analytics, no cookies

## 📄 License

Copyright © 2025 PurpleLotus, Inc. All rights reserved.

## 🤝 Support

- **Email**: [security@purplelotus.tech](mailto:security@purplelotus.tech)
- **Website**: [purplelotus.space](https://purplelotus.space)

## 🎯 What We Do

### Products
- **Osprey** - Supply chain security scanning
- **Petal** - Coming soon

### Services
- Network Penetration Testing
- Application Penetration Testing
- Social Engineering Testing

---

**Because breaches aren't an option. Don't let your workflows work against you.**
