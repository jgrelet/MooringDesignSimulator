# Mooring Design Simulator

[![CI](https://github.com/jgrelet/Mooring-simulator-v2/actions/workflows/ci.yml/badge.svg)](https://github.com/jgrelet/Mooring-simulator-v2/actions/workflows/ci.yml)
[![Release](https://github.com/jgrelet/Mooring-simulator-v2/actions/workflows/release.yml/badge.svg)](https://github.com/jgrelet/Mooring-simulator-v2/actions/workflows/release.yml)
[![CI](https://github.com/jgrelet/MDS-rs/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/jgrelet/MDS-rs/actions/workflows/ci.yml)
[![Release](https://github.com/jgrelet/MDS-rs/actions/workflows/release.yml/badge.svg)](https://github.com/jgrelet/MDS-rs/actions/workflows/release.yml)

[English version](README.md).

**Concevoir, simuler et préparer des mouillages océanographiques de subsurface.**

Mooring Design Simulator est une application de bureau qui associe un concepteur graphique, une bibliothèque de composants et un calcul d’équilibre statique. Elle permet de comparer un mouillage sans courant et sous différents profils de courant, puis de préparer les rapports et documents nécessaires à sa mise en œuvre.

Mooring Design Simulator est issu du travail d’Arnaud Le Fur, alors élève ingénieur, réalisé en 2014 au LOPS de l’Ifremer dans le cadre du stage « Développement et validation d’un logiciel de simulation de ligne de mouillage ». Ce travail avait pour objectif de remplacer deux logiciels utilisés par la communauté océanographique, tous deux développés en MATLAB : Runmoor et Mooring Design and Dynamics (MDD). Cette première version, écrite en Python 2 avec Qt4, n’étant plus maintenable et présentant certaines limitations, nous avons entrepris de reprendre son développement sous Python 3.14 et PySide6.

**Version documentée : 2.1.0-RC16 — préversion de test.**

La documentation et les liens de téléchargement GitHub ci-dessous concernent la préversion de test RC16.

[Télécharger depuis GitHub](https://github.com/jgrelet/MooringDesignSimulator/releases/tag/v2.1.0-RC16) · [Dossier OneDrive](https://1drv.ms/f/c/be92ea594b94cdce/IgAfXMAZMKe4RaSl96BxX8dJAfWHU9u-r8ky-FK3yJPCdiw?e=hUyrJx) · [Documentation française](https://github.com/jgrelet/MooringDesignSimulator/wiki/Home-fr) · [English documentation](https://github.com/jgrelet/MooringDesignSimulator/wiki/Home) · [Historique des versions](CHANGELOG.md)

## Fonctionnalités

- Adopter les longueurs de câbles et positions de clamps préparées comme conception modifiable, conserver les objectifs scientifiques et recalculer les scénarios de courant de façon cohérente ; identifier l’origine des résultats et retrouver la préparation dans les rapports PDF et Deployment Sheets.
- Concevoir plusieurs mouillages dans des onglets indépendants ; dupliquer un mouillage ou copier des groupes de composants avec leurs instruments clampés.
- Définir les positions imposées, verrouiller les longueurs standards préparées et adapter la ligne à la bathymétrie.
- Gérer une bibliothèque de flotteurs, instruments, câbles, cordages, largueurs, terminaux et lests.
- Définir les profils de courant par saisie ou import de fichiers au format CSV, TXT ou NetCDF.
- Comparer les profondeurs, tensions, allongements, poids de lest et indicateurs de déploiement/récupération dans les tableaux et graphes.
- Générer des rapports PDF et des fiches de préparation A3 avec marquages des cordages et numéros de série des instruments.
- Importer et exporter les projets au format historique Mooring Simulator V1, avec contrôles de compatibilité.

![Vue de conception RC13](https://raw.githubusercontent.com/wiki/jgrelet/MooringDesignSimulator/images/mooring-designer-rc13.png)

<p align="center"><em>RC13 — Conception sur deux colonnes, librairie d’instruments, éditeur de composants et onglets de simulation.</em></p>

![Résultats de simulation](https://raw.githubusercontent.com/wiki/jgrelet/MooringDesignSimulator/images/mooring-simulation-results-rc8.png)

<p align="center"><em>Résultats de la simulation en statique ou avec courant.</em></p>

## Démarrer

1. Télécharger l’archive d’installation depuis [GitHub](https://github.com/jgrelet/MooringDesignSimulator/releases/tag/v2.1.0-RC16), correspondant au système et au processeur : `mooringDesignSimulator-windows-amd64.zip`, `mooringDesignSimulator-linux-amd64.tar.gz` ou `mooringDesignSimulator-linux-arm64.tar.gz`. Extraire entièrement l’archive. Les paquets macOS sont construits sur demande et ne sont pas inclus dans cette publication RC16.
2. Conserver l’application avec les dossiers `library/` et `examples/` fournis.
3. Ouvrir un exemple, adapter sa conception et lancer la simulation.

**Mise à jour sous Windows :** si une installation précédente contient déjà les dossiers `library/` et `examples/`, il suffit de télécharger `mooringDesignSimulator.exe` et de remplacer l’exécutable existant dans ce dossier d’installation. Télécharger l’archive complète pour obtenir également les dernières versions de la bibliothèque et des exemples fournis.

La documentation se trouve dans le [wiki du projet](https://github.com/jgrelet/MooringDesignSimulator/wiki/Home-fr). Consulter [Installation et premier lancement](https://github.com/jgrelet/MooringDesignSimulator/wiki/Installation-fr), puis le [guide d’utilisation](https://github.com/jgrelet/MooringDesignSimulator/wiki/UseApplication-fr). L’application utilise un solveur statique et des modèles simplifiés de lancement et de récupération ; elle ne réalise pas une simulation dynamique complète.

Le code source est maintenu dans un dépôt privé. Ce dépôt public présente le logiciel ; sa documentation est maintenue dans le wiki.

**Auteur : J. Grelet.**
