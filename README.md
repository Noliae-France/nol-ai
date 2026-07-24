# nol.ai

API IA **agnostique du fournisseur** en pur [Nolc](https://noliae-nolc.s3.gra.io.cloud.ovh.net/nolc-latest-linux-x86_64.tar.gz), sans dépendance. Un même code cible un modèle local ou distant.

## Installation

```toml
[dependances]
"nol-ai" = { git = "https://github.com/Noliae-France/nol-ai" }
```

## API (v0.1 — le cœur)

- **Messages typés** : `message_systeme`, `message_utilisateur`, `message_assistant`
- **Requête** : `requete_neuve(modele)` + `messages`, `temperature_millieme`, `max_tokens`
- **Sérialisation** : `requete_json(r)` — format chat compatible (OpenAI-like)
- **Réponse** : `reponse_contenu(json)` — extrait le texte généré

```nol
var r = requete_neuve("mon-modele")
push(r.messages, message_systeme("Tu es utile."))
push(r.messages, message_utilisateur("Bonjour"))
let corps = requete_json(r)   // { "model":..., "messages":[...], "temperature":0.700 }
```

## Feuille de route

Génération complète **et streaming** · sortie **JSON structurée** · **appels d'outils** · **embeddings** · **vision et audio** · **annulation et timeout** · quotas et répétitions · **statistiques de tokens** · dorsaux local (voir [nol-llama](https://github.com/Noliae-France/nol-llama)) et distants.

## Licence

MIT © 2026 Bastien LANGUEDOC.
