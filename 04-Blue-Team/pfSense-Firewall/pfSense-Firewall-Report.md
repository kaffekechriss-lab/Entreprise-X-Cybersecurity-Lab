# pfSense Firewall — Security Configuration Report

## 1. Objectif

Documenter la configuration réseau et les mécanismes de sécurité de pfSense dans le laboratoire Entreprise X.

## 2. Environnement

| Élément | Configuration |
|---|---|
| Pare-feu | pfSense |
| Interface surveillée | OPT1 |
| Adresse OPT1 | 192.168.2.254 |
| Réseau interne cible | 192.168.70.0/24 |
| Passerelle interne | GW_R1 |
| Passerelle Internet | GW_KALI_INTERNET |

## 3. Configuration réseau

pfSense assure le routage entre le réseau de Kali et les réseaux internes du laboratoire.

Les routes internes utilisent la passerelle GW_R1. La sortie Internet utilise GW_KALI_INTERNET.

La configuration DNS utilise notamment les serveurs 1.1.1.1 et 8.8.8.8.

## 4. Surveillance de sécurité

Suricata est installé sur pfSense et activé sur OPT1.

Configuration :
- Interface : OPT1 (em1).
- Description : BLUE_TEAM.
- Mode : IDS.
- Règles : Emerging Threats Open (ET Open).
- HOME_NET : 192.168.70.0/24.
- Journalisation EVE JSON activée.
- Journalisation des alertes activée.

## 5. Tests et observations

Les tests de détection IDS ont été réalisés depuis Kali Linux vers Metasploitable 2.

Une activité de reconnaissance Nmap a été détectée par Suricata.

Signature observée : ET SCAN Possible Nmap User-Agent Observed.

SID : 1:2024364.

Source : 192.168.2.3.

Destination : 192.168.70.21.

Les événements ont également été examinés dans les journaux Suricata.

## 6. Limites des tests

Les tests effectués ont validé la détection IDS.

Le mode IPS et le blocage automatique du trafic n'ont pas été testés. Le Blocking Mode est resté désactivé afin de conserver le fonctionnement normal du laboratoire.

La validation du filtrage par règles firewall pfSense doit être distinguée de la validation du mécanisme IPS de Suricata.

## 7. Conclusion

pfSense assure les fonctions de routage et de sécurité réseau du laboratoire Entreprise X.

L'intégration de Suricata apporte une capacité de détection des activités suspectes.

La détection IDS a été validée. La prévention IPS reste une activité non réalisée dans le cadre de cette phase.