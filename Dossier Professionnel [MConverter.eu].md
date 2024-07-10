<img src="media/image1.jpeg" style="width:4.5in;height:2.53125in"
alt="Une image contenant plein air, ciel, herbe, route Description générée automatiquement" />

<img src="media/image2.jpeg" style="width:4.49167in;height:2.16785in"
alt="Une image contenant ciel, plein air, bâtiment, Panneau d’affichage Description générée automatiquement" /><img src="media/image3.png" style="width:0.60764in;height:0.77986in"
alt="Une image contenant texte, Police, affiche, Graphique Description générée automatiquement" /><img src="media/image4.jpeg" style="width:6.53046in;height:2.28696in"
alt="Rendez-vous dans nos nouveaux locaux au Portugal ! - TopTex Blog" /><img src="media/image5.png" style="width:1.89861in;height:0.50903in"
alt="Une image contenant Police, logo, Graphique, symbole Description générée automatiquement" /><img src="media/image6.jpeg" style="width:5.70903in;height:2in"
alt="Dans les coulisses de TopTex avec BFM TV - TopTex Blog" /><img src="media/image7.png" style="width:0.75417in;height:0.75208in"
alt="Une image contenant texte, Police, logo, Graphique Description générée automatiquement" />

<img src="media/image3.png" style="width:0.60826in;height:0.78029in"
alt="Une image contenant texte, Police, affiche, Graphique Description générée automatiquement" /><img src="media/image5.png" style="width:1.89916in;height:0.50918in"
alt="Une image contenant Police, logo, Graphique, symbole Description générée automatiquement" />

# Table des matières

