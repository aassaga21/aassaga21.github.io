---
title: Infrastructure Active Directory haute disponibilité sous Windows Server 2025
kind: Administration système · Windows Server
summary: Domaine Active Directory avec deux contrôleurs de domaine, DHCP en basculement automatique et stratégies de groupe pour une gestion centralisée et tolérante aux pannes.
tags: [Windows Server 2025, Active Directory, DNS, DHCP Failover, GPO, PowerShell]
order: 4
hackmd: https://hackmd.io/@Alexandra-ASSAGA/SyTqlaGi-g
---

## Contexte
Travail pratique du module 123 « Windows Server OS Administration — Advanced », réalisé du 23 au 26 mars 2026.

## Problème
Une entreprise doit gérer ses utilisateurs, ses postes et ses services réseau depuis un point central, **sans interruption de service** si un serveur tombe en panne.

## Solution
- **Deux contrôleurs de domaine** Windows Server 2025 pour le domaine `git.local`, avec réplication Active Directory
- **DNS** intégré à Active Directory
- **DHCP en mode failover** entre les deux serveurs : si l'un s'arrête, l'autre continue de distribuer les adresses
- **Stratégies de groupe (GPO)** appliquées aux utilisateurs : fond d'écran imposé, blocage du panneau de configuration et de l'invite de commandes
- Intégration d'un poste client Windows 10 au domaine

## Résultat
- Domaine fonctionnel, avec poste client et utilisateur intégrés
- Basculement DHCP **testé et validé**
- GPO appliquées et vérifiées sur le poste client
- Documentation complète, étape par étape, avec captures