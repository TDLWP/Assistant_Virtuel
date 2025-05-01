# Echo Assistant 🔊

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) <!-- Remplacez par votre licence si différente -->
[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
<!-- Ajoutez d'autres badges si pertinent (build status, etc.) -->

**Echo Assistant est un assistant virtuel open-source basé sur une application web Flask, conçu pour être interactif et extensible.**

Il écoute vos commandes vocales (via l'API Web Speech du navigateur) ou textuelles et exécute diverses tâches, allant de la simple récupération d'informations au contrôle de l'ordinateur serveur.

<!-- Optionnel: Ajoutez un logo ou une capture d'écran ici -->
<!-- ![Echo Assistant Screenshot](link/to/your/screenshot.png) -->

---

## 📖 Table des Matières

*   [🌟 À Propos du Projet](#-à-propos-du-projet)
*   [✨ Fonctionnalités](#-fonctionnalités)
*   [🛠️ Technologies Utilisées](#️-technologies-utilisées)
*   [🚀 Démarrage Rapide](#-démarrage-rapide)
    *   [Prérequis](#prérequis)
    *   [Installation](#installation)
    *   [Configuration](#configuration)
    *   [Lancement](#lancement)
*   [💻 Utilisation](#-utilisation)
*   [⚙️ Configuration Avancée](#️-configuration-avancée)
    *   [Applications Rapides (`fast_apps.json`)](#applications-rapides-fast_appsjson)
    *   [Indexation des Fichiers](#indexation-des-fichiers)
*   [⚠️ Limitations et Sécurité](#️-limitations-et-sécurité)
*   [🗺️ Feuille de Route (Roadmap)](#️-feuille-de-route-roadmap)
*   [🤝 Contribution](#-contribution)
*   [📜 Licence](#-licence)
*   [🙏 Remerciements](#-remerciements)

---

## 🌟 À Propos du Projet

Echo Assistant a été développé dans le but de fournir une interface d'assistant virtuel accessible via un navigateur web. Il combine la reconnaissance vocale du navigateur avec un backend Python/Flask puissant pour traiter une large gamme de commandes. L'objectif est d'offrir une alternative personnalisable aux assistants commerciaux, tout en permettant un contrôle plus fin (et potentiellement risqué) de la machine serveur.

---

## ✨ Fonctionnalités

Echo Assistant offre un éventail de fonctionnalités, notamment :

*   **🗣️ Interaction Vocale & Textuelle :** Commandez l'assistant via le microphone (support navigateur requis) ou en tapant du texte.
*   **🌐 Informations & Recherche :**
    *   Météo actuelle pour une ville donnée.
    *   Heure actuelle.
    *   Calculs mathématiques simples et complexes.
    *   Recherche web via différents moteurs (Google, DuckDuckGo, YouTube, Wikipedia...).
    *   Traduction de texte entre plusieurs langues.
    *   Vérification de la connectivité Internet du serveur.
*   **🤖 Conversation :**
    *   Chatbot simple intégré (basé sur ChatterBot, si entraîné).
    *   Intégration avec WolframAlpha pour des questions de connaissances générales.
*   **📅 Gestion Personnelle (stocké sur le serveur) :**
    *   Création et listing de rappels basés sur le temps.
    *   Gestion de listes de tâches (ajout, complétion, suppression, listing).
    *   Prise de notes avec catégorisation (ajout, suppression, listing par catégorie).
    *   Planification d'événements simples (ajout, suppression, listing).
*   **🖥️ Contrôle du Serveur (Actions sur la machine où tourne Flask) :**
    *   Lancement rapide d'applications préconfigurées (`fast_apps.json`) ou trouvées dans le PATH.
    *   Lancement générique de fichiers ou applications par chemin.
    *   Prise de captures d'écran.
    *   Lecture/Écriture/Suppression de fichiers texte.
    *   Changement du fond d'écran (Windows, macOS, Linux/Gnome/Feh).
    *   Ajustement du volume système.
    *   Ajustement de la luminosité de l'écran (si supporté).
    *   **Actions Critiques :** Extinction, redémarrage, mise en veille de l'ordinateur serveur.
*   **🖱️ Contrôle UI du Serveur (Fenêtre Active) :**
    *   Simulation de frappe clavier ("dictée").
    *   Simulation d'appui sur des touches simples ou multiples (Entrée, Suppr, F5...).
    *   Simulation de raccourcis clavier (Ctrl+C, Alt+F4, Win+D...).
    *   Tentative de fermeture d'applications par nom de processus.
    *   Gestion de la fenêtre active (Maximiser, Minimiser, Fermer).
    *   Simulation du défilement de la molette (Scroll).
*   **📁 Indexation et Recherche de Fichiers (Serveur) :**
    *   Scan des répertoires spécifiés sur le serveur pour créer un index JSON.
    *   Recherche rapide de fichiers par nom et/ou type dans l'index.
    *   Commandes pour lancer l'indexation et vérifier son statut.
*   **⚙️ Configuration Assistant :**
    *   Changement de la langue de l'interface et de la réponse (Français/Anglais).
    *   Sélection de la voix de synthèse préférée (parmi celles disponibles sur le serveur pour la langue choisie).
*   **🎨 Interface Web :**
    *   Interface réactive (adaptée mobile/desktop).
    *   Thème clair / sombre personnalisable.
    *   Affichage clair de la conversation.
    *   Indicateurs de statut (Prêt, Écoute, Traitement, Erreur).

---

## 🛠️ Technologies Utilisées

*   **Backend :** Python 3, Flask
*   **Frontend :** HTML5, CSS3, JavaScript (ES6+)
*   **Reconnaissance Vocale :** API Web Speech (Navigateur)
*   **Synthèse Vocale :** API Web Speech (Navigateur) ou pyttsx3 (Serveur, via `VoiceAssistant`)
*   **Contrôle UI/Système :** `pyautogui`, `pycaw` (Win), `osascript` (macOS), `amixer` (Linux), `screen_brightness_control`, `psutil`, `subprocess`
*   **Web & API :** `requests`, `python-dotenv`, `deep-translator` (ou `googletrans`)
*   **Chatbot :** `ChatterBot` (Optionnel), WolframAlpha API
*   **Autres :** `Pillow` (pour OCR), `pytesseract` (+ installation Tesseract OCR)
*   **Base de Données :** SQLite (pour ChatterBot)
*   **Format de Données :** JSON (pour index fichiers, config apps)

---

## 🚀 Démarrage Rapide

Suivez ces étapes pour mettre en place et lancer Echo Assistant sur votre machine (serveur).

### Prérequis

*   **Python :** Version 3.8 ou supérieure recommandée. ([python.org](https://www.python.org/))
*   **pip :** Le gestionnaire de paquets Python (généralement inclus avec Python).
*   **git :** Pour cloner le dépôt. ([git-scm.com](https://git-scm.com/))
*   **Tesseract OCR :** Nécessaire pour la fonctionnalité d'extraction de texte depuis une image (`modules/utils/ocr.py`).
    *   **Windows :** Téléchargez l'installeur depuis [Tesseract at UB Mannheim](https://github.com/UB-Mannheim/tesseract/wiki). Assurez-vous d'ajouter Tesseract à votre PATH système pendant l'installation.
    *   **macOS :** `brew install tesseract` (si vous utilisez Homebrew).
    *   **Linux (Debian/Ubuntu) :** `sudo apt update && sudo apt install tesseract-ocr tesseract-ocr-fra tesseract-ocr-eng` (installez les packs de langue nécessaires).
    *   **Linux (Fedora) :** `sudo dnf install tesseract tesseract-langpack-fra tesseract-langpack-eng`.
*   **(Windows) Dépendances COM :** `pycaw` nécessite des composants COM. L'installation de `pywin32` (`pip install pywin32`) est généralement recommandée.
*   **(Linux) Dépendances Audio/Contrôle :** Vous pourriez avoir besoin d'installer `alsa-utils` (pour `amixer`) ou `feh` (pour le fond d'écran) via votre gestionnaire de paquets (`sudo apt install alsa-utils feh`).

### Installation

1.  **Cloner le dépôt :**
    ```bash
    git clone https://github.com/[votre-username]/EchoAssistant.git
    cd EchoAssistant
    ```
    *(Remplacez `[votre-username]` par votre nom d'utilisateur GitHub)*

2.  **Créer un environnement virtuel (recommandé) :**
    ```bash
    python -m venv venv
    ```
    *   Sous Windows : `.\venv\Scripts\activate`
    *   Sous macOS/Linux : `source venv/bin/activate`

3.  **Installer les dépendances Python :**
    ```bash
    pip install -r requirements.txt
    ```
    *(Assurez-vous d'avoir un fichier `requirements.txt` à jour. Voir section ci-dessous)*

### Configuration

1.  **Fichier `.env` :**
    *   Créez un fichier nommé `.env` à la racine du projet (`EchoAssistant/.env`).
    *   Ajoutez vos clés API et autres configurations :
        ```dotenv
        # Clé API OpenWeatherMap (obligatoire pour la météo)
        WEATHER_API_KEY=VOTRE_CLE_OPENWEATHERMAP

        # App ID WolframAlpha (obligatoire pour les questions générales)
        WOLFRAM_APP_ID=VOTRE_APP_ID_WOLFRAMALPHA

        # Configuration Flask (optionnel, valeurs par défaut montrées)
        # FLASK_DEBUG=True
        # FLASK_USE_RELOADER=True
        # FLASK_PORT=7000
        # FLASK_HOST=0.0.0.0 # 0.0.0.0 pour accès réseau, 127.0.0.1 pour local uniquement
        ```
    *   **Obtenir les clés :**
        *   OpenWeatherMap : Inscrivez-vous sur [openweathermap.org](https://openweathermap.org/) et générez une clé API (souvent gratuite pour un usage modéré).
        *   WolframAlpha : Créez un compte développeur sur [products.wolframalpha.com/api/](https://products.wolframalpha.com/api/) et obtenez un AppID.

2.  **Configuration des Applications Rapides (`fast_apps.json`) :**
    *   Vérifiez le fichier `fast_apps.json` à la racine du projet.
    *   **Adaptez les chemins d'accès** pour qu'ils correspondent aux emplacements des applications sur **VOTRE machine serveur**.
    *   Utilisez les alias que vous souhaitez prononcer (en minuscules).
    *   Vous pouvez utiliser des variables d'environnement comme `%LOCALAPPDATA%` (Win) ou `$HOME` (Linux/macOS).

3.  **Configuration de l'Indexation (`modules/utils/file_indexer.py`) :**
    *   Ouvrez le fichier `modules/utils/file_indexer.py`.
    *   Modifiez la liste `DEFAULT_DIRECTORIES_TO_INDEX` pour inclure les dossiers que vous souhaitez scanner sur votre serveur. **Attention :** Indexer des disques entiers peut être très long !

### Lancement

1.  **Activez votre environnement virtuel** (si vous en utilisez un).
2.  **Lancez l'application Flask :**
    ```bash
    python app.py
    ```
3.  **Accédez à l'interface :** Ouvrez votre navigateur web et allez à l'adresse indiquée dans la console (généralement `http://localhost:7000` ou `http://127.0.0.1:7000`). Vous verrez d'abord l'écran d'accueil, puis serez redirigé vers l'interface de chat.

---

## 💻 Utilisation

*   **Interface Web :** L'interface principale affiche la conversation et fournit une zone de saisie.
*   **Saisie Texte :** Tapez votre commande dans le champ en bas et appuyez sur Entrée ou cliquez sur l'icône d'envoi (<i class="fas fa-paper-plane"></i>).
*   **Commande Vocale :** Cliquez sur l'icône du microphone (<i class="fas fa-microphone"></i>). Le navigateur peut vous demander l'autorisation d'utiliser le micro. Parlez clairement après que l'indicateur passe à "Écoute". L'assistant traitera la commande une fois que vous aurez fini de parler. Cliquez à nouveau pour arrêter l'écoute manuellement.
*   **Commandes Disponibles :** Tapez `aide` ou `help` pour obtenir la liste complète des commandes reconnues (voir aussi la section [Fonctionnalités](#-fonctionnalités)).
*   **Paramètres :** Utilisez les menus déroulants en haut à droite pour changer la langue de l'interface/réponse et sélectionner votre voix de synthèse préférée (parmi celles du serveur). Utilisez le bouton <i class="fas fa-sun"></i>/<i class="fas fa-moon"></i> pour basculer entre les thèmes clair et sombre.

---

## ⚙️ Configuration Avancée

### Applications Rapides (`fast_apps.json`)

Ce fichier vous permet de définir des alias (raccourcis) pour lancer rapidement des applications sur le serveur.

*   **Format :** Fichier JSON contenant des paires clé-valeur.
    *   **Clé :** L'alias que vous utiliserez dans la commande (ex: `"chrome"`, `"éditeur de texte"`). Mettez-le en minuscules.
    *   **Valeur :** Le chemin complet vers l'exécutable ou la commande à lancer sur le serveur.
        *   Utilisez des doubles backslashes (`\\`) pour les chemins Windows ou des raw strings (`r"C:\path"`).
        *   Vous pouvez inclure des arguments (ex: `"%LOCALAPPDATA%\\Discord\\Update.exe --processStart Discord.exe"`).
        *   Utilisez des variables d'environnement comme `%LOCALAPPDATA%`, `%APPDATA%` (Win) ou `$HOME` (Linux/macOS).
        *   Si vous donnez juste un nom d'exécutable (ex: `"notepad.exe"`), le système cherchera dans le PATH du serveur.

### Indexation des Fichiers

Cette fonctionnalité permet de rechercher rapidement des fichiers sur le serveur.

1.  **Configuration :** Modifiez `DEFAULT_DIRECTORIES_TO_INDEX` dans `modules/utils/file_indexer.py` pour spécifier les dossiers à scanner.
2.  **Lancement de l'Indexation :** Utilisez la commande vocale/texte `mets à jour l'index des fichiers` ou `update index`. L'indexation se fait en arrière-plan et peut prendre du temps, surtout la première fois ou si les dossiers sont volumineux. L'index est sauvegardé dans `file_index.json`.
3.  **Vérification du Statut :** Utilisez la commande `statut index` ou `index status` pour voir quand l'index a été mis à jour pour la dernière fois et s'il est en cours d'indexation.
4.  **Recherche :** Utilisez les commandes :
    *   `cherche fichier [terme]` (ex: `cherche fichier rapport annuel`)
    *   `trouve fichier [type] [terme]` (ex: `trouve fichier document budget`, `cherche fichier image logo`)
    *   Les types reconnus sont définis dans `FILE_EXTENSIONS` dans `file_indexer.py` (app, musique, vidéo, image, document, etc.).

---

## ⚠️ Limitations et Sécurité

*   **Exécution Côté Serveur :** **TRÈS IMPORTANT !** Toutes les commandes affectant le système (lancement d'applications, contrôle UI, gestion de fichiers, extinction, etc.) s'exécutent sur la **machine où le serveur Flask est lancé**, PAS sur l'ordinateur de l'utilisateur accédant via le navigateur (sauf si c'est la même machine).
*   **Sécurité :** Activer des commandes comme `shutdown`, `restart`, `delete file`, `write file`, ou le contrôle UI (`pyautogui`) via une interface web est **extrêmement risqué**, surtout si le serveur est accessible depuis l'extérieur de votre réseau local. `pyautogui` en particulier donne un contrôle quasi total du bureau du serveur. **Utilisez ces fonctionnalités à vos risques et périls et ne rendez PAS le serveur accessible publiquement avec ces commandes activées.** Envisagez de les désactiver ou de les protéger par authentification si nécessaire.
*   **Fiabilité du Contrôle UI :** Le contrôle de l'interface graphique via `pyautogui` est intrinsèquement fragile. Des changements mineurs dans l'interface d'une application, des fenêtres qui ne sont pas au premier plan sur le serveur, ou des résolutions d'écran différentes peuvent faire échouer les commandes `tape`, `appuie sur`, `ferme fenêtre`, etc.
*   **Reconnaissance/Synthèse Vocale :** La qualité et la disponibilité dépendent fortement du navigateur utilisé et des API Web Speech. Toutes les voix listées par le serveur peuvent ne pas être disponibles ou sonner différemment dans le navigateur.
*   **Indexation Fichiers :** L'index n'est pas mis à jour automatiquement en temps réel. Vous devez utiliser la commande `mets à jour l'index` pour refléter les nouveaux fichiers ou les suppressions. L'indexation peut consommer des ressources (CPU/Disque) pendant son exécution.

---

## 🗺️ Feuille de Route (Roadmap)

*   [ ] Améliorer la gestion des erreurs et les retours utilisateur.
*   [ ] Ajouter un système d'authentification simple pour protéger les commandes sensibles.
*   [ ] Explorer l'intégration avec d'autres API (Calendrier, Domotique...).
*   [ ] Permettre la configuration des répertoires d'indexation via l'interface ou un fichier de config.
*   [ ] Améliorer la pertinence de la recherche de fichiers indexés.
*   [ ] Ajouter des tests unitaires et d'intégration.
*   [ ] Internationalisation plus poussée de l'interface.

*(N'hésitez pas à ajouter vos propres idées ici !)*

---

## 🤝 Contribution

Les contributions sont les bienvenues ! Si vous souhaitez améliorer Echo Assistant, veuillez consulter le fichier [`CONTRIBUTING.md`](CONTRIBUTING.md) pour connaître les directives.

Quelques façons de contribuer :

*   Signaler des bugs ou proposer des fonctionnalités via les [Issues](https://github.com/[votre-username]/EchoAssistant/issues).
*   Proposer des améliorations de code via des Pull Requests.
*   Améliorer la documentation.
*   Ajouter le support pour de nouvelles langues ou commandes.

---

## 📜 Licence

Ce projet est distribué sous la Licence MIT. Voir le fichier [`LICENSE`](LICENSE) pour plus de détails.

---

## 🙏 Remerciements

*   Aux développeurs de Flask et de toutes les bibliothèques Python utilisées.
*   À la communauté open-source pour l'inspiration et les outils.
*   *(Ajoutez d'autres remerciements si nécessaire)*"# Assistant_Virtuelle" 
"# Assistant_Virtuelle" 
"# Assistant_Virtuel" 
"# Assistant_Virtuel" 
"# Assistant_Virtuelle" 
