---

copyright:
  years: 2018
lastupdated: "2018-07-02"

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

# Rôles d'utilisateur dans {{site.data.keyword.knowledgestudioshort}}
{: #roles}

Dans {{site.data.keyword.knowledgestudiofull}}, les rôles servent à organiser l'équipe de personnes chargées de créer les modèles d'apprentissage automatique ou à base de règles.
{: shortdesc}

## Remarques à propos des rôles d'utilisateur dans {{site.data.keyword.knowledgestudioshort}}
{: #notes}

- Les rôles d'utilisateur dans {{site.data.keyword.knowledgestudioshort}} sont gérés aux niveaux suivants :
  - Les rôles {{site.data.keyword.cloud}} contrôlent l'accès aux services {{site.data.keyword.cloud_notm}}. Comme {{site.data.keyword.knowledgestudioshort}} utilise Cloud Foundry pour le contrôle des accès, les utilisateurs de {{site.data.keyword.knowledgestudioshort}} doivent avoir le rôle de développeur. Pour plus d'informations, consultez [Accès Cloud Foundry ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/iam/cfaccess.html){: new_window}.
  - Les rôles {{site.data.keyword.knowledgestudioshort}} contrôlent l'accès aux fonctionnalités de {{site.data.keyword.knowledgestudioshort}}, comme décrit sur cette page.
- Vous n'avez pas besoin d'un rôle {{site.data.keyword.knowledgestudioshort}} pour créer une instance de {{site.data.keyword.knowledgestudioshort}}. Cependant, lorsque quelqu'un crée une instance de {{site.data.keyword.knowledgestudioshort}}, le premier utilisateur à lancer {{site.data.keyword.knowledgestudioshort}} se voit attribuer le rôle d'administrateur (Admin) {{site.data.keyword.knowledgestudioshort}}.
- Pour pouvoir gérer un espace de travail, les chefs de projet doivent être affectés à celui-ci par un administrateur. 
- Administrateurs et chefs de projet peuvent prendre part aux tâches d'annotation humaine (et donc assumer le rôle d'annotateur humain), mais ils doivent être affectés aux jeux d'annotations de la même manière que le sont les annotateurs humains.
- Lorsqu'un rôle est attribué à un utilisateur, il n'est plus possible de rétrograder celui-ci à un rôle inférieur en termes de niveau d'autorisations. Ainsi, un administrateur ne peut pas être rétrogradé au rang de chef de projet ou d'annotateur humain et un chef de projet ne peut pas être rétrogradé au rang d'annotateur humain. Pour des informations sur l'ajout d'utilisateurs, le passage d'utilisateurs à un rôle supérieur et la désactivation de comptes d'utilisateurs, consultez [Constituer une équipe](/docs/services/watson-knowledge-studio/team.html).

## Description des rôles
{: #descriptions}
Les rôles {{site.data.keyword.knowledgestudioshort}} sont décrits dans le tableau suivant. Ils sont listés par ordre décroissant de niveau d'autorisation.

| Rôle | Description |
|------|-------------|
| Admin | Responsable des tâches administratives, ce qui inclut la gestion des utilisateurs, de la consommation de ressources et des frais mensuels. Dans les grandes équipes, il est rare que l'administrateur participe au développement du modèle.
| Chef de projet | Responsable de l'organisation dans son ensemble de l'espace de travail auquel il a été affecté. Les tâches lui incombant incluent la création du système de types, la gestion des actifs, la gestion du travail d'annotation, l'évaluation du modèle d'apprentissage automatique et le déploiement des modèles. Les utilisateurs ayant ce rôle doivent être des experts du sujet ou domaine considéré, car ce sont eux qui créent le système de types, enseignent le bon usage de celui-ci aux annotateurs humains et évaluent la qualité du modèle. |
| Annotateur humain | Effectue l'étiquetage des mentions d'entités et des mentions de relations dans les documents d'entraînement auxquels il est affecté. Le travail est attribué aux annotateurs humains et supervisé par le chef de projet. Il n'est pas obligatoire que les annotateurs humains soient des experts du sujet ou du domaine concerné, l'essentiel étant qu'ils soient formés par le chef de projet à l'utilisation correcte du système de types. |
{:caption="Tableau 1. Description des rôles" caption-side="top"}

## Autorisations de chaque rôle
{: #permissions}

Utilisez le tableau suivant pour comparer les autorisations des différents rôles. Chaque autorisation figure sur une ligne à part. Si un rôle a cette autorisation, sa colonne est cochée (&checkmark;) sur la ligne correspondante.

| Autorisation | Admin | Chef de projet | Annotateur humain |
|------------|-------|-----------------|-----------------|
| Gérer les accès et les rôles des utilisateurs | &checkmark; |  |  |
| Gérer les espaces de travail | &checkmark; |  |  |
| Créer le système de types et les directives d'annotation | &checkmark; | &checkmark; |  |
| Transférer les documents d'entraînement | &checkmark; | &checkmark; |  |
| Gérer les règles | &checkmark; | &checkmark; |  |
| Pré-annoter des documents | &checkmark; | &checkmark; |  |
| Gérer les tâches d'annotation | &checkmark; | &checkmark; |  |
| Résoudre les conflits d'annotations avec l'annotation humaine (*arbitrage*) | &checkmark; | &checkmark; |  |
| Entraîner et évaluer les modèles d'apprentissage automatique | &checkmark; | &checkmark; |  |
| Déployer et retirer du déploiement les modèles dans les services d'exécution | &checkmark; | &checkmark; |  |
| Effectuer l'annotation de documents | &checkmark; | &checkmark; | &checkmark; |
{:caption="Tableau 2. Autorisations de chaque rôle" caption-side="top"}
