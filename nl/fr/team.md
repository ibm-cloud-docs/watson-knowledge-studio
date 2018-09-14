---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-18"

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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/team.html){: new_window}.
{: tip}

# Constituer une équipe
{: #team}

La création d'un modèle nécessite le concours d'experts du domaine, de chefs de projet et d'utilisateurs capables de comprendre et d'interpréter les modèles statistiques. Pour chaque personne devant se connecter à {{site.data.keyword.knowledgestudioshort}}, vous devez ajouter un utilisateur.
{: shortdesc}

**Remarque **: Seuls les plans Standard et Premium peuvent avoir plusieurs utilisateurs. Les plans Lite sont limités à un seul utilisateur. Cet unique utilisateur reçoit d'office le rôle d'administrateur (Admin), c'est-à-dire le rôle ayant le plus de pouvoirs.

## Avant de commencer

- Assurez-vous d'utiliser un navigateur pris en charge. Consultez à cet effet [Navigateur nécessaire](/docs/services/watson-knowledge-studio/system-requirements.html).
- [Créez une instance de {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html#instance).
- Si vous vous êtes inscrit à un plan Standard ou Premium, sous l'onglet **Gérer** d'{{site.data.keyword.cloud_notm}}, invitez dans votre organisation les autres personnes que vous souhaitez ajouter comme utilisateurs dans {{site.data.keyword.knowledgestudioshort}}. Pour plus d'informations sur l'invitation d'utilisateurs, consultez [Invitation d'utilisateurs et affectation d'accès ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/iam/iamuserinv.html){: new_window}.

  **Important** : Assurez-vous que les utilisateurs invités ont le rôle de développeur Cloud Foundry. Pour plus d'informations, consultez [Accès Cloud Foundry ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.

## A propos de cette tâche

En règle générale, vous ajoutez des utilisateurs pour qu'ils assument les rôles d'annotateurs humains et de chefs de projet. Pour une description, consultez [Rôles d'utilisateur dans {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

**Remarque :**

- Si vous vous êtes inscrit à un plan Lite, vous ne pouvez pas ajouter d'autres utilisateurs à votre instance de {{site.data.keyword.knowledgestudioshort}}. Lorsque vous lancez {{site.data.keyword.knowledgestudioshort}}, vous êtes ajouté à l'instance en tant qu'administrateur (rôle Admin). Dans ce cas de figure, le rôle Admin vous permet s'assumer de nombreuses fonctions qui, en temps normal, seraient remplies par différentes personnes ayant différents rôles. Vous pouvez ainsi tester de quelle manière les experts des différentes branches d'un domaine peuvent collaborer à la construction d'un modèle d'apprentissage automatique ou d'un modèle à base de règles.
- Le premier utilisateur à lancer {{site.data.keyword.knowledgestudioshort}} reçoit d'office le rôle d'administrateur (Admin) de l'instance de {{site.data.keyword.knowledgestudioshort}}. La tâche décrite ici part du principe que vous êtes la première personne à lancer {{site.data.keyword.knowledgestudioshort}} après votre inscription à un plan, ce qui signifie que vous avez le rôle Admin.

## Ajouter des utilisateurs dans {{site.data.keyword.knowledgestudioshort}}

Ajoutez des utilisateurs de votre organisation {{site.data.keyword.cloud_notm}} à {{site.data.keyword.knowledgestudioshort}}.

Pour ajouter des utilisateurs à une instance de {{site.data.keyword.knowledgestudioshort}} :

1. Connectez-vous au [Tableau de bord {{site.data.keyword.cloud_notm}}![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net){: new_window} avec votre {{site.data.keyword.ibmid}} et lancez {{site.data.keyword.knowledgestudioshort}}.
1. Cliquez sur l'icône **Paramètres**, puis sur **Gérer les détails du service**.
1. Dans la section **Gérer les utilisateurs**, entrez l'{{site.data.keyword.ibmid}} de l'utilisateur que vous voulez ajouter.
1. Sélectionnez le rôle que vous souhaitez donner à l'utilisateur. Pour une description des rôles disponibles, consultez [Rôles d'utilisateur dans {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

  **Remarque** : Une fois qu'un utilisateur a reçu un rôle donné, vous ne pouvez pas le déclasser (lui attribuer un rôle inférieur). Il est donc important de bien comprendre les tâches que peuvent accomplir les rôles Admin et Chef de projet avant de les attribuer.

1. Cliquez sur **Ajouter**.

## Passer des utilisateurs à un rôle supérieur

Après avoir ajouté des utilisateurs à {{site.data.keyword.knowledgestudioshort}}, vous pouvez faire passer à un rôle supérieur ceux qui ont un rôle aux pouvoirs trop limités. Chaque utilisateur doit recevoir l'un des rôles décrits ci-dessous pour pouvoir accomplir les tâches correspondantes.

**Remarque **: Seuls les plans Standard et Premium peuvent avoir plusieurs utilisateurs. Les plans Lite sont limités à un seul utilisateur, qui a déjà le rôle le plus élevé, Admin.

> **Attention : le déclassement (passage d'un rôle donné à un rôle inférieur) n'est pas permis.**

Pour passer un utilisateur {{site.data.keyword.knowledgestudioshort}} à un rôle supérieur :

1. Connectez-vous au [Tableau de bord {{site.data.keyword.cloud_notm}}![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net){: new_window} avec votre {{site.data.keyword.ibmid}} et lancez {{site.data.keyword.knowledgestudioshort}}.
1. Dans le menu de navigation en haut à droite, cliquez sur l'icône **Paramètres**![icône Paramètres](images/settings.png), puis sur **Gérer les détails du service**. La section **Gérer les utilisateurs** de la page Détails du service contient la liste de tous les ID utilisateur membres de cette instance de {{site.data.keyword.knowledgestudioshort}}.
1. Localisez le nom de l'utilisateur dont vous souhaitez changer le rôle, puis cliquez sur le lien **Editer**.
1. Cliquez sur le rôle actuel de l'utilisateur et choisissez le rôle supérieur auquel vous souhaitez le nommer. Pour une description des rôles disponibles, consultez [Rôles d'utilisateur dans {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

  **Important :** Avant qu'un utilisateur ayant le rôle d'annotateur humain puisse voir un espace de travail dans l'application {{site.data.keyword.knowledgestudioshort}}, vous devez créer cet espace de travail, associer cet utilisateur à un jeu de documents et lui affecter une tâche d'annotation. Mettez en place l'espace de travail dès que possible à compter du moment où les utilisateurs s'inscrivent. Ils pourront ainsi le voir dès leur premier accès à l'application. Lorsque l'espace de travail est prêt, vous pouvez le leur notifier et leur faire savoir qu'ils peuvent commencer à annoter les documents.

1. Optionnel : lorsque vous en avez terminé avec l'administration des utilisateurs dans {{site.data.keyword.knowledgestudioshort}}, mettez fin à la session en fermant le navigateur web. L'interface utilisateur de {{site.data.keyword.knowledgestudioshort}} ne prévoit pas d'action pour vous déconnecter explicitement.

## Désactiver des comptes d'utilisateur

Plus tard, si vous voulez retirer des utilisateurs, ouvrez la page Détails du service en suivant les étapes décrites plus haut. Dans la liste des ID utilisateur, localisez l'utilisateur que vous souhaitez retirer et cliquez sur **Désactiver**.

> **Attention **: La désactivation d'un compte d'utilisateur auquel des documents ont été affectés aura des conséquences sur son travail d'annotation en cours. Celles de ses annotations qui n'ont pas encore été promues au rang de données de référence seront supprimées.

### Tâches connexes

[Créer et affecter des jeux d'annotations](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)
