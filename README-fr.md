# Mooring Design Simulator

[English version](README.md).

**Concevoir, simuler et préparer des mouillages océanographiques de subsurface.**

Mooring Design Simulator est une application de bureau qui associe un concepteur graphique, une bibliothèque de composants et un calcul d’équilibre statique. Elle permet de comparer un mouillage sans courant et sous différents profils de courant, puis de préparer les rapports et documents nécessaires à sa mise en œuvre.

**Version documentée : 2.1.0-RC11 — préversion.**

[Télécharger l’application](https://github.com/jgrelet/MooringDesignSimulator/releases/tag/v2.1.0-RC11) · [Documentation française](https://github.com/jgrelet/MooringDesignSimulator/wiki/Home-fr) · [English documentation](https://github.com/jgrelet/MooringDesignSimulator/wiki/Home) · [Historique des versions](CHANGELOG.md)

## Fonctionnalités

- Concevoir plusieurs mouillages dans des onglets indépendants ; dupliquer un mouillage ou copier des groupes de composants avec leurs instruments clampés.
- Définir les positions imposées, verrouiller les longueurs standards préparées et adapter la ligne à la bathymétrie.
- Gérer une bibliothèque de flotteurs, instruments, câbles, cordages, largueurs, terminaux et lests.
- Définir les profils de courant par saisie ou import de fichiers au format CSV, TXT ou NetCDF.
- Comparer les profondeurs, tensions, allongements, poids de lest et indicateurs de déploiement/récupération dans les tableaux et graphes.
- Générer des rapports PDF et des fiches de préparation A3 avec marquages des cordages et numéros de série des instruments.
- Importer et exporter les projets au format historique Mooring Simulator V1, avec contrôles de compatibilité.

![Conception de plusieurs mouillages](https://raw.githubusercontent.com/wiki/jgrelet/MooringDesignSimulator/images/mooring-designer-rc8.png)

<p align="center"><em>Conception sur deux colonnes, plusieurs mouillages ouverts et onglets de simulation.</em></p>

![Résultats de simulation](https://raw.githubusercontent.com/wiki/jgrelet/MooringDesignSimulator/images/mooring-simulation-results-rc8.png)

<p align="center"><em>Résultats de la simulation en statique ou avec courant.</em></p>

## Démarrer

1. [Télécharger l’archive d’installation](https://github.com/jgrelet/MooringDesignSimulator/releases/tag/v2.1.0-RC11) correspondant au système et au processeur : Windows, Linux ou macOS. Les archives Windows et macOS sont des ZIP ; celles de Linux sont au format `.tar.gz`. Pour macOS, choisir arm64 pour Apple Silicon (M1–M4) ou amd64 pour Intel. Extraire entièrement l’archive.
2. Conserver l’application avec les dossiers `library/` et `examples/` fournis.
3. Ouvrir un exemple, adapter sa conception et lancer la simulation.

**Mise à jour sous Windows :** si une installation précédente contient déjà les dossiers `library/` et `examples/`, il suffit de télécharger `mooringDesignSimulator.exe` et de remplacer l’exécutable existant dans ce dossier d’installation. Télécharger l’archive complète pour obtenir également les dernières versions de la bibliothèque et des exemples fournis.

La documentation se trouve dans le [wiki du projet](https://github.com/jgrelet/MooringDesignSimulator/wiki/Home-fr). Consulter [Installation et premier lancement](https://github.com/jgrelet/MooringDesignSimulator/wiki/Installation-fr), puis le [guide d’utilisation](https://github.com/jgrelet/MooringDesignSimulator/wiki/UseApplication-fr). L’application utilise un solveur statique et des modèles simplifiés de lancement et de récupération ; elle ne réalise pas une simulation dynamique complète.

Le code source est maintenu dans un dépôt privé. Ce dépôt public présente le logiciel ; sa documentation est maintenue dans le wiki.

**Auteur : J. Grelet.**
