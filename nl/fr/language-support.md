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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/services/knowledge-studio/language-support.html){: new_window}.
{: tip}

# Support multilingue
{: #language-support}

{{site.data.keyword.knowledgestudiofull}} prévoit la possibilité d'entraîner un modèle dans plusieurs langues.

Le support multilingue ne signifie pas que le produit lui-même est traduit. Les interfaces utilisateur, les messages et la documentation de {{site.data.keyword.knowledgestudioshort}} ne sont disponibles qu'en anglais.
{: shortdesc}

Vous pouvez entraîner un modèle dans les langues suivantes :

- Anglais (la langue par défaut)
- Arabe
- Portugais brésilien
- Chinois simplifié
- Néerlandais
- Français
- Allemand
- Italien
- Japonais
- Coréen
- Espagnol

Le support multilingue inclut la possibilité d'ajouter à un espace de travail des documents écrits dans ces langues, d'ajouter des dictionnaires, d'exécuter la pré-annotation, d'utiliser l'éditeur de données de référence pour annoter les documents et d'entraîner un modèle d'apprentissage automatique. Lorsque vous sélectionnez une langue, le système applique des canevas spécifiques à cette langue pour traiter les entrées des dictionnaires, le découpage du texte en unités lexicales (analyse lexicale) et la segmentation en phrases. Pour des informations sur la manière dont le système traite les dictionnaires dans différentes langues, consultez [Dictionnaires](/docs/services/watson-knowledge-studio/dictionaries.html#wks_dictionaries).

> **Remarque :** L'éditeur de règle et le modèle à base de règles ne peuvent pas traiter le texte bidirectionnel. Ils sont donc inutilisables avec des documents en arabe.

> **Restrictions :**
>
> En raison de restrictions sur les caractères dans la technologie sous-jacente d'apprentissage automatique, les entrées dans le système de types ne peuvent pas contenir d'espaces et ne peuvent inclure que les caractères ASCII suivants :
>
> - A à Z et a à z
> - 0 à 9
> - Trait de soulignement (_)
>
> Les règles suivantes s'appliquent également :
>
> - Le premier caractère d'un nom doit être une lettre.
> - Le nom d'un type d'entité ne peut pas comporter plus de 64 caractères.
> - Le nom d'un type de relation ne peut pas comporter plus de 128 caractères.
>
> Ainsi, par exemple, lorsqu'un annotateur humain annote du texte en japonais dans l'éditeur de données de référence, les noms des types d'entités et des types de relations qu'il applique ne sont pas en japonais.

### Tâches connexes

[Configurer le support de l'arabe](/docs/services/watson-knowledge-studio/language-support-arabic.html)
