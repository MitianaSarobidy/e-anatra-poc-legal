# Pages publiques Meta — E-anatra

Ces fichiers statiques contiennent la politique de confidentialité, les instructions de suppression des données et les conditions d'utilisation du POC. Ils ne contiennent aucun token ou secret. Le responsable E-anatra doit relire le contenu et signaler toute correction nécessaire.

## Hébergement proposé

Ce dépôt public distinct, `MitianaSarobidy/e-anatra-poc-legal`, contient uniquement ces pages et peut être publié avec GitHub Pages depuis sa branche par défaut. Les URL sont :

- `https://mitianasarobidy.github.io/e-anatra-poc-legal/confidentialite.html`
- `https://mitianasarobidy.github.io/e-anatra-poc-legal/suppression-donnees.html`
- `https://mitianasarobidy.github.io/e-anatra-poc-legal/conditions.html`

Vérifier les URL en HTTPS et leur accès sans connexion avant de les copier dans **Paramètres de l'app → Général**. La politique et la suppression des données sont les deux pages essentielles ; les conditions sont prêtes si Meta les demande. Ne pas publier le dépôt du POC entier : il contient le code de l'application et sa configuration de développement.

## Conservation opérationnelle

Le service Docker `retention` exécute `app:purge-comments --days=29` au démarrage et chaque jour. Il supprime les commentaires anciens et leur historique ; la suppression ciblée sur demande se fait avec `docker compose exec backend php bin/console app:delete-comment --id=<UUID>`. Si l'environnement est arrêté, la purge reprend dès le redémarrage. Vérifier périodiquement `docker compose logs retention`.
