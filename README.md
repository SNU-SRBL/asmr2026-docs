# asmr2026-docs
Course documentation and project resources for the 2026-2 Actuation and Sensing Mechanism Design for Robots class, covering humanoid assembly, actuator and sensor setup, reinforcement-learning simulation, and sim-to-real transfer.

Published site: https://snu-srbl.github.io/asmr2026-docs/

eTL remains the official place for course notices, homework, and submissions. This site is the course guide and materials portal.

Built with [Jekyll](https://jekyllrb.com) and the [Just the Docs](https://just-the-docs.github.io/just-the-docs/) theme, based on the [just-the-docs-template](https://github.com/just-the-docs/just-the-docs-template).

## Site structure

```
index.md                 Home page (includes the material status table)
start-here/              Start Here: course introduction, Berkeley Humanoid Lite
hardware/                Robot Hardware: BOM, actuator assembly, motor driver, robot assembly
cad-to-robot/            From CAD to Robot: Onshape CAD, onshape-to-robot
simulation/              Simulation and Learning: actuator modeling, Isaac Sim, mjlab, RL / sim-to-real
downloads/               Downloads and Versions: released files and version history
help.md                  Help
_config.yml              Site settings (title, eTL link, callouts, navigation links)
.github/workflows/       pages.yml deploys to GitHub Pages; ci.yml test-builds pull requests
```

Each section is a folder with an `index.md` (`has_children: true`); pages inside it set `parent:` to the section title and `nav_order:` for their position in the sidebar.

## Publishing a placeholder page

Placeholder pages contain a `Coming soon` label, a `{: .soon }` callout, and an HTML comment starting with `TA:`. When the material is ready:

1. Replace the placeholder content in the page.
2. Remove the `Coming soon` label and the `{: .soon }` callout.
3. In `index.md`, change the page's status in the "Material status" table to `<span class="label label-green">Available</span>`.
4. For released files, add a row to the version history in `downloads/index.md`.

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
