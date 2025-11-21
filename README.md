# Mouse vs AI: Robust Visual Foraging Challenge

This repository contains the competition website for the NeurIPS 2025 "Mouse vs AI: Robust Visual Foraging Challenge".

The site is built with Jekyll and hosted as a static site (GitHub Pages). The repository contains the site source, content pages, assets, and configuration used to generate the public website.

## Quick overview

- Project: competition website for NeurIPS 2025
- Generator: Jekyll (Ruby)
- Hosting: GitHub Pages (static site)

## Local development (Linux / WSL)

These steps were tested on Ubuntu; adapt for your distribution.

1. Install system dependencies:

	sudo apt update; sudo apt install -y ruby-full build-essential zlib1g-dev

2. Install Jekyll and Bundler for the local user:

	gem install --user-install jekyll bundler

3. Configure bundler to install gems into the repository-local `vendor/bundle` and install gems:

	bundle config set --local path 'vendor/bundle'
	bundle install

4. Serve the site locally (host: http://127.0.0.1:4000):

	bundle exec jekyll serve

Notes:
- Jekyll will auto-regenerate when you edit most files. If you change `_config.yml` you must restart the server.
- The above commands create `.bundle/config`, `vendor/bundle/`, and `Gemfile.lock` in the repo.

## Local development (Windows / PowerShell)

On Windows it's recommended to use WSL (Windows Subsystem for Linux) or set up Ruby via RubyInstaller. The WSL route is simplest if available.

- Using WSL: install Ubuntu from the Microsoft Store, then follow the Linux instructions above from within WSL.
- Using native Windows Ruby (RubyInstaller):
  1. Install Ruby from https://rubyinstaller.org/ (include MSYS2/devkit when prompted).
  2. Open a new PowerShell (or MSYS2 shell) and install bundler and jekyll:

	  gem install jekyll bundler

  3. In the repo folder, run:

	  bundle config set --local path 'vendor/bundle'
	  bundle install
	  bundle exec jekyll serve

If the native Windows route fails (native gems requiring compilation), try WSL for a smoother experience.

## Editing site content

- Content pages live under `_pages/` and `_includes/`.
- Site configuration is in `_config.yml`.
- Static assets are in `assets/` and `assets/images/`.
- Data for the site is under `_data/`.

When editing Markdown files in `_pages/` changes will typically be reflected immediately in the local server.

## Deploying to GitHub Pages

This repository is set up for GitHub Pages. To publish:

1. Push your branch to GitHub (the repository owner may use `main` as the publishing branch).
2. Ensure GitHub Pages is configured for the repository to publish from the `main` branch (or `gh-pages` if you use that). The GitHub repo settings control the exact behavior.

GitHub will build the site automatically when using the `gh-pages` branch or a pre-built site; since this repo contains a Jekyll source it should work with GitHub Pages' Jekyll build unless it uses unsupported plugins.

## Repository structure (high-level)

- `_pages/` — Markdown pages shown on the site (home, guides, etc.)
- `_includes/` — reusable HTML includes (sidebar, head, masthead)
- `_data/` — structured YAML/CSV data (navigation, leaderboard)
- `assets/` — images, videos, and other static files
- `_config.yml` — Jekyll configuration
- `Gemfile` / `Gemfile.lock` — Ruby gem dependencies for Jekyll

## Contributing

1. Create a branch for your changes.
2. Edit or add pages under `_pages/` or content under `assets/`.
3. Run `bundle exec jekyll serve` locally and verify your changes.
4. Open a pull request describing your changes.

If you're not the repository owner, coordinate with the maintainers before making major changes.

## Contact / Maintainers

See the repository for maintainer details or open an issue / PR on GitHub.

## License

No license file is included in this repository. If you plan to reuse content, please check with the repository owner or add a LICENSE file to clarify reuse terms.

---

If you'd like, I can also:

- add a short contributing guide (CONTRIBUTING.md)
- add a GitHub Actions workflow to build and preview the site on PRs
- add a simple LICENSE file (specify which license you'd like)

Tell me which of those you'd like and I'll implement it.
