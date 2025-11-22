# Copilot Instructions for This Repository

## Aperçu du projet
- **Type** : Site statique minimal basé sur Jekyll, uniquement Markdown, sans HTML/CSS personnalisé.
- **Thème** : `minima` (fourni par GitHub Pages, aucune personnalisation locale du thème).
- **Usage principal** : Présenter un site simple, responsive, facile à maintenir, hébergé sur GitHub Pages.

## Structure et fichiers clés
- `_config.yml` : Configuration Jekyll (titre, baseurl, thème, options de build).
- `index.md` : Page d'accueil, tout le contenu éditable en Markdown.
- `.github/workflows/gh-pages.yml` : Déploiement automatique via GitHub Actions (build Docker Jekyll, publication sur `gh-pages`).
- `README.md` : Instructions pour preview local, déploiement, et personnalisation.

## Workflows et commandes critiques
- **Preview local** :
  ```bash
  gem install bundler jekyll
  bundle init
  echo "gem 'github-pages', group: :jekyll_plugins" >> Gemfile
  bundle install
  bundle exec jekyll serve
  ```
  Accès sur `http://127.0.0.1:4000`.
- **Déploiement** :
  - Automatique à chaque push sur `main` (voir workflow GitHub Actions).
  - Utilise l'image Docker officielle `jekyll/jekyll:4` pour garantir la cohérence du build.
  - Publication sur la branche `gh-pages` via `peaceiris/actions-gh-pages`.

## Conventions et particularités
- **Aucune personnalisation HTML/CSS** :
  - Toute modification de contenu se fait en Markdown.
  - Pour ajouter du style, créer un fichier CSS séparé ou changer de thème (voir README).
- **Pas de plugins Jekyll custom** :
  - Seuls les plugins supportés par GitHub Pages sont autorisés (via `github-pages`).
- **Baseurl** :
  - Toujours définir `baseurl` dans `_config.yml` pour un site projet (ex : `/codespaces-blank`).

## Exemples de patterns
- Pour ajouter une nouvelle page : créer un fichier `.md` à la racine, ajouter un frontmatter YAML minimal (`--- title: ... ---`).
- Pour modifier le menu ou l'apparence : passer par la configuration du thème ou changer de thème (pas de modification directe du HTML).

## Points d'attention pour les agents
- Ne pas générer de HTML/CSS custom sans demande explicite.
- Respecter la structure minimaliste et la logique Markdown-only.
- Toute personnalisation doit être documentée dans le README.
- Vérifier la cohérence du `baseurl` et des liens internes lors de l'ajout de pages.

---

Pour toute modification structurelle ou ajout de fonctionnalité, documenter la démarche dans le README et/ou ce fichier.
