---

copyright:
  years: 2015, 2018
lastupdated: "2018-04-04"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

Cette documentation concerne
{{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}.
Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace,
[cliquez sur
ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-use.html){: new_window}.
{: tip}

# Utiliser le modèle à base de règles
{: #wks_rule_publish}

Tirez parti d'un modèle à base de règles que vous avez créé avec {{site.data.keyword.knowledgestudioshort}}
en le mettant à la disposition d'autres applications {{site.data.keyword.watson}}.
{: shortdesc}

**Attention **: Vous pouvez déployer un modèle à base de règles en vue de le
rendre utilisable dans ces services en tant que fonctionnalité [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental).


Pour pouvoir déployer un modèle à l'usage d'un service, vous devez disposer d'un abonnement à
celui-ci.
Les services {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} sont
hébergés sur {{site.data.keyword.Bluemix_notm}}, la plateforme cloud d'{{site.data.keyword.IBM_notm}}.
Pour plus d'informations sur cette plateforme, consultez
[Qu'est-ce que {{site.data.keyword.Bluemix_notm}} ? ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window}.
Pour vous abonner à l'un des services
{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}, créez un compte
sur le site web [{{site.data.keyword.Bluemix_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.ng.bluemix.net/){: new_window}.


Pour certains services, vous devez connaître les détails de l'instance de service dans laquelle vous prévoyez le déploiement.
Vous devez notamment connaître les noms d'espace et d'instance {{site.data.keyword.Bluemix_notm}}.
Ces informations sont disponibles sur la page des services {{site.data.keyword.Bluemix_notm}}.


Vous pouvez aussi pré-annoter de nouveaux documents avec le modèle à base de règles.
Pour les détails, consultez [Pré-annoter des documents avec le modèle à base de règles](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule).

## Déployer un modèle à base de règles sur AlchemyLanguage
{: #wks_rule_bluemix}

Cette fonctionnalité permet à vos applications d'utiliser
le modèle à base de règles déployé pour repérer et extraire des entités de documents de votre domaine.


**Attention** : Il s'agit actuellement d'une fonctionnalité [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)
du service.


### Avant de commencer

Pour utiliser ce modèle personnalisé, vous devez avoir le plan Avancé
du service {{site.data.keyword.alchemylanguageshort}}.


### A propos de cette tâche

Pour déployer sur ce service, vous devez avoir une clé d'accès provenant d'{{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}.

La clé doit appartenir à un compte autorisé à publier des modèles personnalisés. Faute de quoi, le modèle
sera déployé correctement, mais vous ne pourrez pas l'utiliser.


Lorsque vous déployez le modèle à base de règles, vous devez sélectionner quelle version de celui-ci vous
voulez déployer.
La clé doit être spécifiée la première fois que vous déployez un modèle
sur {{site.data.keyword.alchemylanguageshort}}. Vous pouvez ensuite la réutiliser
avec différentes versions du même modèle.
A chaque clé correspond un nombre maximum de modèles pouvant être déployés en même temps.


### Procédure

Pour déployer un modèle à base de règles sur {{site.data.keyword.alchemylanguageshort}} :

1. Connectez-vous en tant qu'administrateur ou chef de projet
{{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de
travail.

1. Sélectionnez l'onglet **Gestion des modèles** > **Versions** > **A base de règles**.
1. Choisissez la version du modèle que vous voulez déployer.

    Si une seule version du modèle est fonctionnelle, sauvegardez le modèle actuel en vue de son déploiement
en cliquant sur **Sauvegarder pour le déploiement**.
Le fait de cliquer sur **Sauvegarder pour le déploiement** crée une version spécifique du modèle, qui est celle qui sera
déployée. Cela vous permet de continuer à améliorer la version en cours.
La sauvegarde de la version peut prendre quelques minutes.
L'option Déployer n'apparaît pas tant que la version n'est pas créée.


1. Cliquez sur **Déployer**, optez pour le déploiement sur {{site.data.keyword.alchemylanguageshort}}, puis cliquez
sur **Suivant**.
1. Entrez la clé que vous avez obtenue d'{{site.data.keyword.alchemylanguageshort}} ou
sélectionnez une version précédemment déployée du modèle à laquelle est associée une clé que vous
comptez réutiliser. Cliquez sur **Déployer**.
Si la clé est valide, une confirmation dans laquelle figure l'ID du modèle s'affiche.
Cela ne signifie pas pour autant que le modèle est prêt à être utilisé par vos applications.

1. Le processus de déploiement peut prendre quelques minutes.
Pour savoir où il en est, cliquez sur **Statut** à côté de la version déployée.
Si le modèle est toujours en cours de déploiement, le statut indiqué
est "publication en cours".
Une fois le déploiement terminé, le statut passe à "disponible" si l'opération a réussi ou "erreur" si des problèmes ont été rencontrés.

    Les informations de statut comprennent l'ID du modèle, les quatre derniers chiffres de la clé {{site.data.keyword.alchemyapishort}} et
un journal du processus de déploiement.
L'ID du modèle (model_id) est le nom par lequel vos applications appelleront le modèle d'apprentissage automatique.
Prenez-en note, car il n'y a pas de moyen programmatique d'y accéder ultérieurement.
Utilisez la clé {{site.data.keyword.alchemyapishort}} pour garder la trace du nombre de déploiements par clé.

### Que faire ensuite

Pour utiliser le modèle déployé, vous devez copier et coller son ID dans l'appel d'API de votre application.


> **Attention :** Vous ne pouvez pas utiliser l'appel d'API
{{site.data.keyword.alchemylanguageshort}} `GET /info/models` pour obtenir
programmatiquement l'ID de modèles à base de règles.
Cet appel vous permet d'accéder à l'ID de modèles d'apprentissage automatique, mais pas à celui
de modèles à base de règles.


L'appel doit aussi spécifier le service {{site.data.keyword.alchemylanguageshort}} à utiliser
avec le modèle, ainsi que votre clé d'accès {{site.data.keyword.alchemyapishort}}.


Le point d'extrémité suivant est accepté :


- **&lt;*type-entré*&gt;GetRankedNamedEntities**

    Utilise le modèle personnalisé que vous spécifiez dans le paramètre 'model' pour extraire la liste des mentions
de tous les types d'entités connus qu'il trouve dans les données d'entrée que vous fournissez.
Les données d'entrée acceptées sont le texte, le HTML ou une URL publique.
Pour plus d'informations sur l'API et la syntaxe à utiliser,
consultez [{{site.data.keyword.alchemylanguageshort}}&gt;Entities ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window}.


## Déployer un modèle à base de règles sur IBM Watson Discovery
{: #wks_rule_discovery}

Déployez le modèle à base de règles pour permettre à une application utilisant
le service {{site.data.keyword.discoveryshort}} d'en tirer parti pour trouver et extraire des entités
lors de l'enrichissement de documents.


**Attention** : Il s'agit actuellement d'une fonctionnalité [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)
du service.


### Avant de commencer

Vous devez posséder un accès administratif à une instance de
service {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} et connaître
les noms d'espace et d'instance {{site.data.keyword.Bluemix_notm}}.


### Procédure

Pour déployer un modèle à base de règles sur {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, effectuez les étapes suivantes :

1. Connectez-vous en tant qu'administrateur ou chef de projet
{{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de
travail.

1. Sélectionnez l'onglet **Gestion des modèles** > **Versions** > **A base de règles**.
1. Choisissez la version du modèle que vous voulez déployer.

    Si une seule version du modèle est fonctionnelle, sauvegardez le modèle actuel en vue de son déploiement
en cliquant sur **Sauvegarder pour le déploiement**.
Cela a pour effet de créer une version spécifique du modèle, qui est celle qui sera
déployée. Vous pourrez ainsi continuer à améliorer la version en cours.
La sauvegarde de la version peut prendre quelques minutes.
L'option Déployer n'apparaît pas tant que la version n'est pas créée.


1. Cliquez sur **Déployer**, optez pour le déploiement sur {{site.data.keyword.discoveryshort}}, puis cliquez
sur **Suivant**.
1. Indiquez les noms d'espace et d'instance {{site.data.keyword.Bluemix_notm}}.
Si nécessaire, sélectionnez une région différente.

1. Cliquez sur **Déployer**.
1. Le processus de déploiement peut prendre quelques minutes.
Pour savoir où il en est, cliquez sur **Statut** sous l'onglet **Versions**, à côté de la version déployée.


    Si le modèle est toujours en cours de déploiement, le statut indiqué
est "publication en cours".
Une fois le déploiement terminé, le statut passe à "disponible" si l'opération a réussi ou "erreur" si des problèmes ont été rencontrés.

    Une fois le modèle disponible, prenez note de son ID (model_id).
Vous devrez le fournir au service {{site.data.keyword.discoveryshort}} afin que celui-ci puisse utiliser
votre modèle personnalisé.


### Que faire ensuite

Pour utiliser le modèle déployé, vous devez fournir son ID lorsqu'il vous est demandé
au cours du processus de configuration d'enrichissement du service {{site.data.keyword.discoveryshort}}.


## Déployer un modèle à base de règles sur IBM Watson Natural Language Understanding
{: #wks_rule_nlu}

Déployez le modèle à base de règles pour permettre à une application utilisant
le service {{site.data.keyword.nlushort}} d'en tirer parti pour trouver et extraire des entités
pertinentes dans votre domaine.


**Attention** : Il s'agit actuellement d'une fonctionnalité [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)
du service.


### Avant de commencer

Vous devez posséder un accès administratif à une instance de
service {{site.data.keyword.nlushort}} et connaître
les noms d'espace et d'instance {{site.data.keyword.Bluemix_notm}}.


### Procédure

Pour déployer un modèle à base de règles sur {{site.data.keyword.nlushort}}, effectuez les étapes suivantes :

1. Connectez-vous en tant qu'administrateur ou chef de projet
{{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de
travail.

1. Sélectionnez l'onglet **Gestion des modèles** > **Versions** > **A base de règles**.
1. Choisissez la version du modèle que vous voulez déployer.

    Si une seule version du modèle est fonctionnelle, sauvegardez le modèle actuel en vue de son déploiement
en cliquant sur **Sauvegarder pour le déploiement**.
Cela a pour effet de créer une version spécifique du modèle, qui est celle qui sera
déployée. Vous pourrez ainsi continuer à améliorer la version en cours.
La sauvegarde de la version peut prendre quelques minutes.
L'option Déployer n'apparaît pas tant que la version n'est pas créée.


1. Cliquez sur **Déployer**, optez pour le déploiement sur {{site.data.keyword.nlushort}}, puis cliquez
sur **Suivant**.
1. Indiquez les noms d'espace et d'instance {{site.data.keyword.Bluemix_notm}}.
Si nécessaire, sélectionnez une région différente.

1. Cliquez sur **Déployer**.
1. Le processus de déploiement peut prendre quelques minutes.
Pour savoir où il en est, cliquez sur **Statut** sous l'onglet **Versions**, à côté de la version déployée.


    Si le modèle est toujours en cours de déploiement, le statut indiqué
est "publication en cours".
Une fois le déploiement terminé, le statut passe à "disponible" si l'opération a réussi ou "erreur" si des problèmes ont été rencontrés.

    Une fois le modèle disponible, prenez note de son ID (model_id).
Vous devrez le fournir au service {{site.data.keyword.nlushort}} afin que celui-ci puisse utiliser
votre modèle personnalisé.


### Que faire ensuite

Pour utiliser la version déployée de votre modèle personnalisé, vous devez fournir son ID dans
le paramètre `entities.model`.


Pour extraire des entités, vous pouvez utiliser le modèle avec la demande
`GET /analyze` de {{site.data.keyword.nlushort}}.


Pour plus de détails, consultez la
[documentation de {{site.data.keyword.nlushort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/index.html){: new_window}.


## Retirer des modèles du déploiement
{: #undeploy-view-model}

Si vous voulez retirer un modèle du déploiement ou simplement trouver son ID, consultez la
page **Modèles déployés**.
Vous pourrez y voir tous les modèles {{site.data.keyword.knowledgestudioshort}} déployés dans des services des espaces auxquels vous avez accès.


Pour retirer un modèle du déploiement ou trouver son ID :


1. Connectez-vous en tant qu'administrateur ou chef de projet
{{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de
travail.

1. Dans le menu **Paramètres** de la barre de menus, en haut à droite, sélectionnez **Gérer les modèles déployés**.

1. Dans la liste des modèles déployés, localisez le modèle que vous souhaitez voir ou retirer du déploiement.
1. Pour retirer le modèle du déploiement, cliquez sur **Annuler le déploiement du modèle** dans la dernière colonne de la ligne où il figure.
1. Pour trouver l'ID du modèle, consultez la colonne **ID modèle**.

## Tirer parti d'un modèle à base de règles dans IBM Watson Explorer
{: #wks_rule_export}

Exportez le fichier PEAR qui est généré au moment où le modèle à base de règles est créé
afin qu'il puisse être utilisé dans {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procédure

Pour exploiter un modèle à base de règles dans {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, effectuez les étapes suivantes :


1. Connectez-vous en tant qu'administrateur ou chef de projet
{{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de
travail.

1. Sélectionnez l'onglet **Gestion des modèles** > **Versions** > **A base de règles**.
1. Cliquez sur **Exporter le modèle en cours**.

    Si vous avez un abonnement à un plan gratuit, aucune option d'exportation n'est disponible.


    Le modèle est sauvegardé en tant que fichier PEAR, que vous êtes invité à
télécharger.
PEAR (Processing Engine ARchive) est le format standard d'empaquetage des composants UIMA
(Unstructured Information Management Architecture).
Le modèle est sauvegardé au format PEAR afin de pouvoir être distribué et réutilisé dans les applications UIMA.


1. Téléchargez le fichier sur votre système local.

1. A partir de l'application {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer,
importez le fichier PEAR.