[Présentation de l’entreprise
[1](#présentation-de-lentreprise)](#présentation-de-lentreprise)

[Projet 1 \[ Supervision Stack Grafana avec sonde réseau \]
[2](#projet-1-supervision-stack-grafana-avec-sonde-réseau)](#projet-1-supervision-stack-grafana-avec-sonde-réseau)

[Problématique [2](#problématique)](#problématique)

[Contexte [3](#contexte)](#contexte)

[Comparatif [3](#comparatif)](#comparatif)

[Mise en place du plan
[3](#mise-en-place-du-plan)](#mise-en-place-du-plan)

[Schéma Réseau [3](#schéma-réseau)](#schéma-réseau)

[Schéma Projet [6](#schéma-projet)](#schéma-projet)

[Déploiement [6](#déploiement)](#déploiement)

[Installation des agents
[7](#installation-des-agents)](#installation-des-agents)

[Création d’un dashboard pour les switches
[8](#création-dun-dashboard-pour-les-switches)](#création-dun-dashboard-pour-les-switches)

[PRI [8](#pri)](#pri)

[Dashboard (Tableau de bords)
[9](#dashboard-tableau-de-bords)](#dashboard-tableau-de-bords)

[Mise en place des alerts
[11](#mise-en-place-des-alertes)](#mise-en-place-des-alertes)

[Comment la supervision et la sonde résolvent-elles le problème ?
[11](#comment-la-supervision-et-la-sonde-résolvent-elles-le-problème)](#comment-la-supervision-et-la-sonde-résolvent-elles-le-problème)

[Projet 2 \[Renouvellement PDA de vérification pour colisage\]
[12](#projet-2-renouvellement-pda-de-vérification-pour-colisage)](#projet-2-renouvellement-pda-de-vérification-pour-colisage)

[Problématique [12](#problématique-1)](#problématique-1)

[Contexte [13](#contexte-1)](#contexte-1)

[Comparatif [14](#comparatif-1)](#comparatif-1)

[Ce qui va changer [16](#ce-qui-va-changer)](#ce-qui-va-changer)

[Mise en place du plan
[17](#mise-en-place-du-plan-1)](#mise-en-place-du-plan-1)

[Qu'est-ce que GS1? [17](#quest-ce-que-gs1)](#quest-ce-que-gs1)

[Hardening d’android (Renforcement d’android)
[21](#hardening-dandroid-renforcement-dandroid)](#hardening-dandroid-renforcement-dandroid)

[PRI [21](#pri-1)](#pri-1)

[Déploiement [21](#déploiement-1)](#déploiement-1)

[Annexes [21](#annexes)](#annexes)

[GANTT Project - Projet 2
[21](#gantt-project---projet-2)](#gantt-project---projet-2)

[Code SMARTIP [23](#code-smartip)](#code-smartip)

## Présentation de l’entreprise 

<img src="media/image5.png" style="width:1.89916in;height:0.50918in"
alt="Une image contenant Police, logo, Graphique, symbole Description générée automatiquement" />

TopTex est une entreprise B2B spécialisée dans les textiles
professionnels et personnels. Elle offre une large gamme de produits
adaptés aux entreprises et particuliers. Présente à travers l'Europe,
TopTex dispose de centres logistiques stratégiques pour une distribution
rapide. L'entreprise se distingue par son engagement envers la qualité,
la durabilité et l'innovation.  
  
<img src="media/image8.png" style="width:6.3in;height:2.43125in"
alt="Une image contenant Monde, Terre, carte, texte Description générée automatiquement" />

Leader dans son domaine dans son pays d’origine, l’entreprise se classe
à la 3ème place au niveau européen. Ce positionnement est dû au fait que
TopTex offre à ses clients des services annexes au textile, comme une
API pour relier leurs sites à notre système d'information, ainsi que des
CMS pré-conçus (SowebShop) pour fournir à nos clients une première page
publicitaire sur Internet.

Toptex a su se moderniser en interne grâce à nos entrepôts
semi-automatisés et à toute l'infogérance qui en découle.

Pour cette alternance, j'ai travaillé au sein du service Support
informatique, dont la mission est de maintenir le système d'information
opérationnel et d'intervenir rapidement en cas de problème.

## Projet 1 \[ Supervision Stack Grafana avec sonde réseau \]

### Problématique

(**Ancienne version**) Le changement de politique de gestion des
appareils informatiques, incluant la migration complète du parc
d'adresses IP statiques, a des impacts significatifs sur l'efficacité
opérationnelle et la sécurité du réseau de l'organisation, notamment en
ce qui concerne la gestion des doublons d'adresses

(**Nouvelle version**) Depuis le passage des IPs statique vers le DHCP,
Toptex rencontre toujours des problèmes de doublons au sein de son
réseau. De ce fait, nous avons l’erreur suivante qui apparaît :

*DHCP server leases 100% used showing IP in client IP and Name fields.*

Cela signifie que les IP réservées pour les baux DHCP sont utilisées à
100%.

Il faut pouvoir différencier quelles IPs sont utilisées sur le réseau et
voir si nous pouvons en dédier plus au DHCP. Nous devons être alertés
lorsque cela se produit afin d'intervenir de manière proactive.

La supervision n’existant pas au moment de ces faits, nous ne sommes pas
en capacité d’être alertés lorsque cela se produit.

### Contexte

Historiquement, malgré une expansion rapide, Toptex n'a pas vu son
système d'information suivre le même rythme. En effet, la gestion des
adresses IP statiques était confiée aux cinq techniciens du système
d'information pour l'ensemble du groupe Toptex et ses agences,
représentant des milliers d'adresses IP à gérer, une tâche colossale.

Constatant cela, le directeur des systèmes d'information, avec le chef
de projet junior responsable du réseau et de la cybersécurité, a lancé
le projet de déployer un serveur DHCP. Ce projet a été réalisé avec
succès.

Cependant, certains appareils hors de notre contrôle (anciens
prestataires) ou simplement des ordinateurs oubliés, entre autres, ont
réapparu à plusieurs reprises, provoquant des doublons d'adresses IP. De
plus, une liste limitée d'adresses IP disponibles pour le DHCP a
entraîné des chevauchements de baux, causant également des doublons.
Nous avons donc dû trouver une solution.

### Comparatif

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nom</th>
<th>PRTG</th>
<th>Suite Grafana + Sonde</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Compatible Jira</td>
<td>Non</td>
<td>Oui</td>
</tr>
<tr class="even">
<td>Ouvert au module perso</td>
<td>Non</td>
<td>Oui</td>
</tr>
<tr class="odd">
<td>Libre/OpenSource</td>
<td>Proprietaire</td>
<td>OpenSource de base/ Semi Ouvert pour le payant</td>
</tr>
</tbody>
</table>

### Mise en place du plan

### Schéma Réseau

1.  Siège Avant

<img src="media/image9.jpeg" style="width:6.3in;height:4.45069in"
alt="Une image contenant texte, diagramme, carte, Plan Description générée automatiquement" />

2.  Dépôt Avant (23k)

<img src="media/image10.jpeg" style="width:6.3in;height:4.45069in"
alt="Une image contenant texte, diagramme, Plan, schématique Description générée automatiquement" />

3.  Siège Maintenant

<img src="media/image11.jpeg" style="width:6.3in;height:4.45069in"
alt="Une image contenant texte, diagramme, Plan Description générée automatiquement" />

4.Dépot Maintenant (23k)

<img src="media/image12.jpeg" style="width:6.3in;height:4.45069in"
alt="Une image contenant texte, diagramme, Plan, schématique Description générée automatiquement" />

### Schéma Projet

(WIP)

### Déploiement

#### Création d’une VM pour utiliser Docker sur Proxmox 

Pour ce projet, nous utilisons la technologie Docker pour le
déploiement. Elle permet de créer des images appelées « conteneurs ».
Ces conteneurs sont très pratiques pour les déploiements à grande
échelle et les redéploiements rapides.

Nous utilisons les images officielles de la stack Grafana fournies par
l'éditeur (Grafana Labs). Bien qu'une version cloud soit disponible,
nous avons préféré héberger les données en local.

Pour unifier le déploiement, nous allons utiliser un plugin Docker nommé
« Compose », qui permet de décrire notre stack applicative en utilisant
des fichiers .yaml.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>Stack (Grafana,Prometheus,Loki,Alertmanager, Cadvisor)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="media/image13.png"
style="width:4.40295in;height:7.73735in" /></td>
</tr>
</tbody>
</table>

Prometheus.yml, Alertmanager.yml et local-config.yml seront inclus dans
les annexes.

Cette architecture de stack de monitoring a été mise en place pour
fournir une solution complète de surveillance et de gestion des alertes
pour nos applications conteneurisées. Chaque élément du fichier
docker-compose.yml joue un rôle clé dans cette solution intégrée.

**Version utilisée : 3.8**

##### Services Configurés :

###### **1.** Prometheus

- **Image** : prom/prometheus:latest ***(L’image qui correspond au
  logiciel)***

- **Volumes** : ./prometheus.yml:/etc/prometheus/prometheus.yml
  ***(Localisation de son volume)***

- **Ports** : 9090:9090 ***(Son port externe et interne d’écoute)***

*Prometheus est un système de monitoring et d'alerting open-source. Il
collecte les métriques des services configurés, stocke les données de
séries temporelles dans une base de données et permet de créer des
règles d'alerting.*

###### 2. Grafana

- **Image** : grafana/grafana:latest ***(L’image qui correspond au
  logiciel)***

- **Ports** : 3000:3000 ***(Son port externe et interne d’écoute)***

- **Volumes** : grafana-storage:/var/lib/grafana ***(Localisation de son
  volume)***

- **Depends On** : prometheus, loki ***(Ne demarre pas avant)***

*Grafana est une plateforme de visualisation et d'analyse de métriques.
Elle se connecte à Prometheus pour visualiser les données de monitoring
sous forme de tableaux de bord personnalisables et peut s'intégrer avec
Loki pour afficher les logs.*

###### 3. Loki

- **Image** : grafana/loki:latest ***(L’image qui correspond au
  logiciel)***

- **Ports** : 3100:3100 ***(Son port externe et interne d’écoute)***

- **Command** : -config.file=/etc/loki/local-config.yaml ***(Commande au
  début pour spécifier la configuration)***

- **Volumes** :
  ./loki-config.yml:/etc/loki/local-config.yaml***(Localisation de son
  volume)***

*Loki est un agrégateur de logs conçu pour fonctionner avec Grafana. Il
collecte les logs des conteneurs et les rend disponibles pour
consultation et analyse via Grafana.*

###### 4. Alertmanager

- **Image** : prom/alertmanager:latest ***(L’image qui correspond au
  logiciel)***

- **Ports** : 9093:9093 ***(Son port externe et interne d’écoute)***

- **Volumes** : ./alertmanager.yml:/etc/alertmanager/alertmanager.yml
  ***(Localisation de son volume)***

*Alertmanager gère les alertes générées par Prometheus. Il reçoit les
alertes de Prometheus et gère leur distribution en fonction des règles
configurées (par e-mail, Slack, etc.).*

###### 5. cAdvisor

- **Image** : google/cadvisor:latest ***(L’image qui correspond au
  logiciel)***

<!-- -->

- **Ports** : 8080:8080 ***(Son port externe et interne d’écoute)***

- **Volumes** : ***(Localisation de son volume)***

  - /-/:ro

  - /var/run/:/var/run:ro

  - /sys:ro

  - /var/lib/docker/:/var/lib/docker:ro

*cAdvisor fournit des informations sur l'utilisation des ressources et
les performances des conteneurs. Il collecte et expose des métriques sur
les performances et l'utilisation des ressources des conteneurs.*

##### Volumes :

- **grafana-storage** : Volume Docker utilisé par Grafana pour stocker
  ses données persistantes.

##### Réseaux :

- **default** :

- **Driver** : bridge - Utilise le pilote de réseau par défaut bridge.

##### Conclusion

Cette stack Docker Compose configure une suite d'outils de monitoring et
de gestion des alertes pour surveiller les performances des applications
conteneurisées. Chaque service joue un rôle spécifique dans la collecte,
l'affichage et la gestion des données de monitoring, offrant ainsi une
solution complète et intégrée pour notre environnement conteneurisé.

### Installation des agents

#### Windows

La supervision des VM(s) Windows se fait sur notre hyperviseur ESXi donc
nous avons déjà un agent mais ce n’est pas suffisant nous devons
installer celui de la stack Grafana pour permettre à prometheus de
récupérer les données

(WIP)

#### CAdvisor

<img src="media/image14.png" style="width:3.70032in;height:2.60856in" />

### Création d’un dashboard pour les switches

Nous allons exploiter les données fournies par une API qui nous indique
l'état opérationnel de nos switches :

> Alive ● = En ligne ●
>
> Down ● = Hors ligne ●

Cette API a été mise à notre disposition à la suite d'une demande que
j'ai formulée auprès du prestataire infogérance (Coaxis), en raison du
refus d'utiliser le protocole SNMP, qui nous aurait permis d'obtenir
davantage d'informations sur nos switches.

*Je suis restreint car la plage d'adresses utilisée n'est pas celle
prévue. L'adresse 10.208.50.0/24 est réservée aux équipements réseau.
Une route est disponible pour que je puisse accéder à l'API.*

*<u>Affichage du dashboard</u>*

<img src="media/image15.png" style="width:6.3in;height:3.08264in" />

### PRI

Le Plan de Reprise des Activités a été conçu et est actuellement examiné
par les ayants droit pour confirmation. Je peux vous en présenter les
détails.

#### Orchestrateurs (Futur)

Le proxy (Squid) qui empêche la connexion sur nos PDA sera prochainement
déployé sur d’autres PDA de services, notamment au niveau de la
préparation de commandes au dépôt. Cela permettra d’éviter que les
utilisateurs accèdent au web via le navigateur.

Les orchestrateurs actuellement à l'étude sont Docker Swarm et
Kubernetes. Le projet en est encore à la phase d'étude et vise à
permettre la réplication de nos conteneurs en cas de surcharge à des
périodes spécifiques (pendant les roulements du matin et du soir). En
dehors de ces périodes, le nombre de conteneurs sera réduit, assurant
ainsi une répartition efficace des charges.

#### Hyperviseurs Redondés (Futur)

L'hyperviseur actuellement utilisé est Proxmox, déployé sans redondance
dans notre laboratoire. Nous souhaitons maintenir ce projet dans le
laboratoire, mais passer d'un vieux mini PC à une infrastructure basée
sur deux NUC, équipés de 32 Go de RAM, de SSD NVMe et de processeurs
Intel de dernière génération pour assurer la redondance. La mise en
place de cette nouvelle infrastructure constitue actuellement mon projet

(WIP)

### Dashboard (Tableau de bords)

Je vais présenter les différents dashboard qu’on utilise pour superviser
notre SI :

Dashboard (Accueil) :

<img src="media/image16.png" style="width:6.3in;height:2.85903in" />

Dashboard pour nos containeurs (Docker) :

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="media/image17.png"
style="width:6.3in;height:2.27708in" /></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="media/image18.png"
style="width:6.3in;height:0.87222in" /></td>
</tr>
</tbody>
</table>

Dashboard pour nos serveurs Windows :

<img src="media/image19.png" style="width:6.3in;height:2.51111in" />

<img src="media/image20.png" style="width:6.3in;height:2.88056in" />

Ce tableau de bord nous permet de superviser nos deux serveurs Windows :

- Trafalgar : notre contrôleur de domaine, DNS, AD, et serveur DHCP

- Waterloo : notre serveur web pour SmartIP (IIS), WDS et WSUS

Fait important nous avons désormais une politique sur notre sécurité au
seins de Toptex, nos sessions distantes de travail sont proteger par DUO
Mobile mais aussi nos serveurs avec nos services dessus.

Et ils sont donc protégés par l'authentification multifactorielle
*<u>(MFA \> Multi-factor authentication)</u>* DUO.

(WIP)

#### DUO MOBILE (MFA)

##### Installation Agent DUO

(WIP)

Dashboard pour nos containers :

<img src="media/image21.png" style="width:6.3in;height:2.84931in"
alt="Une image contenant capture d’écran, texte, logiciel, Logiciel multimédia Description générée automatiquement" />

Ce tableau de bord utilise un conteneur nommé Cadvisor ([abréviation de
Container Advisor](https://prometheus.io/docs/guides/cadvisor/)), un
outil maintenu par Google pour la supervision des conteneurs. Il
s'appuie sur le socket Docker pour obtenir des informations sur les
autres conteneurs, habituellement inaccessibles.

Cela permet d'afficher des graphiques montrant la charge du CPU,
l'utilisation de la RAM et la consommation des conteneurs, afin de
pouvoir les optimiser ou les remplacer par des solutions moins
gourmandes en ressources.

### Mise en place des alertes

L’avantage avec Prometheus, c’est que les métriques peuvent servir aussi
bien à la supervision qu’aux avertissements.

**<u>La stack Grafana fournit trois méthodes pour gérer les
alertes</u>** :

1.  **Via Grafana : Assez directif et sans véritable libre arbitre, vous
    êtes dirigé de A à Z.**

2.  **Via Prometheus : Vous pouvez écrire votre alerte comme si c’était
    un fichier de configuration. C’est assez simple à prendre en main et
    il existe une certaine logique pour la réalisation d’algorithmes
    plus complexes.**

3.  **Via Alertmanager : On peut aussi créer des alertes dans
    Alertmanager un peu à la manière de Prometheus, mais c’est très
    dirigiste car il n’a pas directement accès aux données. Il vous sera
    demandé d’effectuer des détours pour atteindre votre objectif
    d’alerte.**

#### Alertes Prometheus 

Actuellement, chacune de mes alertes est gérer par un fichier spécifique
à chaque plateforme. Voici la liste des plateformes concernées :

- **Docker** <span class="mark">🐳</span>

- **Windows** <span class="mark">🪟</span>

**Windows Serveur Potentiellement Eteint** (l’agent n’est plus
exécuter):

Nous utilisons la valeur de « Up » de l’agent windows pour dire si oui
ou non notre service est Eteint « Down »  
  
<img src="media/image22.png" style="width:6.29167in;height:2.91667in" />

1 **Groups** : (*<u>Doit être placé au début de notre alerte</u>*)

2 **Name** : (*<u>Correspond au nom de notre règle</u>*)

3 **Alert** : (*<u>Nom de l’alerte lorsqu'elle apparaîtra dans nos
outils</u>*)

4 **Expr** : (*<u>Algorithme définissant une valeur, soit numérique,
soit conditionnelle</u>*)

*La valeur attendue peut être soit numérique (0, 1, 2, 3…), soit
booléenne (True/False ou Vrai/Faux).*

5 **Labels** : (*<u>Étiquette que nous attribuons à notre alerte</u>*)

Dans « **Severity** », nous avons :

- **Critical** : Lors d’un événement inattendu (**ex** : Charge CPU à
  100%)

- **Error** : Code erreur détecté dans les logs

- **Warning** : Alerte lorsque nous atteignons un niveau anormal (**ex**
  : Charge CPU à 75%)

- **Info** : Alerte pour une information qui ne nuit pas au système
  d'information (SI)

6 **Annotations** : (*<u>Éléments textuels que nous souhaitons inclure
dans notre alerte</u>*)

- **Summary** : Résumé de la demande, généralement des codes erreur
  internes ou un court message explicatif pour comprendre rapidement le
  problème

- **Description** : Description précise de la demande. Optionnelle, mais
  utile pour, par exemple, rediriger vers une documentation de votre
  base de connaissances (KB) ou pour fournir plus de détails sur le
  résumé afin de faciliter le débogage rapide.

### Comment la supervision et la sonde résolvent-elles le problème ?

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Pour résoudre le problème et renforcer la sécurité, nous avons
décidé de répertorier et de nommer chaque adresse IP dans notre base de
connaissances (KB), de manière plus systématique et efficace
qu'auparavant. En effet, nous utilisons désormais une liste blanche
(whitelist) pour les adresses IP, assignées via notre serveur DHCP qui
peut attribuer certaines IP en filtrant par adresse MAC. Cela nous
permet de savoir qui est sur le réseau, quand et comment.</th>
<th><p>Il existe toujours une liste d'adresses IP "neutres" qui peuvent
être assignées à différents utilisateurs chaque fois qu'un bail DHCP est
renouvelé.</p>
<p>L'outil Smartip nous permet de diagnostiquer les pannes en cas de
plainte, de récupérer l'adresse MAC et de gérer la liste blanche à
distance de manière transparente pour l'utilisateur final. Quant à la
supervision, elle nous alerte en cas de dysfonctionnement de nos
appareils, ce qui nous permet de les rétablir rapidement en suivant les
priorités définies.</p></th>
<th><img src="media/image23.png"
style="width:3.02478in;height:3.02478in"
alt="Une image contenant Animation, Dessin animé, illustration, habits Description générée automatiquement" /></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## Projet 2 \[Renouvellement PDA de vérification pour colisage\]

<img src="media/image24.jpeg" style="width:3.3595in;height:1.82605in"
alt="Une image contenant texte, capture d’écran, modèle, conception Description générée automatiquement" />

### Problématique

<table>
<colgroup>
<col style="width: 28%" />
<col style="width: 42%" />
<col style="width: 28%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="media/image25.png"
style="width:1.83276in;height:1.86999in"
alt="Une image contenant Appareils électroniques, téléphone, Appareil électronique, Téléphonie Description générée automatiquement" /></th>
<th>Le terminal en usage est le WAP4 de Zebra, fonctionnant sous une
configuration unique et non documentée, ce qui la rend difficile à
reproduire. Il opère sur un système d'exploitation obsolète, WinCE, dont
la dernière mise à jour majeure et stable remonte au 13 juin 2013,
correspondant à la version 8.0.</th>
<th><table>
<colgroup>
<col style="width: 47%" />
<col style="width: 52%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="media/image26.png"
style="width:0.51754in;height:0.81746in" /></th>
<th><img src="media/image27.png"
style="width:0.64539in;height:0.58772in"
alt="Une image contenant Panneau de signalisation, signe Description générée automatiquement" /></th>
</tr>
</thead>
<tbody>
</tbody>
</table></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

### Contexte

Nous travaillons avec le fournisseur Timcod, et jusqu'à récemment, nous
étions limités aux terminaux de la marque Zebra. Toutefois, Timcod nous
a récemment permis de tester deux nouveaux modèles pendant deux semaines
: l'EDA52 de Honeywell, une nouvelle marque pour nous, et le TC22 de
Zebra, un modèle que nous n'avions pas encore essayé mais dont nous
connaissions déjà l'écosystème.

Ces appareils, qui tournent sous Android 10 (sorti le 3 septembre 2019),
sont équipés d'une fonctionnalité professionnelle supplémentaire. Il
s'agit du "Kiosk Mode", qui isole l'appareil pour une sécurité
renforcée, un plus par rapport à nos anciens terminaux qui n'avaient pas
cette fonction. Cette amélioration a été rendue possible grâce à notre
solution de gestion d'appareils mobiles (MDM), Euclyd, que nous avons
déployée entre 2022 et 2023.

### Comparatif

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="media/image28.jpeg"
style="width:2.34375in;height:2.34375in"
alt="Une image contenant Téléphone mobile, Appareil de communications portable, Appareil mobile, Appareil de communication Description générée automatiquement" />TC22</th>
<th>EDA52<img src="media/image29.jpg"
style="width:2.14723in;height:2.35425in"
alt="Une image contenant Téléphone mobile, gadget, Appareil électronique, Appareil de communications portable Description générée automatiquement" /></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<img src="media/image30.png" style="width:5.03903in;height:2.65152in"
alt="Une image contenant capture d’écran, texte Description générée automatiquement" />

#### Phase de sélection

Durant la période de prêt, l'ensemble du service a été invité à répondre
à un questionnaire destiné à recueillir leurs impressions. Voici le
formulaire en question :

<img src="media/image31.png" style="width:3.6041in;height:4.46047in"
alt="Une image contenant texte, capture d’écran Description générée automatiquement" />

Dans le formulaire, j'ai inclus une variété de détails techniques et
visuels. Les réponses nominatives m'ont été précieuses pour déterminer
le terminal le plus approprié à nos exigences.

Plusieurs collaboratrices ont directement relevé des aspects
problématiques de l'ancien système, en particulier la nécessité
d'imprimer systématiquement les fichiers contenant les codes-barres.

Pour pallier à ça une solution fut d’utiliser un PDA directement en
scannant l’écran ce qui permet de ne pas imprimer les étiquettes pour
les vérifier ce qui contribue à réduire l’empreinte Carbonne et gagner
en en vitesse pour faire cette tâche.

### Ce qui va changer

<img src="media/image32.png" style="width:4.13954in;height:3.94289in"
alt="C:\Users\Admin\Downloads\diagram.png" />

Ce schéma montre qu'il y a peu d'étapes sautées. Cependant, ce projet
est très utile. Actuellement, nous devons tester nos emballages et
imprimer les codes, ce qui gaspille des ressources comme l'électricité,
l'encre, le papier, des déplacements inutiles et du temps.

La solution est simple : utiliser une tête de lecture assez puissante
pour scanner directement l'écran. Ce projet a justement intégré cette
solution.

### Mise en place du plan

<img src="media/image33.png" style="width:6.3in;height:4.18611in"
alt="Une image contenant texte, capture d’écran, Police, ligne Description générée automatiquement" />

*En annexe vous aurez l’export du fichier msproject :*

#### Explication de la norme GS1

### Qu'est-ce que GS1?

GS1 est un système global qui permet d'identifier de manière unique des
informations telles que les produits, services, et emplacements dans la
chaîne d'approvisionnement.

Il est connu pour les codes-barres dans les magasins mais inclut
également des codes QR et des tags RFID.

*C’est important de comprendre ce que c’est bien que pas en lien
directement car c’est la base de ce projet.*

#### Création d’un interfaçage pour Android

Étant administrateur réseau et système et non développeur de logiciels,
nous allons brièvement présenter le logiciel :

Il s'agit d'un serveur web en Python qui s'exécute (compilé en .exe) sur
Windows. Ce logiciel intègre un backend permettant de « traduire » les
codes-barres scannés et de les envoyer (au PC où s'exécute le logiciel)
sous forme d'entrée clavier.

Ainsi, nous pouvons rester sur notre ordinateur en utilisant le logiciel
de TopTex pour vérifier les codes-barres, car ce logiciel fonctionnera
en arrière-plan.

Ce logiciel a été nommé KariScan *<u>(**Kari** pour la marque historique
de TopTex \[**Kariban**\] et **Scan** pour rappeler la
numérisation).</u>*

*En annexe, vous trouverez le code commenté :*

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 40%" />
<col style="width: 31%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="media/image34.png"
style="width:3.02621in;height:3.02621in" /></th>
<th><img src="media/image35.png" style="width:2.47917in;height:4in"
alt="Une image contenant texte, capture d’écran, Police, conception Description générée automatiquement" /></th>
<th><mark>[1]</mark> Affiche l'adresse IP hébergeant le serveur web qui
permet la connexion via un port généré automatiquement et unique pour
chaque ordinateur.<br />
<br />
<mark>[2]</mark> Le QR Code généré par l'URL simplifie la liaison en le
scannant avec le PDA.</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

#### Mise en place d’un proxy filtrant (Uniquement pour les sites dans le réseau 10.208.X.X)

Nous voulons limiter l'accès à la plage d'adresses IP 10.208.X.X. Cette
restriction permet uniquement les sites hébergés par les machines
exécutant Kariscan.exe. Étant donné que le réseau de Toptex utilise
l'adresse 10.208.0.0/22, seuls les ordinateurs de cette plage seront
autorisés.  
  
Je vais maintenant vous expliquer le fichier de configuration :

<img src="media/image36.png" style="width:6.22949in;height:4.43078in"
alt="Une image contenant texte, capture d’écran, logiciel Description générée automatiquement" />

Ce proxy est utilisé pour nos PC kiosques, permettant aux employés
d'accéder uniquement au logiciel SIRH Eurecia pour la gestion de leurs
congés. Je souhaite également configurer ce proxy pour bloquer l'accès à
tous les autres sites, en n'autorisant que les adresses IP locales
spécifiques. Un fichier contenant les adresses IP des PDA est
disponible, ce qui permet d'assigner une ACL personnalisée pour que les
PDA puissent accéder uniquement à l'intranet via le proxy.

##### Configuration du proxy filtrant squid pour n’autoriser que les sites qui ont pour nom de domaine 10.208.X.X qui correspond à la plage d’ip(s) de TopTex.

###### Création du serveur 

(WIP)

Installation du proxy sur le PDA :  
  
<img src="media/image37.png" style="width:1.61392in;height:3.22785in"
alt="Une image contenant texte, capture d’écran, Police, logiciel Description générée automatiquement" /><img src="media/image38.png" style="width:1.60443in;height:3.20886in"
alt="Une image contenant texte, capture d’écran, Police, nombre Description générée automatiquement" />

**Pour configurer un proxy Squid dans Firefox(*Android*) avec
l'extension Proxy Manager, suivez ces étapes simples :**

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><ol type="1">
<li><p>Ajoutez l'extension Proxy Manager à Firefox.</p></li>
<li><p>Ouvrez Proxy Manager depuis la barre d'outils.</p></li>
<li><p>Créez un nouveau profil de proxy ou éditez-en un
existant.</p></li>
<li><p>Choisissez "HTTPS" pour le protocole.</p></li>
<li><p>Entrez l'adresse IP de votre serveur Squid dans "Host".</p></li>
<li><p>Mettez "3128" comme port, le port standard de Squid.</p></li>
<li><p>Sauvegardez votre configuration.</p></li>
</ol></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

Votre Firefox est maintenant configuré pour utiliser Squid, isolant
ainsi les connexions des terminaux Android.

##### Présentation du MDM rapidement 

(WIP)

#### Enrôlement du PDA dans le MDM Euclyd

Nous devons créer un QR Code d'enrôlement, destiné à être utilisé pour
tous nos PDA. Il sera intitulé : **QR_Kariscan_EDA52**.  
  
<img src="media/image39.png" style="width:5.60445in;height:1.54869in"
alt="Une image contenant texte, Police, nombre, ligne Description générée automatiquement" />

### Hardening d’android (Renforcement d’android)

#### Modification de fonctionnalités de base Honeywell

##### NoSIP (Pour retirer l’usage du clavier)

##### Mise en place d’un suffixe pour automatiser l’envoi de requêtes

##### Activation du mode « Provisionning »

(WIP)

### PRI

(WIP)

### Déploiement

## Annexes

### GANTT Project - Projet 2

<img src="media/image40.jpeg" style="width:6.3in;height:4.45347in"
alt="Une image contenant texte, capture d’écran, Police, nombre Description générée automatiquement" />

<img src="media/image41.jpeg" style="width:6.3in;height:4.45347in"
alt="Une image contenant texte, capture d’écran, Police, nombre Description générée automatiquement" />

<img src="media/image42.jpeg" style="width:6.3in;height:4.45347in"
alt="Une image contenant texte, capture d’écran, Police, nombre Description générée automatiquement" />

<img src="media/image43.jpeg" style="width:6.3in;height:4.45347in"
alt="Une image contenant texte, capture d’écran, diagramme, ligne Description générée automatiquement" />

### Code SMARTIP

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="media/image44.png"
style="width:6.13497in;height:19.85054in"
alt="C:\Users\Admin\Downloads\carbon (1).png" /></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
