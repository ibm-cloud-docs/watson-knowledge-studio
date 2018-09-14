---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-19"

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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/language-support-arabic.html){: new_window}.
{: tip}

# Configurando o suporte para árabe
{: #wks_langsupp_ar}

Leia estas diretrizes para entender como o {{site.data.keyword.knowledgestudioshort}} manipula a forma de caractere árabe e a forma numérico em documentos em árabe.

## Sobre essa Tarefa

Com relação à forma de caractere, o alfabeto árabe não tem letras maiúsculas, mas as letras podem mudar de forma dependendo de sua posição na sequência de texto e nas letras circundantes.
e das letras circundantes. Diferentes sistemas operacionais e programas de conversão de página de códigos manipulam a forma de letra de maneiras diferentes. O armazenamento sem forma é um padrão para sistemas Windows e o {{site.data.keyword.knowledgestudioshort}} supõe que o texto em árabe esteja armazenado sem forma. Se você deseja fazer upload do texto com forma no {{site.data.keyword.knowledgestudioshort}}, deve-se primeiro converter o texto para sem forma usando ferramentas padrão, como a API International Components for Unicode (ICU) (veja a Classe ArabicShaping em [http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html){: new_window}).

> **Importante:** em alguns casos, a falta da forma de caractere árabe adequada pode fazer com que o conteúdo seja exibido incorretamente no editor de verdade absoluta.

Com relação à forma numérica, o {{site.data.keyword.knowledgestudioshort}} trata a forma numérica como uma propriedade de nível de armazenamento, semelhante a como o conteúdo árabe é manipulado na plataforma iOS. Como um monte de conteúdo árabe é criado em plataformas como Windows, que tratam a forma numérica como uma propriedade de nível de exibição, você precisa converter o conteúdo para tornar a forma numérica uma propriedade de nível de armazenamento ou usar um navegador Firefox quando usar o {{site.data.keyword.knowledgestudioshort}}. O Firefox suporta a capacidade de configurar preferências de forma numérica explicitamente no nível do navegador e cumprir a exibição apropriado para todo o conteúdo mostrado no navegador.

## Procedimento

Para configurar a forma numérica no navegador Firefox:

1. No campo URL do navegador, insira **about:config**. Se um aviso do Firefox for mostrado, clique na ação para desconsiderar o aviso e continuar. Para obter informações sobre como editar as propriedades **about:config**, veja [http://kb.mozillazine.org/About:config_entries ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://kb.mozillazine.org/About:config_entries){: new_window}.
1. Digite `bidi` no campo de filtro de procura.
1. Selecione a propriedade **bidi.numeral**, que controla como os numerais são exibidos, e pressione Enter.
1. Mude o valor dessa propriedade, conforme necessário. Por exemplo, insira `3` e, em seguida, clique em **OK**.

    - **0**: numerais nominais (o valor padrão)
    - **1**: numerais de contexto regular
    - **2**: numerais de contexto hindi
    - **3**: numerais arábicos
    - **4**: numerais hindi

    > **Importante:** quando a propriedade **bidi.numeral** é usada, o Firefox ignora completamente o ponto de código de caracteres de dígito específico no conteúdo de uma página da web.

### Referência relacionada

[Suporte ao idioma](/docs/services/watson-knowledge-studio/language-support.html)
