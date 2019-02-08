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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/services/knowledge-studio/create-project.html){: new_window}.
{: tip}

# Créer un espace de travail
{: #create-project}

Lorsque vous construisez un modèle personnalisé, la première étape est de créer un espace de travail.
{: shortdesc}

## A propos de cette tâche

Vous devez créer un espace de travail pour chaque modèle que vous voulez construire et utiliser. Cet espace contiendra les artefacts et les ressources nécessaires à la construction du modèle. Vous pourrez ensuite entraîner le modèle afin d'obtenir un modèle personnalisé qui pourra être déployé sur un service externe afin d'y être exploité.

Avant de créer un espace de travail, répondez à ces questions :

- **Quel type de modèle voulez-vous créer ?**

    - Modèle d'apprentissage automatique : utilise une approche statistique pour trouver les entités et les relations dans les documents. Ce type de modèle peut s'adapter à mesure que la quantité de données croît.
    - Modèle à base de règles : utilise une approche déclarative pour trouver les entités dans les documents. Ce type de modèle est plus prévisible et plus facile à comprendre et à tenir à jour. Il n'a cependant pas la capacité à apprendre de nouvelles données. Il peut seulement trouver des motifs qu'on lui a appris à rechercher.

    > **Remarque :** Vous pouvez aussi créer un seul espace de travail contenant un modèle à base de règles et un modèle d'apprentissage automatique.

- **Quels services utilisera le modèle ?**

    Consultez [Intégration entre services {{site.data.keyword.watson}}](/docs/services/watson-knowledge-studio/index.html#wks_watsoninteg) pour des informations sur les autres services {{site.data.keyword.watson}} avec lesquels les modèles personnalisés peuvent être utilisés.

## Procédure

Pour créer un espace de travail, effectuez les étapes suivantes :

1. Connectez-vous en tant qu'administrateur {{site.data.keyword.knowledgestudioshort}} et cliquez sur **Créer un espace de travail**.

    > **Remarque :** Les personnes ayant le rôle de chef de projet peuvent effectuer toutes les tâches sauf créer un espace de travail. C'est à l'administrateur de créer l'espace de travail et d'y affecter des chefs de projet.

1. Donnez un nom à l'espace de travail. Choisissez un nom court, reflétant les contenus relatifs à votre domaine ou la finalité du modèle. Ce nom pourra être changé ultérieurement si nécessaire.
1. Identifiez la langue des documents que contiendra votre espace de travail. Les documents que vous ajoutez à l'espace de travail, ainsi que les dictionnaires que vous créez ou transférez, devront être dans cette langue.
1. Optionnel : l'analyseur lexical (tokenizer) utilisé par défaut par l'application est basé sur un modèle d'apprentissage automatique. Si vous voulez en changer, vous pouvez étendre la section **Options avancées** et choisir **Marqueur sémantique basé sur un dictionnaire**.

    L'analyseur lexical par défaut est plus avancé que la version à dictionnaires ; il utilise un modèle d'apprentissage automatique pour identifier les unités lexicales dans les documents source sur la base de l'apprentissage statistique qu'il a effectué dans la langue de ces documents. Il identifie les unités lexicales avec plus de précision, car il comprend les motifs plus naturels et nuancés du langage. L'analyseur lexical à base de dictionnaires identifie les unités lexicales en fonction des règles de la langue. Pour plus de détails, consultez [Analyseurs lexicaux](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

1. Optionnel : si vous voulez ajouter des chefs de projet à l'espace de travail, développez la section **Options avancées** et, dans la liste, sélectionnez les noms des personnes à ajouter. Plus tard, l'administrateur pourra ajouter ou retirer des chefs de projet en éditant l'espace de travail.

    Seuls sont affichés les noms des personnes auxquelles vous avez attribué le rôle de chef de projet dans la page User Account Management (gestion des comptes d'utilisateur) de l'instance. Pour plus d'informations sur l'ajout d'utilisateurs, consultez [Constituer une équipe](/docs/services/watson-knowledge-studio/team.html).

    > **Remarque :** Si vous avez un abonnement à un plan Lite, sautez cette étape. Comme vous ne pouvez pas ajouter d'autres utilisateurs, vous ne pouvez attribuer le rôle de chef de projet à personne. Vous n'avez pas besoin d'un chef de projet distinct. En tant qu'administrateur, vous pouvez accomplir toutes les tâches qui reviendraient normalement à un chef de projet.

1. Cliquez sur **Créer**.

## Que faire ensuite

Une fois l'espace de travail créé, vous pouvez commencer à configurer ses ressources.

Un administrateur peut éditer l'espace de travail pour changer sa description ou son nom, ou encore pour y ajouter ou en retirer des chefs de projet. A partir de la page d'accueil de {{site.data.keyword.knowledgestudioshort}}, cliquez sur l'icône **Afficher le menu** de la vignette de l'espace de travail et choisissez l'option **Editer**.

**Concepts connexes** :

[Transférer des ressources d'un autre espace de travail](/docs/services/watson-knowledge-studio/exportimport.html)

**Référence associée** :

[Support multilingue](/docs/services/watson-knowledge-studio/language-support.html)

## Analyseurs lexicaux
{: #wks_tokenizer}

Un analyseur lexical groupe les caractères en unités lexicales et les unités lexicales en phrases. Une unité lexicale est plus ou moins équivalente à un mot.

Les actions à entreprendre par l'analyseur lexical pour identifier les unités lexicales dans un document dépendent de la langue de ce dernier. Dans les langues telles que le français ou l'anglais, les unités lexicales sont souvent assimilées à des mots délimités par des espaces dans une phrase. La correspondance exacte entre unités lexicales et mots n'est cependant pas systématique. Il existe en effet des cas où d'autres éléments textuels ont valeur d'unités lexicales. Par exemple, la ponctuation à la fin d'une phrase compte pour une unité lexicale et les contractions sont souvent étendues en deux unités lexicales. Dans les langues qui n'utilisent pas d'espaces, comme le chinois, des algorithmes statistiques plus complexes sont utilisés pour identifier les unités lexicales.

Le processus de découpage en unités lexicales est important, car il détermine les groupes de caractères que les utilisateurs pourront surligner pour les annoter dans l'éditeur de données de référence. Les annotations des mentions d'entités et de relations sont généralement alignées avec les limites des unités lexicales concernées. Elles doivent obligatoirement figurer au sein d'une même phrase (elles ne peuvent pas s'étendre sur plusieurs phrases).

### Types pris en charge

{{site.data.keyword.knowledgestudioshort}} prévoit les analyseurs lexicaux suivants :

- **Analyseur lexical à base d'apprentissage automatique (par défaut)**

    C'est le plus avancé des deux analyseurs. Il identifie les unités lexicales dans les documents source sur la base de l'apprentissage statistique qu'il a effectué dans la langue de ces documents. Il est capable de trouver les unités lexicales capturant les motifs plus naturels et nuancés du langage. Vous ne pouvez pas le personnaliser.

- **Analyseur lexical à base de dictionnaires**

    Cet analyseur est basé sur des dictionnaires linguistiques. Il trouve les unités lexicales qui obéissent aux règles de la langue du document source. Seuls des utilisateurs avancés peuvent personnaliser cet analyseur.

L'analyseur lexical que vous prévoyez d'utiliser doit être choisi au moment où vous créez l'espace de travail, car après, vous ne pouvez plus en changer. Pour les meilleurs résultats, utilisez l'analyseur lexical par défaut. Seuls les utilisateurs avancés souhaitant infléchir le comportement d'analyse lexicale au moyen d'un mécanisme à dictionnaires déterministe peuvent choisir l'analyseur lexical à base de dictionnaires. Ils peuvent le personnaliser en ajoutant de nouvelles entrées aux dictionnaires. Cependant, la personnalisation doit être faite avec soin, car lorsque vous ajoutez de nouveaux mots à un dictionnaire, les changements peuvent avoir un impact non souhaité sur le modèle d'apprentissage automatique.

## Synthèse des entrées, des sorties et des limites
{: #wks_formats}

Les différentes phases du développement d'un modèle requièrent différentes entrées et produisent différentes sorties.

Pour chaque phase du processus de développement, ce tableau résume les activités typiques à entreprendre, les formats de fichier d'entrée acceptés, les sorties qui peuvent être produites et les éventuelles limites de taille ou autres conditions à remplir.

### Tous types de modèles

<table summary="Tableau récapitulant les entrées, les sorties et les limites pour tous les types de modèles.">
  <caption>Tableau 1. Tous types de modèles</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e252">
      Tâche
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e254">
      Activité typique
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e256">
      Formats d'entrée acceptés
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e258">
      Formats de sortie possibles
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e260">
      Limites et conditions
    </th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>Gestion d'un système de types</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>Créer un système de types ou transférer et modifier un système de types existant.</p>
      <p>Définir les types d'entités et les types de relations de votre
domaine.</p>
      <p>Vous ne pouvez pas obtenir de visualisation du système de types.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <ul>
        <li>
          <p>Fichier JSON que vous avez téléchargé d'un espace de travail {{site.data.keyword.knowledgestudioshort}}</p>
        </li>
        <li>
          <p>Fichier ZIP que vous avez téléchargé de Human Annotation Tool (HAT)</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>JSON</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>Pour éviter toute surcharge visuelle dans l'annotation humaine,
ne définissez pas plus de 50 types d'entités et 50 types de relations.</p>
      <p>Limite de taille du fichier pour le transfert d'un système de types : 20 Mo</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>Gestion des dictionnaires</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>Transférer un fichier de dictionnaire CSV en lecture seule
ou un fichier ZIP de dictionnaires que vous avez téléchargé d'un autre espace de travail.</p>
      <p>Créer un nouveau dictionnaire (vide), puis y ajouter des entrées créées une à une ou récupérées d'un fichier CSV que vous transférez.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <p>Fichier de dictionnaire :</p>
      <ul>
        <li>
          <p>Fichier CSV au format UTF-8</p>
        </li>
        <li>
          <p>Fichier ZIP de dictionnaires téléchargé d'un autre espace de travail</p>
        </li>
      </ul>
      <p>Fichier d'entrées de termes :</p>
      <ul>
        <li>
          <p>Fichier CSV au format UTF-8</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>Fichier CSV au format UTF-8</p>
        </li>
        <li>
          <p>Fichier ZIP de dictionnaires à utiliser dans un autre espace de travail</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>Limites de taille des fichiers :</p>
      <ul>
        <li>
          <p>1 Mo par fichier CSV d'entrées de termes</p>
        </li>
        <li>
          <p>16 Mo par fichier de dictionnaire CSV en lecture seule</p>
        </li>
        <li>
          <p>15 000 entrées par dictionnaire, sauf si lecture seule</p>
        </li>
        <li>
          <p>64 dictionnaires par espace de travail</p>
        </li>
      </ul>
    </td>
  </tr>
</table>

 {: #wks_formats__datasimpletable_xxj_qr5_2y}

### Modèle d'apprentissage automatique

<table summary="Tableau récapitulant les entrées, les sorties et les limites du modèle d'apprentissage automatique.">
  <caption>Tableau 2. Modèle d'apprentissage automatique</caption>
  <tr>
    <th style="vertical-align:botton; text-align:left" id="d25459e331">Tâche</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e333">Activité typique</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e335">Formats d'entrée acceptés</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e337">Formats de sortie possibles</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e339">Limites et conditions</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Gestion des documents </p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Transférer un petit sous-ensemble représentatif de documents</p>
      <p>Télécharger des documents contenant des annotations précédemment ajoutées par un annotateur humain,
un modèle d'apprentissage automatique ou un moteur d'analyse UIMA</p>
      <p>Il n'est pas possible d'ingérer la totalité du corpus d'{{site.data.keyword.ibmwatson_notm}} Explorer pour déterminer quels sont les documents de grande valeur pour l'annotation.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <ul>
        <li>
          <p>Fichier CSV au format UTF-8</p>
        </li>
        <li>
          <p>Fichier texte au format UTF-8</p>
        </li>
        <li>
          <p>Fichier ZIP contenant des documents précédemment téléchargés d'un autre corpus</p>
        </li>
        <li>
          <p>Fichier ZIP contenant des fichiers XMI au format UIMA CAS</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>Fichier ZIP de documents</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>40.000 caractères par document</p>
        </li>
        <li>
          <p>10.000 documents par espace de travail</p>
        </li>
        <li>
          <p>1.000 jeux de documents (jeux d'annotations compris) par espace de travail</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Pré-annotation</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
       <p>Utiliser un pré-annotateur à base de dictionnaire
ou un pré-annotateur {{site.data.keyword.nlufull}} pour fournir le point de départ de
l'annotation humaine.</p>
       <p>Vous ne pouvez pas ré-annoter un corpus d'{{site.data.keyword.ibmwatson_notm}} Explorer.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Documents bruts.</p>
      <p><b>Remarque :</b> Vous ne devez pas pré-annoter des documents déjà annotés par un humain, sous peine de
perdre le travail de ce dernier.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Documents partiellement annotés</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>Néant</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Annotation de documents</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Gérer l'annotation humaine</p><p>Annoter les entités, les relations et les chaînes de coréférences
pour créer les données de référence</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Tâche d'annotation</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Données de référence</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>256 tâches d'annotation actives par espace de travail</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Entraînement et raffinement</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Entraîner un modèle d'apprentissage automatique supervisé
pour extraire de textes non structurés l'information spécifique d'un domaine.</p><p>Evaluer et améliorer un modèle d'apprentissage automatique supervisé.</p>
      <p>Vous ne pouvez pas créer de modèle d'apprentissage automatique semi-supervisé ou non supervisé.</p>
      <p>Vous ne pouvez pas effectuer d'ingénierie de caractéristiques
(feature engineering) très poussée.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Non applicable</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Modèle d'apprentissage automatique</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>1 modèle d'apprentissage automatique par espace de travail</p>
        </li>
        <li>
          <p>10 versions du modèle par espace de travail</p>
        </li>
        <li>
          <p>Le nombre maximum d'espaces de travail est fonction de votre plan d'abonnement.</p>
        </li>
        <li>
          <p>Le nombre maximum d'actions d'entraînement qu'il est possible d'exécuter chaque mois est fonction de votre plan d'abonnement.</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Publication</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Publier un modèle d'apprentissage automatique pour qu'il puisse servir à extraire du texte dans d'autres applications {{site.data.keyword.watson}}.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Non applicable</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>ID du modèle (pour utilisation dans {{site.data.keyword.nlufull}} ou {{site.data.keyword.discoveryfull}})</p>
        </li>
        <li>
          <p>Fichier ZIP (pour utilisation dans {{site.data.keyword.ibmwatson_notm}} Explorer)</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>Pour un déploiement sur les services {{site.data.keyword.watson}}, vous devez connaître les noms d'espace et d'instance du service {{site.data.keyword.cloud_notm}}.</p>
    </td>
  </tr>
</table>

### Modèle à base de règles

<table summary="Tableau récapitulant les entrées, les sorties et les limites pour le modèle à base de règles.">
  <caption>Tableau 3. Modèle à base de règles</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e509">
      Tâche
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e511">
      Activité typique
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e513">
      Formats d'entrée acceptés
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e515">
      Formats de sortie possibles
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e517">
      Limites et conditions
    </th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>Editeur de règle</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>Créer ou transférer dans l'éditeur de règle des documents à partir desquels seront définies des classes, des expressions régulières et des règles.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <ul>
        <li>
          <p>Texte standard (ajouté dans l'éditeur)</p>
        </li>
        <li>
          <p>Fichier CSV au format UTF-8</p>
        </li>
        <li>
          <p>Copie à partir de tous les jeux de documents</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <p>Néant</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <ul>
        <li>
          <p>1 modèle à base de règles par espace de travail</p>
        </li>
        <li>
          <p>5.000 caractères par document</p>
        </li>
        <li>
          <p>100 documents par espace de travail</p>
        </li>
        <li>
          <p>Titre de document limité à 256 caractères</p>
        </li>
        <li>
          <p>200 règles par espace de travail</p>
        </li>
        <li>
          <p>400 classes par espace de travail</p>
        </li>
        <li>
          <p>100 groupes d'expressions régulières par espace de travail</p>
        </li>
        <li>
          <p>100 entrées d'expression régulière par groupe d'expressions régulières</p>
        </li>
        <li>
          <p>1.000 caractères par entrée d'expression régulière</p>
        </li>
        <li>
          <p>5 versions du modèle à base de règles par espace de travail</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>Publication</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>Publier un modèle à base de règles pour qu'il puisse servir à la reconnaissance de motifs dans d'autres applications {{site.data.keyword.watson}}.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <p>Non applicable</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <ul>
        <li>
          <p>ID du modèle (pour utilisation dans {{site.data.keyword.nlufull}} ou {{site.data.keyword.discoveryfull}})</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <p>Pour un déploiement sur les services {{site.data.keyword.watson}}, vous devez connaître les noms d'espace et d'instance du service {{site.data.keyword.cloud_notm}}.</p>
    </td>
  </tr>
</table>
