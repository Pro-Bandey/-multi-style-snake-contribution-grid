
# 🐍 Multi-Style Snake Contribution Grid

[![Generate Snake](https://github.com/YourUsername/YourRepo/actions/workflows/snake.yml/badge.svg)](https://github.com/YourUsername/YourRepo/actions/workflows/snake.yml)
[![Output Branch](https://img.shields.io/badge/branch-output-blueviolet)](https://github.com/YourUsername/YourRepo/tree/output)

Transform your GitHub contribution graph into a dynamic animation with **5 distinct styles**, unique shapes, and automated month labels. This project uses a custom composite action to generate multiple snake variations simultaneously.

## ✨ Features

- **Auto-User Detection**: No need to hardcode names; it automatically analyzes the repository owner.
- **5 Unique Themes**: Light, Dark, Ocean, Dracula, and Hacker.
- **Geometric Shapes**: Little-blocks are transformed into **Squares, Rounds, Triangles, Stars, and Diamonds**.
- **Month Visibility**: Bold month names are rendered directly above the contribution grid for better context.
- **Automated Gallery**: Generates a `README.md` inside the `output` branch to preview all assets in one place.
- **GIF & SVG Support**: High-quality SVGs for crisp profile rendering and GIFs for social sharing.

## 🎨 Style Gallery

| Style | Shape | Background | Snake Color |
| :--- | :--- | :--- | :--- |
| **Light** | 🟦 Blocks | White | Orange |
| **Dark** | 🔵 Rounds | Dark Grey | Yellow |
| **Ocean** | 🔺 Triangles | Deep Sea Blue | Cyan |
| **Dracula** | ⭐ Stars | Dracula Purple | Pink |
| **Hacker** | 💎 Diamonds | Pure Black | Neon Green |

---

## 🚀 Setup

### 1. Create the Workflow
Create a file at `.github/workflows/snake.yml` and paste the following:

```yaml
name: Generate Snake

permissions:
  contents: write
  pages: write
  id-token: write

on:
  schedule:
    - cron: "0 */6 * * *" # Every 6 hours
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      # This uses the Composite Action code we developed
      - name: Generate Snakes
        uses: Pro-Bandey/multi-style-snake-action@main # Replace with your repo path
        with:
          github_user_name: ${{ github.repository_owner }}
```

### 2. Manual Action Settings
1. Go to your repository **Settings** > **Actions** > **General**.
2. Scroll to **Workflow permissions** and ensure **"Read and write permissions"** is selected.

---

## 📊 View Your Results

After the action runs (manually or via schedule), it will create a new branch named `output`. You can find all your files there:

- `github-snake-light-blocks.svg`
- `github-snake-dark-rounds.svg`
- `github-snake-ocean-triangles.svg`
- `github-snake-dracula-stars.svg`
- `github-snake-hacker-diamonds.svg`
- `README.md` (The auto-generated gallery)

---

## 🖼️ Adding to your Profile README

Copy and paste this into your profile `README.md` to show off your favorite style:

```markdown
## 🐍 My Contribution Snake
![Snake Animation](https://github.com/USER_NAME/REPO_NAME/blob/output/github-snake-dracula-stars.svg)
```

## 🛠️ Technical Overview

The generation uses CSS `clip-path` injection for the complex shapes (Triangles, Stars, Diamonds) within the SVG output. 

```css
/* Example of the Star Shape used */
rect.ContributionCalendar-day {
  clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
}
```

---

**Author:** [Pro-Bandey](https://github.com/Pro-Bandey)  
**License:** MIT  
*Generated with ❤️ and custom CSS modifications.*
