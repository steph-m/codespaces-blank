# Mon Petit Site (Jekyll + GitHub Pages)

Ceci est un site Jekyll minimal qui utilise le thème `minima` intégré à GitHub Pages — aucun HTML/CSS personnalisé n'est présent dans le dépôt.


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


Personnalisation :

- Modifiez `index.md` pour changer le contenu en Markdown.
- Si vous voulez un style personnalisé, dites-le : je peux proposer une modification limitée (fichier CSS séparé) ou configurer un thème différent.
