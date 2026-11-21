# ENTREPRISE X
# Security Assessment Report

**Projet :** Entreprise X — Cybersecurity Lab  
**Type d'évaluation :** Network Security Assessment  
**Environnement :** Laboratoire virtualisé  
**Cible principale :** Metasploitable 2  
**Adresse IP de la cible :** `192.168.70.21`  
**Machine d'analyse :** Kali Linux (`192.168.2.3`)  
**Passerelle de sécurité :** pfSense (`192.168.2.254`)  
**Période :** Novembre 2026  
**Statut :** Rapport de laboratoire

---

## 1. Executive Summary

Ce projet consiste à concevoir et à tester un environnement de laboratoire réseau et cybersécurité représentant une infrastructure d'entreprise.

L'évaluation a combiné des activités Red Team et Blue Team.

La phase Red Team a permis d'identifier plusieurs services vulnérables sur Metasploitable 2 et de démontrer deux exploitations conduisant à un accès privilégié.

La phase Blue Team a permis de configurer Suricata en mode IDS, de détecter une activité de reconnaissance Nmap et d'analyser le trafic réseau avec tcpdump et Wireshark.

Les résultats démontrent l'importance de la mise à jour des services, de la surveillance réseau et de la mise en place de mécanismes de défense adaptés.

## 2. Architecture et périmètre

L'environnement repose sur des machines virtuelles et des équipements réseau simulés.

| Équipement | Adresse IP | Fonction |
|---|---|---|
| Kali Linux | 192.168.2.3 | Tests de sécurité et analyse |
| pfSense | 192.168.2.254 | Passerelle et sécurité réseau |
| Metasploitable 2 | 192.168.70.21 | Machine cible vulnérable |
| Réseau cible | 192.168.70.0/24 | Réseau de laboratoire |

Les tests ont été réalisés dans un environnement contrôlé et isolé.

## 3. Méthodologie

Le travail a suivi deux grandes approches :

### 3.1 Red Team

- Reconnaissance réseau avec Nmap.
- Énumération des services et des versions.
- Analyse des vulnérabilités potentielles.
- Validation contrôlée de vulnérabilités par exploitation.
- Conservation des résultats et des preuves.

### 3.2 Blue Team

- Configuration de Suricata sur pfSense.
- Activation des règles ET Open.
- Surveillance des événements réseau.
- Détection d'une activité de reconnaissance Nmap.
- Capture et analyse du trafic avec tcpdump et Wireshark.

## 4. Résultats Red Team

### 4.1 Services identifiés

| Service | Version observée | Observation |
|---|---|---|
| FTP | vsftpd 2.3.4 | Vulnérabilité historique exploitée |
| SMB | Samba 3.0.20 | Vulnérabilité historique exploitée |
| SSH | Service SSH | Version et configuration examinées |
| HTTP | Apache 2.2.8 / PHP 5.2.4 | Versions anciennes identifiées |

### 4.2 Exploitations validées

**vsftpd 2.3.4 — CVE-2011-2523**

L'exploitation contrôlée du service FTP a réussi et a permis d'obtenir un shell avec privilèges root sur la machine cible.

**Samba 3.0.20 — CVE-2007-2447**

L'exploitation contrôlée du service SMB a également réussi et a permis d'obtenir un shell avec privilèges root.

### 4.3 Autres observations

- Le protocole SMBv1 était pris en charge.
- Un accès anonyme en écriture au partage SMB `tmp` a été démontré.
- Le serveur HTTP utilisait des versions anciennes d'Apache et de PHP.
- Une tentative HTTP PUT sur l'URL de test a retourné le code HTTP 405.

## 5. Résultats Blue Team

### 5.1 Suricata IDS

Suricata a été installé et configuré sur l'interface OPT1 de pfSense.

Configuration et observations :

- Interface surveillée : OPT1 (`em1`).
- Mode de détection : IDS.
- Règles : ET Open.
- HOME_NET personnalisé : `192.168.70.0/24`.
- Journalisation EVE JSON activée.
- Journalisation HTTP activée.
- Blocking Mode : désactivé.

### 5.2 Détection Nmap

Une activité de reconnaissance provenant de Kali a été détectée.

| Élément | Résultat |
|---|---|
| Source | 192.168.2.3 |
| Destination | 192.168.70.21 |
| Signature | ET SCAN Possible Nmap User-Agent Observed |
| SID | 1:2024364 |
| Sévérité | 1 |

Cette alerte confirme que Suricata a identifié une activité correspondant à une règle de détection de scan.

### 5.3 Analyse des journaux

Les journaux suivants ont été générés :

- `alerts.log`
- `eve.json`
- `http.log`
- `suricata.log`

L'analyse de `eve.json` a confirmé la présence d'événements DNS et d'alertes Suricata.

Une alerte `SURICATA UDPv4 invalid checksum` (SID `1:2200075`) a également été observée. Elle nécessite une vérification complémentaire, car elle peut être liée à la capture des paquets ou aux mécanismes d'offloading de la virtualisation.

### 5.4 Analyse du trafic réseau

Les outils tcpdump et Wireshark ont été utilisés pour analyser les échanges entre Kali et Metasploitable.

Résultat de la capture :

- 5 requêtes ICMP Echo Request.
- 5 réponses ICMP Echo Reply.
- Aucun paquet perdu dans cette capture.
- Communication bidirectionnelle confirmée.

Le fichier PCAP utilisé est `entreprise-x-icmp.pcap`.

## 6. Évaluation des risques

| Risque constaté | Impact potentiel | Recommandation |
|---|---|---|
| Ancienne version de vsftpd | Accès non autorisé au système | Mettre à jour ou remplacer le service |
| Ancienne version de Samba | Exécution de commandes à distance | Mettre à jour Samba et désactiver SMBv1 |
| Partage SMB accessible en écriture anonyme | Modification de fichiers | Supprimer l'accès anonyme en écriture |
| Anciennes versions Apache et PHP | Exposition à des vulnérabilités connues | Mettre à jour les composants Web |
| Services réseau exposés | Augmentation de la surface d'attaque | Appliquer le principe du moindre privilège |

## 7. Recommandations générales

1. Maintenir les systèmes et services à jour.
2. Désactiver les protocoles obsolètes tels que SMBv1.
3. Limiter les accès anonymes et les permissions d'écriture.
4. Appliquer des règles de filtrage réseau adaptées.
5. Surveiller régulièrement les journaux de sécurité.
6. Utiliser Suricata pour détecter les activités suspectes.
7. Étudier le passage d'IDS à IPS après validation et tests contrôlés.
8. Conserver les preuves et documenter les incidents.

## 8. Limites de l'évaluation

Cette évaluation a été réalisée dans un laboratoire virtualisé et ne constitue pas un audit complet d'une infrastructure de production.

Le mode IPS de Suricata n'a pas encore été validé par un test de blocage. Les règles de filtrage pfSense et leurs effets doivent être évalués séparément.

L'analyse du trafic présentée dans ce rapport porte principalement sur les échanges ICMP capturés entre les deux machines.

## 9. Conclusion

Le laboratoire Entreprise X a permis de mettre en pratique plusieurs compétences en administration réseau et en cybersécurité.

La phase Red Team a démontré les conséquences de services obsolètes et mal sécurisés. La phase Blue Team a permis de mettre en place une première capacité de détection et d'analyse du trafic réseau.

Ce projet constitue une base pratique pour approfondir la sécurisation des infrastructures, la détection des menaces et la réponse aux incidents.

---

**Projet :** Entreprise X Cybersecurity Lab  
**Document :** Security Assessment Report  
**Classification :** Documentation technique de laboratoire