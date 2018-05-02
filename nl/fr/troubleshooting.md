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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}.
Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/troubleshooting.html){: new_window}.
{: tip}

# Dépannage, assistance et FAQ
{: #troubleshooting}

Pour isoler et résoudre les problèmes avec vos produits
{{site.data.keyword.IBM_notm}}, vous pouvez utiliser
les informations de résolution des problèmes et d'assistance.
Celles-ci contiennent les instructions à suivre pour utiliser les ressources de détermination des problèmes fournies avec vos produits {{site.data.keyword.IBM_notm}}, parmi lesquels {{site.data.keyword.knowledgestudiofull}}.
{: shortdesc}

## Techniques de traitement des problèmes
{: #ts_overview}

La *recherche de panne* est une approche systématique de la résolution d'un problème.
Il s'agit de déterminer la raison pour laquelle un problème s'est produit et d'identifier les moyens d'y remédier.
Certaines techniques courantes peuvent vous aider dans votre recherche de panne. 

La première étape de la recherche de panne est de décrire complètement le problème.
Les descriptions de problèmes aident le représentant du support technique {{site.data.keyword.IBM_notm}} et vous-même à savoir où commencer pour trouver la cause du problème.
Cette étape vous amènera à vous poser quelques questions élémentaires :

- Quels sont les symptômes du problème ?
- Où le problème se produit-il ?
- Quand le problème se produit-il ?
- Dans quelles circonstances le problème se produit-il ?
- L'incident peut-il être reproduit ?

Les réponses à ces questions donnent généralement une bonne description du problème qui peut conduire à sa résolution.

### Quels sont les symptômes du problème ?

Lorsque vous commencez à décrire un problème, la question la plus évidente est "Quel est le problème ?"
Cette question, qui semble simple, peut cependant être décomposée en plusieurs questions plus ciblées qui permettront de mieux décrire le problème.
Ces questions peuvent être :

- Par qui ou par quoi le problème est-il signalé ?
- Quels sont les codes d'erreur et les messages ?
- Comment la défaillance du système se produit-elle ? Par exemple, est-ce une boucle, un blocage, un arrêt brutal, une dégradation des performances ou un résultat incorrect ?

### Où le problème se produit-il ?

Il n'est pas toujours aisé de déterminer à quel endroit survient le problème. C'est pourtant l'une des étapes les plus importantes pour sa résolution.
De nombreuses couches de technologie peuvent exister entre les composants qui signalent le problème et les composants défaillants.
Réseaux, disques et pilotes figurent parmi les composants à examiner dans votre investigation du problème.


Les questions suivantes vous aideront à cerner l'endroit où se produit le problème pour vous permettre d'isoler la couche où il se situe : 

- Le problème est-il spécifique à une plateforme ou un système d'exploitation, ou est-il commun à plusieurs plateformes ou systèmes d'exploitation ?
- L'environnement et la configuration actuels sont-ils pris en charge ?
- Tous les utilisateurs rencontrent-ils ce problème ?
- (Pour les installations multisites) Tous les sites rencontrent-ils ce problème ?

Si le problème est signalé par une couche en particulier, cela ne signifie pas pour autant qu'il est originaire de cette couche.
L'identification de l'origine d'un problème revient en partie à comprendre l'environnement dans lequel il existe.
Prenez quelques instants pour décrire complètement l'environnement du problème, notamment
le système d'exploitation et sa version, tous les logiciels correspondants et leur
version, ainsi que les informations sur le matériel.
Vérifiez que l'environnement d'exécution est bien une configuration prise en charge : de
nombreux problèmes sont imputables à des niveaux de logiciels incompatibles qui n'ont pas
été prévus pour fonctionner ensemble ou dont le fonctionnement concomitant n'a pas encore
fait l'objet de tests exhaustifs.

### Quand le problème se produit-il ?

Etablissez une chronologie détaillée des événements qui ont conduit à une
défaillance, surtout lorsqu'il s'agit d'un problème qui ne s'est produit qu'une fois.
Il est plus facile de décrire le déroulement en commençant par la fin : commencez par le
moment où l'erreur a été signalée (aussi précisément que possible, même à la milliseconde
près) et remontez le cours des événements à l'aide des journaux et informations
disponibles.
Généralement, il n'est pas nécessaire de remonter plus loin que le premier événement suspect enregistré dans un journal de diagnostic.

Pour développer une chronologie détaillée des événements, répondez à ces questions :

- Le problème se produit-il seulement à des moments particuliers du jour ou de la nuit ?
- A quelle fréquence le problème se produit-il ?
- Quelle suite d'événements a précédé le moment où le problème a été signalé ?
- Le problème se produit-il après un changement d'environnement, comme la mise à niveau ou l'installation d'un logiciel ou de matériel ?

Les réponses à ces questions fournissent un cadre de référence pour l'analyse du problème.

### Dans quelles circonstances le problème se produit-il ?

Savoir quels systèmes et applications étaient en cours d'exécution au moment où le problème s'est produit est essentiel à la recherche de panne.
Ces questions sur votre environnement peuvent vous aider à identifier la cause première du problème :

- Le problème se produit-il toujours lorsque la même tâche est exécutée ?
- Faut-il qu'une certaine succession d'événements se produise pour que le problème survienne ?
- D'autres applications échouent-elles au même moment ?

La réponse à ces types de questions peut vous aider à décrire l'environnement dans lequel le problème se produit et à faire le lien avec d'éventuelles dépendances.
N'oubliez pas que si plusieurs problèmes se produisent à peu près au même moment, cela ne signifie pas pour autant qu'ils sont liés entre eux.

### L'incident peut-il être reproduit ?

Du point de vue de la recherche de panne, le problème idéal est celui qui peut être reproduit.
Généralement, dès lors qu'un problème peut être reproduit, vous disposez de plus d'outils ou de procédures pour en rechercher la cause.
Par conséquent, les problèmes que vous pouvez reproduire sont souvent plus faciles à déboguer et à résoudre.

Ces problèmes présentent toutefois un inconvénient. S'ils ont un impact important sur l'activité, vous ne souhaitez pas qu'ils se reproduisent.
Si possible, recréez le problème dans un environnement de test ou de développement qui vous offrira davantage de souplesse et de contrôle pour mener votre enquête.

- Le problème peut-il être recréé sur un système test ?
- Plusieurs utilisateurs ou applications rencontrent-ils le même type de problème ?
- Est-il possible de recréer le problème en exécutant une unique commande, un ensemble de commandes ou une application particulière ?

## Problèmes de modèle AlchemyLanguage
{: #wks_ts_deployed_model_deleted}

### Problème

Vous ne pouvez pas déployer un modèle AlchemyLanguage, ou vous êtes parvenu à le déployer, mais il n'est pas disponible à l'utilisation.

### Symptômes

- Vous avez déployé un modèle, mais son statut montre qu'il s'est produit une erreur.
- Vous avez déployé un modèle, son statut indique qu'il est disponible, mais vous ne parvenez pas à l'utiliser.
- Le modèle a été déployé correctement, il fonctionnait auparavant, mais à présent il ne fonctionne plus.

### Causes

Les événements suivants peuvent être la cause de problèmes avec les modèles déployés :


- Si vous faites une faute de frappe en tapant la
clé {{site.data.keyword.alchemyapishort}} dans le paramètre `apikey` de l'appel d'API REST,
cet appel échouera.
Il en va de même pour l'ID du modèle.
Mieux vaut donc copier et coller ces données pour éviter toute erreur.

- Si vous fournissez une clé {{site.data.keyword.alchemyapishort}} non valide ou
appartenant à un compte qui n'est pas autorisé à publier un modèle personnalisé, le processus de déploiement
indiquera que le modèle a été déployé correctement, mais en réalité, vous ne pourrez pas utiliser celui-ci.

- Si pendant l'utilisation d'{{site.data.keyword.alchemylanguageshort}} dans
{{site.data.keyword.Bluemix}}, vous supprimez toutes les instances de service associées à une clé
{{site.data.keyword.alchemyapishort}} dans
{{site.data.keyword.Bluemix_notm}}, tous les modèles déployés se référant
à cette clé seront retirés du service.
En effet, {{site.data.keyword.Bluemix_notm}} vérifie périodiquement que chaque modèle enregistré est associé à une
clé valide. Si ce n'est pas le cas, il le supprime.
Si votre modèle a été déployé avec une clé qui a ensuite été supprimée, son statut deviendra `erreur`.

### Résoudre le problème

1. Vérifiez le statut du déploiement.


    Connectez-vous en tant qu'administrateur
{{site.data.keyword.knowledgestudioshort}}.
Sur la page **Gestion des modèles** > **Versions**, déterminez le statut du modèle déployé
en consultant la colonne **Statut**.


1. Si le statut de déploiement du modèle est `erreur` ou `disponible`,
mais que le modèle ne fonctionne pas lorsque vous tentez de l'utiliser, retirez-le du déploiement
en cliquant sur **Annuler le déploiement**.
1. Redéployez le modèle.

    Utilisez seulement une clé {{site.data.keyword.alchemyapishort}} valide, associée à un compte autorisé à
déployer des modèles. Pensez aussi à copier et coller (plutôt que de taper à la main) l'ID de modèle et la clé d'API
lorsque vous ajoutez ces données en paramètres de l'appel d'API.


**Tâches connexes** :

[Déployer un modèle d'apprentissage automatique sur {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}](/docs/services/watson-knowledge-studio/publish-ml.html#wks_mabluemix)

## Impossible de créer un compte gratuit
{: #wks_ts_free}

### Problème

Vous tentez de créer un compte gratuit et recevez le message d'erreur `Erreur 331 : Nous ne pouvons pas traiter votre demande. Veuillez réessayer ultérieurement ou contacter le Centre d'assistance {{site.data.keyword.IBM_notm}}.`

### Causes

{{site.data.keyword.knowledgestudioshort}} n'autorise pas plus d'un compte gratuit par organisation.

### Résoudre le problème

Créez un compte qui ne soit pas inclus dans l'organisation.

Si vous avez besoin d'utiliser votre compte d'utilisateur actuel pour l'essai gratuit et que ce compte est associé à un
compte payant, vous pouvez soumettre un ticket de demande de service.
Pour plus d'informations, consultez [Contacter le support {{site.data.keyword.IBM_notm}}](/docs/services/watson-knowledge-studio/troubleshooting.html#ts_contactingibmsupport).

Si vous avez besoin d'utiliser votre compte d'utilisateur actuel pour l'essai gratuit et que ce compte n'est pas associé à un
compte payant, postez votre problème sur [{{site.data.keyword.IBM_notm}} developerWorks Answers](https://developer.ibm.com/answers/topics/wks/),
en veillant à étiqueter la question avec **WKS**.


## Impossible d'accéder à l'application
{: #wks_ts_access}

Découvrez comment accorder aux utilisateurs
l'accès à {{site.data.keyword.knowledgestudioshort}} et remédier aux problèmes d'accès les plus courants.


Pour demander une instance d'{{site.data.keyword.IBM_notm}} {{site.data.keyword.knowledgestudioshort}},
vous devez être en possession des données d'identification (ID et mot de passe)
d'un compte d'utilisateur {{site.data.keyword.IBM_notm}} inscrit.


### Administrateur

A chaque instance d'{{site.data.keyword.knowledgestudioshort}} est associé un rôle d'administrateur.
La personne qui, à l'origine, s'inscrit pour utiliser l'application reçoit ce rôle automatiquement.
L'administrateur peut inviter d'autres personnes.


Pour des informations sur la façon d'inviter d'autres personnes à utiliser votre
instance de l'application, consultez
[Constituer une équipe](/docs/services/watson-knowledge-studio/team.html).

### Annotateur humain

Si vous avez été invité à une instance de {{site.data.keyword.knowledgestudioshort}}
pour y travailler comme annotateur humain, vous avez certainement reçu de son administrateur une invitation par e-mail.
Si vous n'avez pas encore de compte (ID et mot de passe) {{site.data.keyword.IBM_notm}},
vous devez d'abord vous inscrire auprès d'{{site.data.keyword.IBM_notm}}.
Lorsque vous serez inscrit auprès d'{{site.data.keyword.IBM_notm}} et aurez
accepté l'invitation, l'accès à l'instance vous sera accordé.
Cependant, même en ayant accès à l'instance, vous ne pourrez commencer à annoter des documents que lorsque l'administrateur ou le chef de projet
de cette instance vous aura ajouté à un espace de travail et vous aura affecté une
tâche d'annotation dans cet espace.
Ce n'est qu'à compter du moment où une tâche vous est affectée que vous pouvez effectuer une action quelle qu'elle soit
dans l'instance de {{site.data.keyword.knowledgestudioshort}}.
Pour annoter les documents qui vous sont confiés, utilisez l'éditeur de données de référence.
Pour les meilleures performances, utilisez un navigateur Google Chrome.


Pour toute aide à l'utilisation de l'éditeur de données de référence, consultez
[Annoter des documents](/docs/services/watson-knowledge-studio/user-guide.html).

## Services expérimentaux : que signifie *expérimental* ?
{: #experimental}

Pour des informations sur les services expérimentaux, consultez
la [documentation {{site.data.keyword.Bluemix_notm}}](/docs/services/index.html#experimental_services).
Pour des détails complets sur les services expérimentaux,
consultez la dernière version de la [description des services {{site.data.keyword.Bluemix_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/software/sla/sladb.nsf/searchsaas/?searchview&searchorder=4&searchmax=0&query=IBM+Bluemix+Service+Description){: new_window}.

## Problèmes d'espace de stockage
{: #storage}

Si vous atteignez la limite d'espace de stockage, qui varie en fonction de votre plan d'abonnement, vous ne pourrez
pas effectuer les tâches que vous voulez mener à bien.


### Symptômes

En tentant d'effectuer l'une des tâches suivantes, vous recevez un message signalant que vous avez dépassé l'espace de stockage autorisé :


- Transférer des documents ou des dictionnaires 
- Déployer un modèle ou une version d'un modèle 
- Exécuter un pré-annotateur sur des documents

### Causes

La limite de stockage a été atteinte ou serait franchie si l'action était menée jusqu'à son terme.

### Résoudre le problème

Les plus gros consommateurs d'espace de stockage sont les modèles d'apprentissage automatique et les modèles
à base de règles.
Pour libérer de l'espace, vous pouvez prendre les mesures suivantes :


- Supprimez les versions instantanées des modèles auxquelles vous ne pensez pas devoir revenir.

- Supprimez les modèles dont vous n'avez pas besoin. 
- Si vos modèles sont trop importants pour être supprimés, envisagez de passer à un plan qui prévoit un plus grand espace de stockage.


Après avoir supprimé des modèles ou des versions de modèles, attendez au moins une heure avant de retenter
l'action qui a conduit au message d'erreur.
La mise à disposition de l'espace que vous avez libéré peut en effet prendre jusqu'à une heure. 

Si le rôle Admin vous a été attribué et si vous avez un compte Premium ou Standard, pour gérer votre facture mensuelle,
vous pouvez fixer une limite de stockage sur la page Détails du service, dans
l'interface de {{site.data.keyword.knowledgestudioshort}}.
Pour ce faire, dans la barre de navigation supérieure de {{site.data.keyword.knowledgestudioshort}},
cliquez sur l'icône **Paramètres**, puis sur le lien de visualisation/modification des détails du
service**** et enfin sur le lien **Définir la limite de stockage**.
{: tip}

## Contacter le support IBM
{: #ts_contactingibmsupport}

Le support {{site.data.keyword.IBM_notm}} offre une assistance concernant les
défauts du produit, répond aux questions les plus courantes et aide les utilisateurs à
résoudre les problèmes qu'ils rencontrent avec le produit.

### Avant de commencer

Voyez d'abord si une solution à votre problème n'est pas déjà documentée.
Recherchez le terme {{site.data.keyword.knowledgestudioshort}} sur le [portail {{site.data.keyword.IBM_notm}} Support ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/home/entry/portal){: new_window}.
Dans la page des résultats de recherche, cliquez sur l'onglet **Support** pour limiter les
résultats à ceux des notes techniques, des Redbooks {{site.data.keyword.IBM_notm}} et de la documentation.
Cliquez sur l'onglet **For developers** pour voir seulement les
résultats de la communauté {{site.data.keyword.IBM_notm}} developerWorks, comme les blogs et les questions posées sur les forums.


Après avoir tenté de trouver une réponse ou une solution sur
le [portail {{site.data.keyword.IBM_notm}} Support ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/home/entry/portal){: new_window},
vous pouvez contacter le support {{site.data.keyword.IBM_notm}}.
Le type d'assistance dont vous bénéficiez dépend de votre type de service.


- **Utilisateurs du plan gratuit**

    Demandez de l'aide aux autres membres de la communateur des développeurs.
Pour les liens à la communauté des développeurs, consultez
la section **Communauté des développeurs** dans la
table des matières.


- **Utilisateurs d'un plan payant**

    En tant qu'utilisateur d'un plan payant, vous pouvez vous aussi poser des questions aux autres
utilisateurs et bénéficier de leur expérience.
Les forums sont ouverts à tous et sont un bon point de départ.
Pour les liens, consultez
la section **Communauté des développeurs** dans la
table des matières.


    Soumettez un ticket de problème sur l'[{{site.data.keyword.IBM_notm}} Cloud Service Portal ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://watson.service-now.com/wcp){: new_window}.

    > **Remarque :** Vous devez être autorisé à soumettre des problèmes à {{site.data.keyword.IBM_notm}}.

### Procédure

Pour contacter le support {{site.data.keyword.IBM_notm}} à propos d'un problème :


1. Définissez le problème, rassemblez des informations sur le contexte et déterminez l'importance du problème.
1. Collectez les informations de diagnostic, si possible.
1. Soumettez le problème au support {{site.data.keyword.IBM_notm}}. Pour les coordonnées du support à contacter,
référez-vous au [guide du support Software as a Service ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www-01.ibm.com/software/support/acceleratedvalue/SaaS_Handbook_V18.pdf){: new_window}.
