# asmr2026-docs
Course documentation and project resources for the 2026-2 Actuation and Sensing Mechanism Design for Robots class, covering humanoid assembly, actuator and sensor setup, reinforcement-learning simulation, and sim-to-real transfer.

Published site: https://snu-srbl.github.io/asmr2026-docs/

eTL remains the official place for course notices, homework, and submissions. This site is the course guide and materials portal.

Built with [Jekyll](https://jekyllrb.com) and the [Just the Docs](https://just-the-docs.github.io/just-the-docs/) theme, based on the [just-the-docs-template](https://github.com/just-the-docs/just-the-docs-template).

## Site structure

```
index.md                 Home page: project overview, section table, material status, gallery
start-here/              Start Here: course introduction, Berkeley Humanoid Lite
hardware/                Robot Hardware: BOM, actuator assembly, motor driver, USB-to-CAN adapter,
                         body system, low-level software, full robot assembly
cad-to-robot/            From CAD to Robot: Onshape CAD, onshape-to-robot
simulation/              Simulation and Learning: robot model (v1), actuator modeling,
                         Isaac Sim and Isaac Lab, mjlab, real robot safety
references/              References
downloads/               Downloads and Versions: released files and version history
help.md                  Help
assets/downloads/        Released files (actuator parts, leg structure STLs, robot model package)
assets/images/           Images, one folder per topic
_includes/head_custom.html  Opens links to other websites in a new tab
_config.yml              Site settings (title, eTL link, callouts, navigation links)
.github/workflows/       pages.yml deploys to GitHub Pages; ci.yml test-builds pull requests
```

Each section is a folder with an `index.md` (`has_children: true`); pages inside it set `parent:` to the section title and `nav_order:` for their position in the sidebar.

## Updating the site

- **New page:** copy an existing page in the same section, change `title`, `nav_order`, and `permalink`, and write the content.
- **New released file:** put it in `assets/downloads/` (no spaces in file names), link it from its page, and add a row to the version history in `downloads/index.md`.
- **New image:** put it in `assets/images/<topic>/`. Keep photos under about 1600 px and 500 KB, and remove GPS data from phone photos before adding them.
- **Status:** the "Material status" table in `index.md` shows one row per section. Use `label-green` (Available), `label-blue` (Partly available), or `label-yellow` (Coming soon).
- **Notes for maintainers:** HTML comments starting with `TA:` mark places where more content can be added. Students don't see them.

Useful formatting: callouts `{: .note }`, `{: .important }`, `{: .warning }`, `{: .soon }` placed on the line above a paragraph. See the [Just the Docs documentation](https://just-the-docs.github.io/just-the-docs/) for more.

## Previewing locally

Requires Ruby 3.3, the same version the GitHub workflow uses. The macOS system Ruby (2.6) is too old, and Ruby 4.x does not work with Jekyll 4.4 (`cannot load such file -- logger`). With Homebrew:

```bash
brew install ruby@3.3
export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"   # add to ~/.zshrc to make permanent
ruby -v   # should print 3.3.x
```

Then, from the repository root:

```bash
bundle install
bundle exec jekyll serve --livereload
```

Open http://localhost:4000/asmr2026-docs/ in a browser. Pages rebuild automatically when you save; restart the server after editing `_config.yml`.

## Publishing

The site is built and deployed by GitHub Actions (`.github/workflows/pages.yml`) on every push to `main`.

One-time setup: in the GitHub repository go to **Settings → Pages → Build and deployment → Source** and select **GitHub Actions**.
