# Place this file at: .github/workflows/snake.yml
# in your hotukasim/hotukasim profile repo.
#
# It regenerates the "snake eating your contributions" animation
# that the README embeds from the `output` branch.

name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"   # once a day, midnight UTC
  push:
    branches:
      - main
  workflow_dispatch:        # lets you trigger it manually from the Actions tab

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    steps:
      - uses: Platane/snk@v3
        id: snake-gif
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
