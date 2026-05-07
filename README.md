# 🌌 TP 3 : Pilotage d'un Écran LCD via I2C - Systèmes Embarqués

Bienvenue dans le **Travail Pratique N°3** ! L'objectif de ce projet est de configurer et d'utiliser le bus de communication série synchrone **I2C** pour interagir avec un écran LCD 16x2 via le microcontrôleur **STM32 Nucleo-C031C6**.

Ce projet intègre l'importation de bibliothèques externes (`LCD_16X2.h` et `.c`) et propose un **Jumeau Numérique Web interactif** permettant de simuler l'écran LCD et de visualiser en direct la mise en forme de données issues de l'ADC.

## 🚀 Fonctionnalités du Compte-Rendu Interactif

Le fichier `compte_rendu_tp3.html` est une application web autonome au design "Deep Space" comprenant :
* **Un Simulateur LCD I2C Dynamique :** Visualisation d'un écran 16x2 rétroéclairé bleu. 
* **Onglet "Manip 1" :** Exécution d'une séquence statique ("Embedded System" / "Lab Session") illustrant l'utilisation des fonctions de base (`lcd_print`, `lcd_set_cursor`).
* **Onglet "Manip 2" (Défi Post-Lab) :** Intégration du TP2. Un potentiomètre virtuel pilote en temps réel les valeurs brutes et la tension affichées sur l'écran LCD via un formatage de chaîne de caractères (`sprintf`).
* **Analyse Post-Lab complète :** Explications détaillées sur les avantages matériels du bus I2C (économie de broches GPIO) et la gestion matérielle des adresses réseau (0x27) pour éviter les collisions de données.

## 📋 Manipulations Réalisées (Code C)

1. **Configuration Matérielle (CubeMX) :** Activation de l'I2C1 sur les broches `PB8` (SCL) et `PB9` (SDA).
2. **Affichage Statique :** Initialisation correcte (`lcd_init()`) en dehors de la boucle principale pour éviter le scintillement, suivi de cycles d'écriture et d'effacement (`lcd_clear()`) dans la boucle infinie.
3. **Affichage Dynamique (Capteur + I2C) :** Conversion d'une valeur numérique (entière et flottante) en caractères ASCII via la fonction `<stdio.h> sprintf()` avant de l'envoyer sur le bus I2C.

## 🛠️ Matériel & Outils Requis

* **Carte :** STM32 Nucleo-C031C6 (Physique ou simulation via [Wokwi](https://wokwi.com/stm32)).
* **Composants :** 1x Écran LCD 16x2 avec module adaptateur I2C PCF8574, 1x Potentiomètre analogique.
* **Environnement C :** STM32CubeIDE (avec inclusion des drivers `LCD_16X2`).
* **Environnement Web :** Navigateur web moderne pour le Jumeau Numérique.

## ⚙️ Instructions de Simulation (Wokwi)

1. Créez un projet "STM32 Nucleo64 C031C6" sur Wokwi.
2. Ajoutez un composant `LCD1602 I2C`.
3. Connectez :
   * La broche `SCL` du LCD à la broche **PB8** du STM32.
   * La broche `SDA` du LCD à la broche **PB9** du STM32.
   * `VCC` à `5V` (ou `3V3` selon le modèle de l'écran Wokwi) et `GND` à `GND`.
4. Ajoutez les fichiers `LCD_16X2.h` et `LCD_16X2.c` à votre projet Wokwi et mettez à jour votre `main.c`.
5. Lancez la simulation.

## 👥 Équipe du Projet

**Année Universitaire :** 2025/2026
* **Binôme :** Dahane Ahmed Lamine & Tabbi Meriem
* **Enseignante Responsable :** Mme. Afaf Saoud
