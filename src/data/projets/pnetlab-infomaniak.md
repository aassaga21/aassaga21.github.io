---
title: Lab d'émulation réseau PNETLab sur Infomaniak, déployé avec Terraform
kind: Infrastructure as Code · Réseau
summary: Déploiement automatisé d'une plateforme d'émulation réseau multi-constructeurs sur Infomaniak Public Cloud, entièrement reproductible grâce à Terraform.
tags: [Terraform, OpenStack, Infomaniak, QEMU/KVM, cloud-init]
order: 3
hackmd: https://hackmd.io/@Alexandra-ASSAGA/H18lx2xyze
---

## Contexte
Projet personnel réalisé en mai 2026. PNETLab est une plateforme qui permet de simuler des équipements réseau professionnels (routeurs, switchs, pare-feu) pour s'entraîner et préparer des certifications.

## Problème
Disposer d'un lab réseau puissant sans matériel physique, et pouvoir le **recréer ou le détruire en une commande**. Difficulté supplémentaire : l'image officielle de PNETLab (format OVA) n'est pas directement compatible avec l'environnement OpenStack d'Infomaniak.

## Solution
- **Conversion de l'image** OVA → QCOW2 avec `qemu-img`, puis import sur Infomaniak
- **Terraform** (provider OpenStack) décrit toute l'infrastructure : réseau privé, routeur, groupes de sécurité, VM (8 vCPU, 32 Go de RAM), volume persistant de 250 Go et IP flottante
- **cloud-init** configure automatiquement la machine au premier démarrage
- **ishare2** permet d'ajouter les images des équipements réseau

## Résultat
- Plateforme PNETLab opérationnelle, accessible en web et en SSH
- Infrastructure **100 % reproductible** : `terraform apply` pour créer, `terraform destroy` pour tout supprimer
- Limite identifiée et documentée : le *nested KVM* n'est pas encore activé chez l'hébergeur (demande au support en cours), ce qui restreint les types d'équipements émulables
- Documentation complète, avec plus de 35 captures