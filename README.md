# BMAD Framework Submodule

[BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD) - Universal AI Agent Framework.

Prepackaged prompt & context engineering framework for the full software development lifecycle. Specialized agents (Analyst, PM, Architect, Dev, Test Architect) with curated workflows and knowledge bases.

## Why use a Git Submodule?

A submodule is a pointer to another git repository, akin to a bookmark. Your repo stores a reference (`.gitmodules` + SHA), not the actual files.

**Why use this:**

- Clean PRs (2 files vs 300+ BMAD framework related files)
- Central updates (one BMAD repo → all projects)
- Auto-initialization via `npm install`

**Alternative (gitignore):** Every engineer installs BMAD individually. Submodule installs once for everyone.

---

## Setup

### Add to Your Project

```bash
git submodule add https://github.com/muratkeremozcan/bmad-submodule.git bmad-submodule
git submodule init
git submodule update
```

### Auto-Initialize (Recommended)

Add to `package.json`:

```json
{
  "scripts": {
    "postinstall": "git submodule update --init --recursive || true"
  }
}
```

Now `npm install` auto-initializes BMAD.

### Clone with Submodules

```bash
# One command
git clone --recurse-submodules <your-repo>

# Or after clone
git submodule update --init --recursive
```

## Updating this submodule at your repo

Nav to the submodule folder, pull, nav to repo root and commit.

```bash
  cd youre-repo/bmad-submodule
  git pull origin main
  cd ..
  git add bmad-submodule
  git commit -m "Update BMAD"
  git push
```

### Clean installing (or renaming the submodule) at your repo

```bash
  # 1. Completely remove current submodule
  git submodule deinit -f bmad-submodule
  git rm -f bmad-submodule
  rm -rf .git/modules/bmad-submodule

  # 2. Empty .gitmodules
  echo "" > .gitmodules

  # 3. Re-add with desired name
  git submodule add https://github.com/muratkeremozcan/bmad-submodule.git bmad-submodule

  # 4. Verify
  ls -la bmad-submodule/
  git submodule status
```

<!-- TODO: -->
