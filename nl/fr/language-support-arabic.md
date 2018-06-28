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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/language-support-arabic.html){: new_window}.
{: tip}

# Configurer le support de l'arabe
{: #wks_langsupp_ar}

Lisez ce guide pour comprendre comment {{site.data.keyword.knowledgestudioshort}} gère le formage des caractères et des chiffres arabes dans les documents en arabe.

## A propos de cette tâche

En ce qui concerne le formage des caractères, l'alphabet arabe n'a pas de majuscules, mais les lettres peuvent changer de forme en fonction de leur position dans la chaîne de caractères et des lettres qui les entourent. Les différents systèmes d'exploitation et programmes de conversion de pages de codes ne gèrent pas de la même manière le formage des lettres. Sur les systèmes Windows, le texte en arabe est stocké non formé et {{site.data.keyword.knowledgestudioshort}} suppose que c'est ainsi qu'il est stocké. Si vous voulez transférer du texte formé dans {{site.data.keyword.knowledgestudioshort}}, vous devez préalablement le convertir en texte non formé à l'aide d'outils standard tels que l'API ICU (International Components for Unicode). (Consultez la description de la classe Java ArabicShaping sur [http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html){: new_window}.)

> **Important :** Dans certains cas, l'absence de formage correct des caractères arabes peut entraîner un affichage incorrect du contenu dans l'éditeur de données de référence.

En ce qui concerne le formage des nombres, {{site.data.keyword.knowledgestudioshort}} traite celui-ci comme une propriété au niveau du stockage, d'une manière similaire à la gestion des contenus en arabe sur la plateforme iOS. Comme beaucoup de contenus en arabe sont créés sur des plateformes telles que Windows, qui traite le formage des nombres comme une propriété au niveau de l'affichage, vous devez soit convertir ces contenus de manière à faire du formage des nombres une propriété au niveau du stockage, soit utiliser Firefox comme navigateur lorsque vous utilisez {{site.data.keyword.knowledgestudioshort}}. Firefox dispose en effet d'une préférence permettant de fixer explicitement le formage des nombres au niveau du navigateur.

## Procédure

Pour configurer le formage des nombres dans Firefox :

1. Entrez **about:config** dans le champ d'URL du navigateur. Si Firefox affiche un avertissement, cliquez sur le bouton signifiant que vous prenez le risque de continuer. Pour des informations sur l'édition des propriétés **about:config**, consultez [http://kb.mozillazine.org/About:config_entries ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://kb.mozillazine.org/About:config_entries){: new_window}.
1. Tapez `bidi` dans le champ du filtre de recherche.
1. Sélectionnez la propriété **bidi.numeral**, qui contrôle de quelle manière les chiffres sont affichés, et appuyez sur Entrée.
1. Changez la valeur de cette propriété selon nécessité. Par exemple, entrez `3` et cliquez sur **OK**.

    - **0** : Chiffres nominaux (valeur par défaut)
    - **1** : Chiffres du contexte standard
    - **2** : Chiffres du contexte Hindi
    - **3** : Chiffres arabes
    - **4** : Chiffres Hindi

    > **Important :** Lorsque la propriété **bidi.numeral** est utilisée, Firefox ignore complètement le point de code des caractères représentant des chiffres dans le contenu d'une page web.

### Références associées

[Support multilingue](/docs/services/watson-knowledge-studio/language-support.html)
