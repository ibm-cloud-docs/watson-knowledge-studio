---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-13"

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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/services/knowledge-studio/publish-ml.html){: new_window}.
{: tip}

# Utiliser le modèle d'apprentissage automatique
{: #publish-ml}

Tirez parti d'un modèle d'apprentissage automatique que vous avez entraîné avec {{site.data.keyword.knowledgestudioshort}} en le mettant à la disposition d'autres applications {{site.data.keyword.watson}}.
{: shortdesc}

Vous pouvez déployer ou exporter un modèle d'apprentissage automatique. Un pré-annotateur à base de dictionnaire ou un pré-annotateur {{site.data.keyword.nlushort}} ne peut servir qu'à pré-annoter des documents au sein de {{site.data.keyword.knowledgestudioshort}}.

Pour pouvoir déployer un modèle à l'usage d'un service, vous devez disposer d'un abonnement à celui-ci. Les services {{site.data.keyword.IBM_notm}}{{site.data.keyword.watson}} sont hébergés sur {{site.data.keyword.Bluemix_short}}, la plateforme cloud d'{{site.data.keyword.IBM_notm}}. Pour plus d'informations sur cette plateforme, consultez [Qu'est-ce que {{site.data.keyword.Bluemix_notm}} ? ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window}. Pour vous abonner à l'un des services {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}, créez un compte sur le site web [{{site.data.keyword.Bluemix_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.ng.bluemix.net/){: new_window}.

Pour certains services, vous devez connaître les détails de l'instance de service dans laquelle vous prévoyez le déploiement. Vous devez notamment connaître les noms d'espace et d'instance {{site.data.keyword.Bluemix_notm}}. Ces informations sont disponibles sur la page des services {{site.data.keyword.Bluemix_notm}}.

Vous pouvez aussi pré-annoter de nouveaux documents avec le modèle d'apprentissage automatique. Pour les détails, consultez [Pré-annoter des documents avec le modèle d'apprentissage automatique](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire).

