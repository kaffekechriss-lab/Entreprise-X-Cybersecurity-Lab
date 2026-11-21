# Analyse des journaux EVE JSON — Suricata

## 1. Objectif

Vérifier le fonctionnement de la journalisation EVE JSON de Suricata sur pfSense et analyser les événements réseau enregistrés.

## 2. Emplacement des journaux

Répertoire :

`/var/log/suricata/suricata_em17947/`

Fichiers observés :

- `alerts.log` : 418 KB
- `eve.json` : 4.2 MB
- `http.log` : 179 KB
- `suricata.log` : 3.3 KB

## 3. Analyse d'un événement

Signature : `SURICATA UDPv4 invalid checksum`

- SID : 2200075
- Source : 192.168.2.254
- Destination : 8.8.8.8
- Protocole : UDP
- Port destination : 53
- Application : DNS
- Sévérité : 3
- Action : allowed

## 4. Interprétation

Suricata a détecté un paquet UDP présentant un checksum invalide pendant une communication DNS.

Cette anomalie peut être liée aux mécanismes de checksum offloading de l'environnement virtualisé. Cette hypothèse reste à confirmer par une analyse complémentaire des paquets.

L'action `allowed` indique que le paquet n'a pas été bloqué.

## 5. Résultat

La présence de données dans `eve.json`, `alerts.log` et `http.log` confirme que Suricata enregistre des événements réseau.

La journalisation EVE JSON fonctionne correctement.

## 6. Conclusion

Le mécanisme de détection et de journalisation de Suricata est opérationnel en mode IDS. Les événements peuvent être exploités pour les analyses de sécurité et la production de rapports.