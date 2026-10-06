# reachouttrack-landing

Page statique pour `www.reachouttrack.org`, hébergée sur GitHub Pages. Le
service étant ouvert à tous depuis le 6 octobre 2026 (spec 085), elle renvoie
vers l'application (`app.reachouttrack.org`) et est conservée comme support de
la future campagne de communication. Dépôt volontairement autonome : aucun
code partagé avec l'application ReachOutTrack.

- `index.html` — la page (autonome, styles inline, indexable)
- `CNAME` — domaine custom GitHub Pages
- `robots.txt` — tout autorisé, pointe vers le sitemap
- `sitemap.xml` — une seule URL, `https://www.reachouttrack.org/` (identique à
  la balise `canonical` d'`index.html`)

Mise à jour : éditer `index.html`, `git push` → redéploiement Pages en ~1 min.

## Tester en local

Servir le dossier en HTTP plutôt qu'ouvrir `index.html` directement : en
`file://`, la CSP (`img-src 'self'`) peut bloquer la capture d'écran.

```sh
python -m http.server 8000
# ou, sans Python : npx serve -l 8000 .
```

Puis ouvrir <http://localhost:8000>. Vérifier l'affichage mobile (outils de
développement → mode appareil) et le thème sombre (préférence du système, ou
outils de développement → Rendu → `prefers-color-scheme: dark`). `Ctrl+C` pour
arrêter le serveur.

## Règles à respecter (spec 085, S32)

- **Mentions légales** liées en pied de page et **hébergeur GitHub** identifié
  sur la page (LCEN art. 6-III), même sans collecte de données.
- **Aucun script tiers** de mesure d'audience ou de publicité (la CSP l'interdit
  de toute façon). Pour suivre la campagne, préférer des paramètres UTM sur les
  liens vers l'application.
- **Page indexable** : `noindex` a été retiré une fois la demande de dépôt de
  marque lancée. Le remettre (`<meta name="robots" content="noindex" />`) si le
  dépôt est refusé ou fait l'objet d'une opposition.

Procédure complète (DNS OVH, activation Pages, HTTPS, conditions de
conservation de la page) : `docs/runbook-page-attente-github-pages.md` (§10)
dans le dépôt applicatif.
