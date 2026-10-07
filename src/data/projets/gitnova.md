---
title: GITNova — Plateforme de VM à la demande pour l'école
kind: Hackathon · Cloud & DevOps
summary: Plateforme qui permet aux étudiants de demander une machine virtuelle pour leurs cours, validée par un administrateur puis déployée automatiquement sur Infomaniak Public Cloud.
tags: [Terraform, Ansible, GitHub Actions, OpenStack, Entra ID]
order: 1
hackmd: https://hackmd.io/@Alexandra-ASSAGA/H1LpUedZfg
---

## Contexte
Projet réalisé en équipe de 5 lors du hackathon de juin 2026 au Geneva Institute of Technology. J'étais **responsable de l'infrastructure** et **cheffe de projet**.

## Problème
Les étudiants ont besoin d'environnements prêts à l'emploi pour leurs cours (Linux, web, réseau, cloud, Windows Server). Créer et configurer ces machines à la main prend du temps, et des VM oubliées génèrent des coûts inutiles.

## Solution
Un portail web, avec connexion via Microsoft Entra ID, où l'étudiant fait sa demande. Après validation par un administrateur, tout le cycle de vie de la VM est automatisé :

- **Terraform** crée la VM sur Infomaniak (OpenStack), avec une clé SSH unique et un réseau isolé par année d'études
- **Ansible** installe les outils du cours, à partir de 5 modèles : Linux, Web, Réseau, Cloud, Windows
- **GitHub Actions**, via un runner auto-hébergé, orchestre le déploiement, l'extinction automatique à 23 h et la destruction à la date d'expiration
- Les secrets sont chiffrés avec **Ansible Vault**, et la supervision repose sur **Prometheus + Grafana**

Principe clé : *aucune machine sans date de fin*.

## Résultat
- Chaîne complète automatisée : demande → validation → déploiement → configuration → extinction → destruction
- [À compléter : résultat de la démo, classement, retour du jury]
- Ce que j'en retiens : [À compléter en 1 phrase]