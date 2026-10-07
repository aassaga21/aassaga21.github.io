---
title: Lab SCCM — Gestion de parc Windows avec Configuration Manager
kind: Administration système · Gestion de parc
summary: Reproduction d'un environnement d'entreprise avec Microsoft Configuration Manager (SCCM) pour automatiser le déploiement de logiciels et de mises à jour sur des postes Windows.
tags: [SCCM, SQL Server 2022, Windows Server 2022, Active Directory, Sophos, VMware]
order: 5
hackmd: https://hackmd.io/@Alexandra-ASSAGA/BkOMMfxZzl
---

## Contexte
Projet académique réalisé en juin 2026 au Geneva Institute of Technology, dans le cadre de ma spécialisation Cloud, Réseau et Automatisation. **Projet en cours** : l'enrôlement des postes clients est en cours de finalisation.

## Problème
En entreprise, installer des logiciels et des mises à jour poste par poste est impossible à grande échelle. Il faut un outil centralisé, relié à l'annuaire Active Directory, pour piloter tout le parc depuis une seule console.

## Solution
Un lab de 4 machines virtuelles sous VMware Workstation, derrière un pare-feu **Sophos** :
- Un **contrôleur de domaine** Active Directory / DNS
- Un serveur **SCCM** avec sa base **SQL Server 2022**
- Un **poste client** Windows
- **Extension du schéma Active Directory** pour SCCM, puis installation d'un site principal autonome

## Résultat
- Console Configuration Manager **opérationnelle** et site « GIT Lab » fonctionnel
- Infrastructure AD, SQL Server et SCCM installée et configurée de bout en bout
- Prochaine étape : finaliser l'enrôlement des clients et le déploiement d'applications
- Limites identifiées : lab sur un seul poste, ressources mémoire contraintes, pas encore de PKI (communication HTTP améliorée plutôt que HTTPS complet)