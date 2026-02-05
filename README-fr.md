# Integration Jenkins avec Visual TOM
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE.md)&nbsp;
[![fr](https://img.shields.io/badge/lang-en-red.svg)](README.md)  
Ce projet fournit une intégration entre Visual TOM et Jenkins afin de lancer des traitements Jenkins depuis un traitement Visual TOM en utilisant l’outil jenkins-cli.jar.

# Disclaimer
Aucun support ni garanties ne seront fournis par Absyss SAS pour ce projet et fichiers associés. L'utilisation est à vos propres risques.

Absyss SAS ne peut être tenu responsable des dommages causés par l'utilisation d'un des fichiers mis à disposition dans ce dépôt Github.

Il est possible de faire appel à des jours de consulting pour l'implémentation.

# Prérequis

  * Visual TOM 7.1.2 or supérieur
  * Binaire Jenkins CLI à télécharger depuis votre serveur Jenkins : http://jenkins-server:port/jnlpJars/jenkins-cli.jar à positionner dans le répertoire %ABM_BIN%
  * Java compatible avec votre version de Jenkins: [Support Policy Java – Jenkins](https://www.jenkins.io/doc/book/platform-information/support-policy-java/?utm_source=chatgpt.com)

# Consignes

Définir les variables suivantes sur l’agent exécutant les traitements Jenkins :

  ```Variables d'environnement à déclarer
JENKINS_URL=http://<jenkins-server>:<port>
JENKINS_USER_ID=XXXX
JENKINS_API_TOKEN=34654564XXXXX21231321
JAVA_JENKINS=F:\openlogic-openjdk-jre-17.0.12+7-windows-x64\bin\java
  ```

Le fichier **jenkins.xml** correspond au modèle de traitement Jenkins à importer dans votre base. Il prend en argument une entrée qui correspond au nom du job Jenkins.

La queue **submit_queue_jenkins.bat** à positionner et à déclarer sur l'agent Windows.

# Actions disponibles

## Objectif global
La queue batch encapsule l'exécution du binaire jenkins-cli.jar avec l'argument build qui permet de déclencher un job Jenkins

## Arguments

Dans le modèle un seul paramètre en entrée est nécessaire : le nom du job Jenkins

La commande build permet de :
- ➡️ déclencher un job Jenkins
- ➡️ éventuellement passer des paramètres
- ➡️ attendre la fin du build
- ➡️ contrôler le comportement (logs, échec, délais…)

## Résultat du job	Code CLI

| Job Result | CLI Exit Code |
| ---------- | ------------- |
| SUCCESS    | 0             |
| FAILURE    | ≠ 0           |
| ABORTED    | ≠ 0           |
| TIMEOUT    | ≠ 0           |


# Licence
Ce projet est sous licence Apache 2.0. Voir le fichier [LICENCE](license) pour plus de détails.


# Code de conduite
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-v2.1%20adopted-ff69b4.svg)](code-of-conduct.md)  
Absyss SAS a adopté le [Contributor Covenant](CODE_OF_CONDUCT.md) en tant que Code de Conduite et s'attend à ce que les participants au projet y adhère également. Merci de lire [document complet](CODE_OF_CONDUCT.md) pour comprendre les actions qui seront ou ne seront pas tolérées.
