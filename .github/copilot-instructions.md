# Copilot Instructions for This Repository

### Aperçu
- Type : site statique Jekyll, contenu en Markdown.
- Thème actuel : Minimal Mistakes (via `remote_theme` ou gem `minimal-mistakes-jekyll`).
- Usage : site d'association sportive — pages principales : Accueil, Projets, Contact.

### Changements récents
- Passage au thème Minimal Mistakes.
- Ajout des assets : `assets/images/logo.svg` et `assets/images/banner.jpg`.

### Structure et fichiers importants
- `_config.yml` — configuration (titre, `baseurl`, thème, plugins, navigation, `defaults`).
- `index.md`, `projets.md`, `contact.md` — pages en Markdown.
- `assets/images/` — logos et images de bannière.
- `.github/workflows/` — workflows CI optionnels.

### Build local et plugin requis
Minimal Mistakes utilise parfois le tag Liquid `include_cached` fourni par le plugin `jekyll-include-cache`. Pour un build fiable, il est recommandé d'utiliser Bundler et un `Gemfile` listant les gems nécessaires.

Exemple de `Gemfile` recommandé :
```ruby
source "https://rubygems.org"

gem "jekyll", "~> 4.2"
gem "minimal-mistakes-jekyll"
gem "jekyll-include-cache"
gem "jekyll-feed"
```

Commandes locales pour tester :
```bash
gem install bundler
bundle install
bundle exec jekyll serve
```

Si tu préfères garder `remote_theme: "mmistakes/minimal-mistakes"`, il faudra toutefois builder via `bundle` (ou en CI) pour charger `jekyll-include-cache` si le thème l'utilise.

### Déploiement / CI (extrait)
Installer les dépendances puis builder :
```yaml
- name: Install dependencies
  run: |
    gem install bundler
    bundle install
- name: Build site
  run: bundle exec jekyll build --destination _site
```

Puis déployer le contenu de `_site` (par ex. via `peaceiris/actions-gh-pages`).

### Gestion des images (logo / bannière)
- Place les images dans `assets/images/`.
- Pour éviter les faux positifs du linter, les exemples dans la doc utilisent des chemins explicites :
```markdown
![Logo](/assets/images/logo.svg)
<img src="/assets/images/banner.jpg" alt="Bannière" />
```

### Utiliser la bannière avec Minimal Mistakes
Minimal Mistakes attend généralement l'image de l'en-tête dans le front matter d'une page (`header.image`) ou via `defaults` dans `_config.yml`.

Exemple (front matter d'une page) :
```yaml
---
title: Accueil
header:
  teaser: true
  image: "/assets/images/banner.jpg"
  caption: "Association Sportive — Passion & Partage"
---
```

Exemple (appliquer globalement via `_config.yml`) :
```yaml
defaults:
  - scope:
      path: ""
      type: "pages"
    values:
      header:
        teaser: true
        image: "/assets/images/banner.jpg"
```

### Bonnes pratiques
- Préfère les SVG pour les logos (transparence et scalabilité).
- Optimise les images avant commit (compression).
- Documente toute modification structurelle dans `README.md`.

### Points d'attention
- Si tu rencontres `Unknown tag 'include_cached'`, ajoute `jekyll-include-cache` au `Gemfile` et build via `bundle`.
- Vérifie `baseurl` dans `_config.yml` pour les chemins d'assets.
- Évite de modifier le HTML du thème Minimal Mistakes ; privilégie la configuration et les includes.

---

Documente toute modification structurelle dans le `README.md` ou ici.
