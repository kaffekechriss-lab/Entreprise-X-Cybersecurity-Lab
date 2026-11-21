# Traffic Analysis Report — Entreprise X

## 1. Objectif

Analyser le trafic réseau entre Kali Linux et Metasploitable 2 afin de vérifier les échanges ICMP et de se familiariser avec les outils tcpdump et Wireshark.

## 2. Environnement de test

| Équipement | Adresse IP | Rôle |
|---|---|---|
| Kali Linux | 192.168.2.3 | Machine d'analyse |
| Metasploitable 2 | 192.168.70.21 | Machine cible |
| pfSense | 192.168.2.254 | Passerelle du laboratoire |

## 3. Outils utilisés

- tcpdump : capture et lecture du trafic réseau.
- Wireshark : analyse graphique des paquets.
- ICMP : protocole utilisé pour tester la communication.

## 4. Méthodologie

### 4.1 Capture avec tcpdump

Commande utilisée :

```bash
sudo tcpdump -i eth1 -nn host 192.168.70.21
```

Résultat : observation des requêtes ICMP envoyées par Kali et des réponses retournées par Metasploitable.

### 4.2 Enregistrement de la capture

Commande utilisée :

```bash
sudo tcpdump -i eth1 -nn -s 0 -w ~/Desktop/entreprise-x-icmp.pcap host 192.168.70.21
```

La capture a été enregistrée au format PCAP pour permettre son analyse ultérieure.

### 4.3 Vérification avec tcpdump

Commande utilisée :

```bash
tcpdump -nn -r ~/Desktop/entreprise-x-icmp.pcap
```

Résultat observé :
- 5 requêtes ICMP Echo Request.
- 5 réponses ICMP Echo Reply.
- Communication bidirectionnelle réussie.

### 4.4 Analyse avec Wireshark

Le fichier PCAP a été ouvert dans Wireshark avec le filtre d'affichage :

```text
icmp
```

Les échanges ICMP ont été visualisés et analysés.

## 5. Résultats

| Indicateur | Résultat |
|---|---|
| Protocole analysé | ICMP |
| Adresse source | 192.168.2.3 |
| Adresse destination | 192.168.70.21 |
| Requêtes envoyées | 5 |
| Réponses reçues | 5 |
| Perte observée | 0 paquet sur cette capture |
| Analyse Wireshark | Réussie |

## 6. Conclusion

La capture et l'analyse du trafic réseau ont été réalisées avec succès.

Les outils tcpdump et Wireshark ont permis d'observer les échanges ICMP entre Kali Linux et Metasploitable 2.

Ce laboratoire démontre l'utilisation des outils de capture et d'analyse réseau dans le cadre des activités Blue Team de l'environnement Entreprise X.