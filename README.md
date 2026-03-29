# Configuration VirtualDJ pour Pioneer DDJ-200 sous Linux (Wine/Bottles)

Ce dépôt contient les fichiers de configuration XML pour utiliser le contrôleur MIDI Pioneer DDJ-200 avec VirtualDJ sur un système Linux, via Wine/Bottles.

L'objectif est de fournir une configuration fonctionnelle "clé en main" pour éviter les longues heures de dépannage.

## Contexte

Cette configuration a été testée avec la configuration suivante :

*   **OS :** Bazzite (Distribution Linux basée sur Fedora)
*   **VirtualDJ :** v2025 b8472 (version Windows)
*   **Contrôleur :** Pioneer DDJ-200 (connecté en USB)
*   **Environnement :** Bottles (utilisant Wine)

## Fichiers

Ce projet contient deux fichiers de mapping XML pour VirtualDJ :

1.  `devices/SIMPLE_MIDI_0_0.xml`: Définit les contrôles physiques du DDJ-200 (boutons, sliders, etc.) et leur assigne un nom.
2.  `mappers/SIMPLE_MIDI_0_0.xml`: Lie ces noms à des actions spécifiques dans VirtualDJ (VDJScript).

## Installation

1.  Assurez-vous que votre contrôleur DDJ-200 est correctement détecté par votre système Linux et par Wine/Bottles.
2.  Copiez les deux fichiers XML dans les répertoires correspondants de VirtualDJ au sein de votre "Bottle" :
    *   Copiez `devices/SIMPLE_MIDI_0_0.xml` dans :
        `.../drive_c/users/VOTRE_UTILISATEUR/AppData/Local/VirtualDJ/Devices/`
    *   Copiez `mappers/SIMPLE_MIDI_0_0.xml` dans :
        `.../drive_c/users/VOTRE_UTILISATEUR/AppData/Local/VirtualDJ/Mappers/`
3.  Lancez VirtualDJ. La configuration devrait être automatiquement chargée.

## Mappings principaux

Voici un aperçu des mappings personnalisés :

| Contrôle physique | Action VDJ |
| --- | --- |
| **PLAY** | `play_pause` (la LED clignote en lecture) |
| **CUE** | `cue_stop` |
| **SYNC** | `sync` |
| **SHIFT+PLAY** | `cue_play` (stutter) |
| **SHIFT+CUE** | `goto 0%` (retour au début) |
| **SHIFT+SYNC** | `pitch_reset` |
| **SHIFT+PFL** | `load` (charge la piste sélectionnée) |
| **JOGWHEEL (côté)** | `jogwheel` (pitch bend) |
| **SHIFT+JOGWHEEL (côté)** | `browser_scroll` (navigation dans la bibliothèque) |
| **JOGWHEEL (dessus)** | `touchwheel` (scratch) |
| **PADs 1-6** | Contrôle des Stems (Vocal, Instru, Bass, Kick, Hihat) |
| **SHIFT+PADs 1-4** | Boucles (8, 16, 32, 64 temps) |

Pour une liste complète, consultez les fichiers XML.
