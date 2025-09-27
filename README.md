# RPG Nexus

Un projet de jeu de rôle (RPG) développé avec Unity, conçu comme une plateforme modulaire et évolutive pour créer des expériences RPG immersives.

## 🎮 Description

RPG Nexus est un framework de base pour développer des jeux de rôle en 2D utilisant Unity. Le projet fournit une architecture solide et extensible pour créer des RPG avec des systèmes de combat, d'inventaire, de progression de personnages et bien plus.

## 🛠️ Technologies utilisées

- **Moteur** : Unity 6000.2.6f1 (Unity 6)
- **Pipeline de rendu** : Universal Render Pipeline (URP) 17.2.0
- **Système d'entrée** : Unity Input System 1.14.2
- **Animation 2D** : Unity 2D Animation 12.0.2
- **Support d'assets** : Aseprite Importer, PSD Importer
- **Outils 2D** : Sprite Shape, Tilemap, Tilemap Extras

## 📁 Structure du projet

```
Assets/
├── Scenes/
│   └── SampleScene.unity          # Scène principale de démonstration
├── Settings/
│   ├── UniversalRP.asset          # Configuration URP
│   ├── Renderer2D.asset           # Renderer 2D
│   └── Lit2DSceneTemplate.scenetemplate
├── InputSystem_Actions.inputactions  # Configuration des contrôles
└── DefaultVolumeProfile.asset     # Profil de post-processing
```

## 🚀 Installation et configuration

### Prérequis

- Unity 6000.2.6f1 ou version supérieure
- Git

### Étapes d'installation

1. **Cloner le repository**

   ```bash
   git clone https://github.com/milocartal/rpg-nexus.git
   cd rpg-nexus
   ```

2. **Ouvrir dans Unity**

   - Lancez Unity Hub
   - Cliquez sur "Add project from disk"
   - Sélectionnez le dossier `rpg-nexus`
   - Ouvrez le projet avec Unity 6000.2.6f1

3. **Configuration initiale**
   - Le projet utilisera automatiquement l'Universal Render Pipeline configuré
   - Les systèmes d'entrée sont préconfigurés via Input System

## 🎯 Fonctionnalités prévues

- [ ] Système de combat au tour par tour
- [ ] Gestion des personnages et statistiques
- [ ] Système d'inventaire et d'objets
- [ ] Dialogue et système de quêtes
- [ ] Système de progression et de niveaux
- [ ] Interface utilisateur responsive
- [ ] Sauvegarde et chargement de parties
- [ ] Système audio et effets sonores

## 🔧 Configuration Unity

### Packages installés

- **2D** : Animation, Sprite Shape, Tilemap
- **Rendering** : Universal RP
- **Input** : Input System
- **Tools** : Visual Scripting, Timeline
- **Import** : Aseprite, PSD Importer

### Paramètres recommandés

- **Plateforme cible** : PC, Mac & Linux Standalone
- **Mode de rendu** : 2D URP
- **Résolution** : 1920x1080 (adaptable)

## 🤝 Contribution

Les contributions sont les bienvenues ! Pour contribuer :

1. Forkez le projet
2. Créez une branche pour votre fonctionnalité (`git checkout -b feature/AmazingFeature`)
3. Committez vos changements (`git commit -m 'Add some AmazingFeature'`)
4. Poussez vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrez une Pull Request

## 📝 Licence

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

## 📞 Contact

Milo CARTAL - [@milocartal](https://github.com/milocartal)

Lien du projet : [https://github.com/milocartal/rpg-nexus](https://github.com/milocartal/rpg-nexus)

## 🙏 Remerciements

- Unity Technologies pour l'excellent moteur de jeu
- La communauté Unity pour les ressources et tutoriels
- Tous les contributeurs qui aident à améliorer ce projet