## Déployer un modèle d'apprentissage automatique sur IBM Watson Discovery
{: #wks_madiscovery}

Lorsque vous êtes satisfait des performances du modèle, vous pouvez en déployer une version sur {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}. Cette fonctionnalité permettra à vos applications d'utiliser le modèle d'apprentissage automatique déployé pour enrichir les connaissances obtenues de vos données afin d'inclure la reconnaissance de concepts et de relations pertinents dans votre domaine.

### Avant de commencer
{: #wks_madiscovery_prereqs}

Vous devez posséder un accès administratif à une instance de service {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} et connaître les noms d'espace et d'instance {{site.data.keyword.Bluemix_notm}}.

### A propos de cette tâche
{: #wks_madiscovery_about}

Lorsque vous déployez le modèle d'apprentissage automatique, vous devez sélectionner quelle version de celui-ci vous voulez déployer.

### Procédure
{: #wks_madiscovery_procedure}

Pour déployer un modèle d'apprentissage automatique sur {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, effectuez les étapes suivantes :

1. Connectez-vous en tant qu'administrateur ou chef de projet {{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de travail.
1. Sélectionnez **Modèle d'apprentissage automatique** > **Versions**.
1. Choisissez la version du modèle que vous voulez déployer.

    Si une seule version du modèle est fonctionnelle, créez un instantané du modèle actuel. Cela a pour effet de créer une version spécifique du modèle, qui est celle qui sera déployée. Vous pourrez ainsi continuer à améliorer la version en cours. L'option Déployer n'apparaît pas tant que vous ne créez pas au moins une version.

    **Remarque **: Chaque version ne peut être déployée que sur une seule instance de service. Si vous voulez déployer le même modèle sur plusieurs instances, créez une version pour chaque instance.

1. Cliquez sur **Déployer**, optez pour le déploiement sur {{site.data.keyword.discoveryshort}}, puis cliquez sur **Suivant**.
1. Sélectionnez l'espace et l'instance {{site.data.keyword.Bluemix_notm}}. Si nécessaire, sélectionnez une région différente.
1. Cliquez sur **Déployer**.
1. Le processus de déploiement peut prendre quelques minutes. Pour savoir où il en est, cliquez sur **Statut** sous l'onglet **Versions**, à côté de la version déployée.

    Si le modèle est toujours en cours de déploiement, le statut indiqué est "publication en cours". Une fois le déploiement terminé, le statut passe à "disponible" si l'opération a réussi ou "erreur" si des problèmes ont été rencontrés.

    Une fois le modèle disponible, prenez note de son ID (model_id). Vous devrez le fournir au service {{site.data.keyword.discoveryshort}} afin que celui-ci puisse utiliser votre modèle personnalisé.

### Que faire ensuite
{: #wks_madiscovery_next}

Pour utiliser le modèle déployé, vous devez fournir son ID lorsqu'il vous est demandé au cours du processus de configuration d'enrichissement du service {{site.data.keyword.discoveryshort}}. Pour plus de détails, consultez la [documentation du service {{site.data.keyword.discoveryshort}}![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/services/discovery/integrate-wks.html){: new_window}.

## Déployer un modèle d'apprentissage automatique sur IBM Watson Natural Language Understanding
{: #wks_manlu}

Lorsque vous êtes satisfait des performances du modèle, vous pouvez en déployer une version sur {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}}. Cette fonctionnalité permettra à vos applications d'utiliser le modèle d'apprentissage automatique déployé pour analyser les caractéristiques sémantiques de textes, notamment les entités et les relations qu'ils contiennent.

### Avant de commencer
{: #wks_manlu_prereqs}

Vous devez avoir un service {{site.data.keyword.nlushort}} sur lequel déployer votre modèle. Vous devez aussi connaître les noms d'espace et d'instance {{site.data.keyword.Bluemix_notm}} associés à ce service. Si vous avez oublié ces noms, retrouvez-les en vous connectant à {{site.data.keyword.Bluemix_notm}}. Si vous n'avez pas de compte {{site.data.keyword.Bluemix_notm}}, inscrivez-vous afin d'en obtenir un.

### A propos de cette tâche
{: #wks_manlu_about}

Lorsque vous déployez le modèle d'apprentissage automatique, vous devez sélectionner quelle version de celui-ci vous voulez déployer.

### Procédure
{: #wks_manlu_procedure}

Pour déployer un modèle d'apprentissage automatique sur le service {{site.data.keyword.nlushort}}, effectuez les étapes suivantes :

1. Connectez-vous en tant qu'administrateur ou chef de projet {{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de travail.
1. Sélectionnez **Modèle d'apprentissage automatique** > **Versions**.
1. Choisissez la version du modèle que vous voulez déployer.

    Si une seule version du modèle est fonctionnelle, créez un instantané du modèle actuel. Cela a pour effet de créer une version spécifique du modèle, qui est celle qui sera déployée. Vous pourrez ainsi continuer à améliorer la version en cours. L'option Déployer n'apparaît pas tant que vous ne créez pas au moins une version.

    **Remarque **: Chaque version ne peut être déployée que sur une seule instance de service. Si vous voulez déployer le même modèle sur plusieurs instances, créez une version pour chaque instance.

1. Cliquez sur **Déployer**, optez pour le déploiement sur {{site.data.keyword.nlushort}}, puis cliquez sur **Suivant**.
1. Sélectionnez l'espace et l'instance {{site.data.keyword.Bluemix_notm}}. Si nécessaire, sélectionnez une région différente.
1. Cliquez sur **Déployer**.
1. Le processus de déploiement peut prendre quelques minutes. Pour savoir où il en est, cliquez sur **Statut** sous l'onglet **Versions**, à côté de la version déployée. Si le modèle est toujours en cours de déploiement, le statut indiqué est "publication en cours". Une fois le déploiement terminé, le statut passe à "disponible" si l'opération a réussi ou "erreur" si des problèmes ont été rencontrés.

    Une fois le modèle disponible, prenez note de son ID (model_id). Vous devrez le fournir au service {{site.data.keyword.nlushort}} afin que celui-ci puisse utiliser votre modèle personnalisé.

### Que faire ensuite
{: #wks_manlu_next}

Pour utiliser la version déployée de votre modèle personnalisé, vous devez fournir son ID dans le paramètre `entities.model`.

Vous pouvez utiliser le modèle avec la demande {{site.data.keyword.nlushort}} `GET /analyze` pour extraire les caractéristiques suivantes :

- **entités**

    La commande suivante trouve les entités présentes dans la phrase passée via le paramètre text :

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=entities"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    Le service retourne un objet JSON des instances de types d'entités qu'il a trouvées, compte tenu de ce qui est défini dans le modèle personnalisé :

    ```javascript
    {
      "language": "en",
      "entities": [
        {
          "type": "MANUFACTURER",
          "text": "Honda",
          "count": 1
        },
        {
          "type": "MODEL",
          "text": "Civic",
          "count": 1
        },
        {
          "type": "VEHICLE",
          "text": "Vehicle 1",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "two lane undivided roadway",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "curve",
          "count": 1
        },
        {
          "type": "MODEL_YEAR",
          "text": "1995",
          "count": 1
        },
        {
          "type": "CONDITION",
          "text": "negotiating",
          "count": 1
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

- **relations**

    La commande suivante trouve les relations présentes dans la phrase passée via le paramètre text :

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=relations"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    Le service retourne un objet JSON des instances de types de relations qu'il a trouvées, compte tenu de ce qui est défini dans le modèle personnalisé :

    ```javascript
    {
      "relations": [
        {
          "type": "timeOf",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.954254,
          "arguments": [
            {
              "text": "1995",
              "entities": [
                {
                  "type": "Date",
                  "text": "1995"
                }
              ]
            },
            {
              "text": "Honda Civic",
              "entities": [
                {
                  "type": "SportingEvent",
                  "text": "Honda Civic"
                }
              ]
            }
          ]
        },
        {
          "type": "locatedAt",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.40592,
          "arguments": [
            {
              "text": "negotiating",
              "entities": [
                {
                  "type": "EventMeeting",
                  "text": "negotiating"
                }
              ]
            },
            {
              "text": "roadway",
              "entities": [
                {
                  "type": "Facility",
                  "text": "roadway"
                }
              ]
            }
          ]
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

Pour plus de détails, consultez la [documentation de {{site.data.keyword.nlushort}}![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/services/natural-language-understanding/index.html){: new_window}.

## Retirer des modèles du déploiement
{: #undeploy-view-model}

Si vous voulez retirer un modèle du déploiement ou simplement trouver son ID, consultez la page **Modèles déployés**.

### A propos de cette tâche
{: #wks_undeploy_about}

Ce que vous voyez sur la page Modèles déployés dépend de la [région ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/resources/services_region.html){: new_window} qui héberge votre instance {{site.data.keyword.knowledgestudioshort}}. Si la région prend en charge les instances gérées par les méthodes de gestion des accès [IAM ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/iam/users_roles.html){: new_window} et [Cloud Foundry ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/iam/cfaccess.html){: new_window}, un onglet est visible pour chaque méthode. Les modèles des instances gérées par IAM sont listés sous l'onglet **Groupes de ressources**. Les modèles des instances gérées par Cloud Foundry sont listés sous l'onglet **Organisations**. 

Si la région prend en charge les instances gérées par seulement une des deux méthodes de gestion des accès, vous ne voyez qu'une seule liste de modèles, car une seule méthode de gestion des accès est applicable.

### Procédure
{: #wks_deploy_procedure}

Pour retirer un modèle du déploiement ou trouver son ID :

1. Lancez {{site.data.keyword.knowledgestudioshort}}.
1. Dans le menu **Paramètres** de la barre de menus, en haut à droite, sélectionnez **Gérer les modèles déployés**.
1. Dans la liste des modèles déployés, localisez le modèle que vous souhaitez voir ou retirer du déploiement.
1. Pour retirer le modèle du déploiement, cliquez sur **Annuler le déploiement du modèle** dans la dernière colonne de la ligne où il figure.
1. Pour trouver l'ID du modèle, consultez la colonne **ID modèle**.

Dans le cas d'un modèle à base de règles ou d'un modèle d'apprentissage automatique, vous pouvez aussi retirer le modèle du déploiement à partir de la page Versions.

## Tirer parti d'un modèle d'apprentissage automatique dans IBM Watson Explorer
{: #wks_maexport}

Exportez le modèle d'apprentissage automatique entraîné afin qu'il puisse être exploité dans {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Avant de commencer
{: #wks_maexport_prereqs}

Si vous choisissez d'identifier les types de relations et de les annoter, vous devez en définir au moins deux et annoter les instances des relations dans les données de référence avant d'exporter le modèle. Si vous ne définissez et n'annotez qu'un seul type de relation, cela risque d'entraîner des problèmes ultérieurs dans {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, édition 11.0.1.0.

### A propos de cette tâche
{: #wks_maexport_about}

A présent que votre modèle d'apprentissage automatique est entraîné à reconnaître les entités et les relations dans un domaine spécifique, vous pouvez en tirer parti dans {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

Cliquez sur [ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window} pour visionner une vidéo de moins de 2 minutes illustrant comment exporter un modèle et l'utiliser dans {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procédure
{: #wks_maexport_procedure}

Pour exploiter un modèle d'apprentissage automatique dans {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, effectuez les étapes suivantes :

1. Connectez-vous en tant qu'administrateur ou chef de projet {{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de travail.
1. Sélectionnez **Modèle d'apprentissage automatique** > **Versions**.
1. Cliquez sur **Exporter le modèle en cours**.

    Si vous avez un abonnement à un plan Lite, aucune option d'exportation n'est disponible.

    Le modèle est sauvegardé en tant que fichier ZIP, que vous êtes invité à télécharger.

1. Téléchargez le fichier sur votre système local.
1. A partir de l'application {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, importez le modèle.

    Vous pouvez dès lors associer le modèle à un modèle d'apprentissage automatique dans {{site.data.keyword.watson}} Explorer Content Analytics. Une fois cette association réalisée, lorsque vous explorerez des documents, le modèle trouvera les instances d'entités et de relations qu'il a appris à reconnaître. Pour découvrir comment importer et configurer le modèle dans {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, référez-vous au document technique (en anglais) décrivant l'intégration : [http://www.ibm.com/support/docview.wss?uid=swg27048147 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window}.

#### Tâches connexes
{: #wks_maexport_related}

[Exporter des documents analysés de {{site.data.keyword.watson}} Explorer Content Analytics](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
