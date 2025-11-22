# Mon Petit Site (Jekyll + GitHub Pages)


Ceci est un site Jekyll minimal qui utilise le thème `jekyll-theme-cayman` intégré à GitHub Pages — aucun HTML/CSS personnalisé n'est présent dans le dépôt.


Instructions rapides :

- Publier sur GitHub Pages : créez un repository (par ex. `username.github.io`) et poussez ce dossier sur la branche `main`.
- Prévisualiser localement : installez Ruby + Bundler puis exécutez :

```bash
gem install bundler jekyll
bundle init
echo "gem 'github-pages', group: :jekyll_plugins" >> Gemfile
bundle install
bundle exec jekyll serve
```

Ensuite ouvrez `http://127.0.0.1:4000`.

Déploiement automatique (GitHub Actions) :

Ce dépôt contient un workflow GitHub Actions (`.github/workflows/gh-pages.yml`) qui :

- se déclenche à chaque push sur la branche `main` ;
- construit le site avec l'image Docker officielle `jekyll/jekyll:4` ;
- publie le contenu généré (`_site`) sur la branche `gh-pages` à l'aide de `peaceiris/actions-gh-pages`.

Notes :

- Le déploiement utilise le `GITHUB_TOKEN` fourni automatiquement par GitHub Actions — aucune clé supplémentaire n'est requise.
- Si vous préférez que GitHub Pages construise directement le site (sans Actions), configurez Pages sur la branche `main` dans les réglages du dépôt.
- Pour changer la branche source du workflow, modifiez la clé `branches` dans `.github/workflows/gh-pages.yml`.



## Personnalisation

- Le thème a été changé pour `jekyll-theme-cayman` (voir `_config.yml`) pour un rendu plus moderne.
- Deux pages supplémentaires sont disponibles :
	- [`projets.md`](projets.md) : liste détaillée des projets
	- [`contact.md`](contact.md) : informations de contact
- La navigation entre les pages se fait via des liens Markdown en haut de chaque page.
- Pour ajouter une page, créez un fichier `.md` avec un frontmatter YAML (`--- title: ... ---`).
- Pour changer de thème, modifiez la clé `theme:` dans `_config.yml` (voir https://pages.github.com/themes/ pour la liste des thèmes compatibles).
