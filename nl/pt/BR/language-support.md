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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/knowledge-studio/language-support.html){: new_window}.
{: tip}

# Suporte ao idioma
{: #language-support}

O {{site.data.keyword.knowledgestudiofull}} fornece suporte para treinar um modelo em várias linguagens.

O suporte para múltiplas linguagens não significa que o produto propriamente dito seja traduzido. As interfaces com o usuário, mensagens e documentação do {{site.data.keyword.knowledgestudioshort}} estão disponíveis somente em inglês.
{: shortdesc}

É possível treinar um modelo nas linguagens a seguir:

- Inglês (a linguagem padrão)
- Árabe
- Português do Brasil
- Chinês (Simplificado)
- Holandês
- Francês
- Alemão
- Italiano
- Japonês
- Coreano
- Espanhol

O suporte inclui a capacidade de incluir documentos nessas linguagens em uma área de trabalho, incluir dicionários, executar pré-anotação, usar o editor de verdade absoluta para anotar documentos e treinar um modelo de aprendizado de máquina. Quando você seleciona uma linguagem, o sistema aplica modelos específicos da linguagem para manipular entradas de dicionário, tokenização de texto e segmentação de sentença. Para obter informações sobre como o sistema manipula dicionários em diferentes linguagens, veja [Dicionários](/docs/services/watson-knowledge-studio/dictionaries.html#wks_dictionaries).

> **Nota:** o editor de regras e o modelo baseado em regra não podem manipular texto bidirecional, portanto não podem ser usados com documentos em árabe.

> **Restrições:**
>
> Devido a restrições de caracteres na tecnologia de aprendizado de máquina subjacente, as entradas no sistema de tipos não podem conter espaços e podem incluir somente os caracteres ASCII a seguir:
>
> - A-Z e a-z
> - 0-9
> - O caractere de sublinhado: _
>
> As regras a seguir também se aplicam:
>
> - O primeiro caractere no nome deve ser alfabético.
> - O comprimento do nome do tipo de entidade não pode exceder 64 caracteres.
> - O comprimento do nome do tipo de relação não pode exceder 128 caracteres.
>
> Assim, por exemplo, quando um anotador humano anotar texto em japonês no editor de verdade absoluta, os nomes de tipo de entidade e tipo de relação que puderem ser aplicados não serão em japonês.

### Tarefas relacionadas

[Configurando o suporte para árabe](/docs/services/watson-knowledge-studio/language-support-arabic.html)
