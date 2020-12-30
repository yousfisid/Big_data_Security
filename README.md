# Big_data_Security
# Introduction
Le déploiement de metron mettra en place 2cluster (hdp et hdf) , Comme on peut le noter ci-dessus, Apache Metron agit comme un pipeline de traitement de flux de sécurité en temps-réel destiné à :

Capturer les événements télémétriques générés par les diverses classes de sources de données ingérées. Durant cette phase Metron utilise son propre composant d’ingestion ou des outils comme Apache NiFi pour traiter les flux de données à travers leurs propres topics Kafka. Metron peut également traiter de gros volumes d’événements comme PCAP, NetFlow,… à partir d’un TAP réseau.

Traiter les flux routés par Kafka au sein d’une topologie Storm sur lequel s’appuie Metron Streaming pour ses traitements. Durant cette phase, les données sont analysées, normalisées, validées, puis étiquetées.

Enrichir les événements préalablement traités, à travers diverses opérations comme l’enrichissement des informations de connexion utilisées par lesdits événements (IP, hostname, GPS,…) pour une meilleure identification.

Etiqueter les événements traités et enrichis, qui consiste à vérifier leurs informations afin de valider leur degré de dangerosité, puis de les étiqueter en fonction des résultats du processus de vérification. De cette façon, en cas de faille de sécurité suite à l’ingestion d’un événement, le système sera en mesure d’éviter que des événements similaires se reproduisent à l’avenir.

Stocker les événements télémétriques préalablement capturés, traités, enrichis et étiquetés au sein d’un « coffre » appelé Security Data Vault (HDFS, etc…) ou d’un magasin PCAP dans le cas de gros paquets réseaux. Les événements ayant levé des alertes sont indexés dans un magasin d’alertes.
