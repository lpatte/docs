---
title: "Création d'une ACL IP"
slug: ceph/create-an-ip-acl
excerpt: "Ce guide vous montre comment créer une ACL IP pour autoriser l'accès à votre cluster Ceph."
section: Cloud Disk Array
---

**Last update 26th March 2018**


## Utiliser l'interface web


> [!primary]
>
> L'utilisation d'une interface web est le moyen le plus simple de créer un ACL IP.
>

Tout d'abord, connectez-vous à [l’espace client](https://www.ovh.com/manager/dedicated/#/configuration){.external} et dans la rubrique Plates-formes et services vous trouverez le service Ceph.

Vous trouverez ici l'ACL existante, par défaut il n'y a pas d'ACL.


![Ceph pools](images/create_an_ip_acl_1.png){.thumbnail}

Obtenir votre adresse IP.


```bash
admin@server:~$ ip -4 a
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    inet 123.123.123.123/32 brd 234.234.234.234 scope global eth0
      valid_lft forever preferred_lft forever
```

Ajouter votre IP.


![Ceph pools](images/create_an_ip_acl_2.png){.thumbnail}

Et créer l'IP ACL.

Après la création de la pool d'adresses IP, vous êtes de retour au gestionnaire. Vous pouvez voir que le statut du pool a changé car l'ACL est en cours de création.


## Utiliser l'API

> [!api]
>
> @api {POST} /dedicated/ceph/{serviceName}/acl
>
serviceName est le fsid de votre cluster.

Vous pouvez vérifier la création d'une ACL en consultant la liste des ACL.


> [!api]
>
> @api {GET} /dedicated/ceph/{serviceName}/acl
>
Example:


```bash
GET /dedicated/ceph/98d166d8-7c88-47b7-9cb6-63acd5a59c15/acl
[
  {
    network: "123.123.123.123"
    id: 57054
    netmask: "255.255.255.255"
    family: "IPV4"
  }
]
```

## Aller plus loin

Rendez-vous sur notre chaîne Discord dédiée : <https://discord.gg/ovhcloud>. Posez des questions, fournissez des commentaires et interagissez directement avec l'équipe qui construit nos services de stockage et de sauvegarde.

Rejoignez notre communauté d'utilisateurs sur <https://community.ovh.com/>.
