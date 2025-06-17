# Introduction


Ce projet a pour objectif de mettre en place une solution d'intelligence artificielle générative en auto-hébergement. Il s'appuie sur deux composants principaux :

- Ollama : un outil permettant de télécharger, gérer et exécuter localement des modèles de langage (LLMs).

- Open WebUI : une interface web moderne et intuitive pour interagir avec ces modèles en toute simplicité.

Cette plateforme permet à un utilisateur de poser des questions en langage naturel et d'obtenir des réponses cohérentes, contextuelles, et intelligentes, sans dépendre de services cloud externes.

## Qu'est-ce qu'un LLM ?

Un LLM (ou modèle de langage à grande échelle) est un modèle d’intelligence artificielle entraîné sur d’énormes volumes de texte. Ces modèles apprennent les structures, relations, et significations dans le langage humain. Une fois entraîné, un LLM est capable de :

- Comprendre et générer du texte en langage naturel

- Répondre à des questions, traduire des textes, résumer des documents

- Simuler une conversation naturelle, écrire du code, etc.

Les modèles les plus connus aujourd'hui sont GPT-3, GPT-4, LLaMA (Meta), Mistral, etc. Ces modèles contiennent des milliards de paramètres : ce sont des fonctions mathématiques ajustées pendant l'entraînement pour prédire le mot suivant dans une phrase.

Par exemple :

**Entrée** : *"Le ciel est bleu parce que..."*

**Sortie :** *"...la lumière du soleil est diffusée par l’atmosphère terrestre."*

## Pourquoi utiliser Ollama et Open WebUI ?

Ollama permet d'exécuter localement les LLMs, sans envoyer vos données vers un serveur distant.

Open WebUI fournit une interface élégante pour discuter avec ces modèles, comparable à ChatGPT, mais auto-hébergée, respectueuse de la vie privée et entièrement personnalisable.

Ce projet est donc une alternative locale, libre et extensible aux assistants IA disponibles sur Internet.

## Où sont stockées les données ?

Ce projet est conçu pour **fonctionner entièrement en local**, garantissant ainsi **la confidentialité totale des données** :

- **Les modèles sont stockés sur la machine locale**, dans le dossier `~/.ollama`.
- **Les historiques de conversation sont enregistrés dans le volume Docker d'Open WebUI**, accessible uniquement par l'utilisateur du système.
- Aucune donnée n’est envoyée vers des serveurs distants, sauf configuration explicite.

Ainsi, toutes les interactions avec les modèles d'IA sont **privées, sécurisées, et sous ton contrôle total**.


## Environnement de déploiement – Machine Virtuelle

Pour garantir de bonnes performances à l’**IA générative auto-hébergée**, ce projet a été déployé sur une **machine virtuelle (VM)** puissante, optimisée pour l’exécution de modèles LLM locaux, notamment ceux proposés via **Ollama**.

### Spécifications techniques de la VM

| Ressource       | Détail                        |
|------------------|-------------------------------|
|  Processeurs    | 16 cœurs                      |
|  Mémoire RAM    | 50 Go                         |
|  Stockage SSD  | 500 Go                        |
|  GPU           | NVIDIA L4 avec 24 Go de VRAM  |
|  Adresse IP     | `159.31.247.122`              |

Cette configuration permet :

-  Le **chargement rapide** et **l’inférence fluide** de modèles de langage volumineux (ex : LLaMA3, Mistral, etc.)
-  Une **installation 100% locale** sans compromis sur les performances
-  Le **support GPU (CUDA)** pour l’accélération des tâches d’inférence via la carte NVIDIA L4 (24 Go VRAM), indispensable pour des modèles LLM modernes

### Pourquoi ce choix de VM ?

Le choix de cette VM repose sur plusieurs critères clés pour une plateforme d'IA locale :

- **Compatibilité GPU avec Ollama et PyTorch** (accélération CUDA)
- **Mémoire suffisante** pour charger des modèles en RAM + VRAM sans swap
- **Stockage conséquent** pour accueillir plusieurs modèles (~2-10 Go chacun) et les historiques utilisateurs
- **Sécurité et isolation** : environnement dédié pour l’IA générative, sans interférence avec d'autres services
