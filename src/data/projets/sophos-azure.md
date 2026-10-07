---
title: Architecture hybride Sophos Firewall + Microsoft Azure
kind: Cloud hybride · Réseau & Sécurité
summary: Connexion sécurisée d'un réseau local protégé par un pare-feu Sophos à Microsoft Azure via un tunnel VPN IPsec, avec gestion centralisée via Azure Arc et supervision Azure Monitor.
tags: [Azure, Sophos, VPN IPsec, Azure Arc, Azure Monitor]
order: 2
hackmd: https://hackmd.io/@Alexandra-ASSAGA/HJlI-sCZgGg
---

## Contexte
Projet personnel réalisé en mai 2026. Environnement : pare-feu Sophos SF01V (SFOS 22.0) protégeant un réseau local, et un abonnement Azure for Students (région Europe de l'Ouest).

## Problème
Beaucoup d'entreprises gardent une partie de leur infrastructure sur site tout en adoptant le cloud. Il faut alors relier les deux de façon **chiffrée**, et pouvoir **gérer et superviser** les machines locales depuis la même console que les ressources cloud.

## Solution
- **Tunnel VPN IPsec site-à-site** (IKEv2, AES-256 / SHA-256) entre le LAN Sophos (172.16.0.0/24) et un réseau virtuel Azure (10.0.0.0/16)
- **Azure VPN Gateway** basée sur les routes, avec une IP publique statique
- **Azure Arc** pour enregistrer la VM Windows locale comme machine hybride, gérable depuis le portail Azure
- **Azure Monitor** et un espace Log Analytics pour collecter les métriques de la machine

## Résultat
- Tunnel IPsec à l'état **Connected** et communication établie entre le réseau local et Azure
- VM locale visible et **Connected** dans Azure Arc
- Métriques remontées dans Azure Monitor
- Guide de déploiement complet documenté, avec plus de 10 captures de configuration