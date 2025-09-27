# RPG Nexus

Plateforme de jeu de rôle (RPG) 2D sous Unity, pensée comme un socle modulaire pour jouer **dans les univers, personnages et campagnes créés sur RPG-Gestionary** (auth, récupération/synchronisation des données, outillage MJ).

## 🗺️ Contexte & objectifs (client)

* **Contexte** : le site **RPG-Gestionary** permet de créer univers, personnages et campagnes. Le jeu **RPG Nexus** doit offrir une expérience « plateau » connectée à ces contenus. 
* **Objectif** :

  * Authentifier les utilisateurs avec leurs identifiants RPG-Gestionary.
  * **Récupérer** univers/PNJ/personnages/sessions autorisés pour l’utilisateur.
  * **Permettre aux MJ** de créer des **maps** et des **sessions** puis d’animer la partie (dés, fog of war, PNJ/ennemis, états/bonus/malus, inventaire).
  * **Sauvegarder** l’avancement des campagnes **sur la plateforme**. 

## 🎮 Portée V1 (CdC)

Fonctionnalités cœur directement alignées sur le besoin client :

* **Authentification** via identifiants RPG-Gestionary *(implémentation exacte à valider avec l’API ; ne jamais stocker de mot de passe en clair)*. 
* **Récupération des données joueur** : univers accessibles, personnages jouables, sessions disponibles. 
* **Rôles & droits** : différenciation **Joueur** / **MJ** (MJ hérite des droits joueur + outils). 
* **Éditeur de map (MJ)** : création/édition de cartes d’un univers ; **une map peut appartenir à plusieurs sessions**. 
* **Gestion des sessions (MJ)** : création/lancement de sessions dans un univers. 
* **Dés en session** (MJ & joueurs) avec **modificateurs/attributs paramétrables**. 
* **Fog of War** : verrouillage/déverrouillage de zones par le MJ. 
* **PNJ & ennemis** : création/contrôle par le MJ en session. 
* **États/effets** sur personnages (bonus/malus) gérés par le MJ. 
* **Inventaire** : gestion par le MJ, **vue en lecture seule côté joueurs**. 
* **Familiers** : gestion côté MJ **ou** joueur selon option définie sur le site. 
* **Sauvegarde/synchronisation** de la progression de la campagne vers RPG-Gestionary. 

### Hors-portée V1 (éventuellement plus tard)

* Combat RPG complet, dialogues/quetes, progression de niveau, audio avancé, etc. (anciens objectifs du framework générique).

## 🛠️ Technologies

* **Moteur** : Unity **6000.2.6f1** (Unity 6)
* **Rendu** : Universal Render Pipeline (URP) **17.2.0**
* **Input** : Unity Input System **1.14.2**
* **2D** : Unity 2D Animation **12.0.2**, Sprite Shape, Tilemap & Extras
* **Import** : Aseprite Importer, PSD Importer
* **Outils** : Visual Scripting, Timeline

## 📁 Structure du projet

```
Assets/
├── Scenes/
│   └── SampleScene.unity
├── Settings/
│   ├── UniversalRP.asset
│   ├── Renderer2D.asset
│   └── Lit2DSceneTemplate.scenetemplate
├── InputSystem_Actions.inputactions
└── DefaultVolumeProfile.asset
```

## 🔐 Authentification & synchro (avec RPG-Gestionary)

> Implémentation exacte à confirmer avec l’API de RPG-Gestionary (schéma d’auth, type de jeton, endpoints). Le jeu **ne stocke jamais le mot de passe en clair**. 

### Variables d’environnement (Unity → Project Settings → Player → Scripting Define Symbols)

Créez un fichier `.env.example` (ou un ScriptableObject `RPGGestionarySettings` selon préférence) :

```
RPG_API_BASE_URL=
RPG_CLIENT_ID=
RPG_CLIENT_SECRET=   # si applicable (éviter côté client si le flux l’exige)
```

### Flux attendu (proposé)

1. Écran de connexion (identifiants RPG-Gestionary).
2. Appel API → **jeton** (session).
3. Hydratation du profil : univers, personnages, sessions autorisés.
4. Au lancement d’une session : push/pull des données nécessaires (maps, PNJ/ennemis, états, inventaire).
5. Sauvegarde régulière → plateforme (checkpoints).

## 🧩 Modules principaux

* **Core** : bootstrap, services, gestion des données & cache.
* **Auth** : UI + service d’auth.
* **Sync** : clients API (profils, univers, maps, sessions, inventaire, sauvegardes).
* **Map Editor (MJ)** : création/édition/assignation aux sessions (multi-sessions support). 
* **Session Runtime** : table virtuelle, initiative (si utile), outils MJ.
* **Dice Roller** : dX avec modificateurs/attributs paramétrables. 
* **Fog of War** : masquage/révélation par zones. 
* **NPC/Enemies** : gestion entités MJ. 
* **States/Effects** : application/suivi bonus-malus. 
* **Inventory** : CRUD MJ, lecture joueurs. 
* **Save** : synchronisation campagne. 

## 🚀 Installation

### Prérequis

* Unity **6000.2.6f1** ou supérieur
* Git

### Étapes

```bash
git clone https://github.com/milocartal/rpg-nexus.git
cd rpg-nexus
```

1. Ouvrir dans **Unity Hub** (Unity 6000.2.6f1).
2. Vérifier l’URP et l’Input System (auto-configurés).
3. Renseigner les variables d’API (voir plus haut).

## 🎯 Roadmap (V1)

* **Auth & profil** (base)
* **Map Editor MJ** (création, multi-sessions)
* **Sessions** (création/lancement)
* **Dés** (modificateurs)
* **Fog of War**
* **PNJ/Ennemis**
* **États/bonus/malus**
* **Inventaire** (gestion MJ, vue joueurs)
* **Sauvegarde** (push vers plateforme)

> Tous ces items proviennent du CdC client. 

## 🔧 Paramètres Unity recommandés

* **Plateforme cible** : PC, Mac & Linux Standalone
* **Mode de rendu** : 2D URP
* **Résolution** : 1920×1080 (adaptable)

## 🧪 Qualité & tests

* Tests d’intégration API (auth, profil, synchro)
* Tests de régression sur Fog of War & inventaire
* Playtests MJ/Joueurs (comportements session, dés, états)

## 🤝 Contribution

1. Fork
2. Branche : `feature/<NomFeature>`
3. Commits : clairs & atomiques
4. PR avec description, captures si UI MJ/Joueur

## 📓 Glossaire

* **MJ** : Maître du Jeu (rôle avec outils avancés)
* **Session** : instance de partie dans un univers
* **Map** : carte jouable ; peut être liée à plusieurs sessions 

## 📝 Licence

MIT — voir [LICENSE](LICENSE)

## 📞 Contact

Milo CARTAL — [@milocartal](https://github.com/milocartal)
Projet : [https://github.com/milocartal/rpg-nexus](https://github.com/milocartal/rpg-nexus)

## 🙏 Remerciements

* Unity Technologies
* Communauté Unity
* Contributeurs & testeurs
