# Checklist ABNT NBR 17225

Brazilian accessibility standard (adaptation of WCAG 2.1). Published: 2024. Source: Academia de Acessibilidade.
> **Version note:** This reference reflects ABNT NBR 17225:2024. If a newer edition is released, update this file and bump the version in CHANGELOG.md.

**Classificações:**
- **Requisito** = obrigatório (maps to WCAG Level A/AA)
- **Recomendação** = recomendado (maps to WCAG Level AAA or best practice)

> The standard covers 146 checklist items across 16 sections.
> Cumprindo um item de Recomendação, geralmente cumpre-se também o Requisito equivalente de nível inferior.

---

## 1. Interação por Teclado

Algumas pessoas não conseguem utilizar o mouse, ou podem utilizar tecnologia assistiva que não permitem o uso preciso ou total do cursor. É importante que a interface e o conteúdo possam ser navegados e operados utilizando somente o teclado.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.1.1 | Indicador de foco visível | Todos os elementos focáveis possuem um indicador de foco visível. | Requisito |
| 5.1.2 | Elemento em foco totalmente visível | Todos os elementos focáveis estão completamente visíveis quando recebem foco. NOTA: Cumprindo este item, cumpre-se também o item 5.1.3 (Elemento em foco parcialmente visível). | Recomendação |
| 5.1.3 | Elemento em foco parcialmente visível | Todos os elementos focáveis estão pelo menos parcialmente visíveis quando recebem foco, considerando a sobreposição por elementos de autoria do desenvolvedor. | Requisito |
| 5.1.4 | Ordem de foco previsível | Todos os elementos focáveis recebem foco em ordem sequencial lógica e intuitiva, consistente com a apresentação e que preserva o significado e a operabilidade. | Requisito |
| 5.1.5 | Uso de foco | Todos os elementos focáveis são utilizados para interação. | Recomendação |
| 5.1.6 | Armadilha de foco | Não há componentes que bloqueiam, impedem ou interrompem a navegação por teclado. | Requisito |
| 5.1.7 | Conteúdo adicional | Não há conteúdo adicional que seja exibido somente pelo foco do teclado ou posicionamento do cursor. NOTA: Cumprindo este item, cumpre-se também os itens 5.1.8 (Conteúdo adicional persistente) e 5.1.9 (Conteúdo adicional dispensável). | Recomendação |
| 5.1.8 | Conteúdo adicional persistente | Todo conteúdo adicional exibido por foco do teclado ou posicionamento do cursor permanece visível até que a pessoa retire o foco, posicione o cursor fora do componente ou dispense-o de outra forma, ou até que a informação transmitida pelo conteúdo deixe de ser válida. | Requisito |
| 5.1.9 | Conteúdo adicional dispensável | Todo conteúdo adicional exibido por foco do teclado ou posicionamento do cursor pode ser dispensado sem a necessidade de retirar o foco ou reposicionar o cursor; ou o conteúdo adicional exibido comunica um erro de entrada, ou não oculta ou substitui outro conteúdo. | Requisito |
| 5.1.10 | Atalhos de teclado | Não há atalhos de teclado que utilizam uma única tecla, de forma que sempre haja a presença de uma tecla modificadora (como CTRL ou ALT). NOTA: Cumprindo este item, cumpre-se também o item 5.1.11 (Atalhos de teclado sem tecla modificadora). | Recomendação |
| 5.1.11 | Atalhos de teclado sem tecla modificadora | Há um mecanismo simples para desativar ou remapear o atalho de teclado sem tecla modificadora; ou o atalho só é acionado quando um componente específico está em foco. | Requisito |
| 5.1.12 | Acessibilidade por teclado total | Todas as funcionalidades da página são acessíveis com o teclado, sem exceção. NOTA: Cumprindo este item, cumpre-se também o item 5.1.13 (Acessibilidade por teclado parcial). | Recomendação |
| 5.1.13 | Acessibilidade por teclado parcial | Todas as funcionalidades da página que não são acessíveis pelo teclado não admitem modo de operação equivalente utilizando somente o teclado (por exemplo, desenho à mão livre). | Requisito |
| 5.1.14 | Mecanismos de entrada simultâneos | Não há funcionalidade na página que restringe o uso de algum mecanismo de entrada disponível; ou a restrição do uso do mecanismo de entrada específico é essencial, necessária para garantir a segurança do conteúdo ou para respeitar as configurações da pessoa. | Recomendação |
| 5.1.15 | Comportamento de componentes customizados | Todos os componentes customizados possuem comportamento previsível. NOTA: Cumprindo este item, cumpre-se também o item 5.1.16 (Instruções para componentes customizados). | Recomendação |
| 5.1.16 | Instruções para componentes customizados | Todos os componentes customizados que exigem interações complexas e comportamento não previsível possuem instruções para operação. | Requisito |

---

## 2. Imagens

Imagens facilitam a compreensão e tornam o conteúdo mais amigável ao transmitir informações de forma visual. A acessibilidade em imagens garante que todas as pessoas, incluindo aquelas que utilizam tecnologia assistiva, possam perceber, compreender e interagir com o conteúdo visual.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.2.1 | Texto alternativo para imagens de conteúdo | Todas as imagens que transmitem informação ou conteúdo relevante possuem texto alternativo que descreve essa informação ou conteúdo. | Requisito |
| 5.2.2 | Texto alternativo para imagens funcionais | Todas as imagens funcionais possuem texto alternativo que descreve a funcionalidade do elemento. | Requisito |
| 5.2.3 | Texto alternativo para imagens decorativas | Todas as imagens decorativas possuem texto alternativo vazio ou estão implementadas de outra forma, de modo que podem ser ignoradas por tecnologia assistiva. | Requisito |
| 5.2.4 | Descrição para imagens complexas | Todas as imagens complexas possuem texto alternativo que as identifica e têm descrição detalhada disponível na página (próximo à respectiva imagem) ou em outra página indicada. | Requisito |
| 5.2.5 | Imagens de texto | Não há imagens de texto; ou todas as imagens de texto são essenciais e possuem texto alternativo com o mesmo conteúdo; ou é possível customizar as imagens de texto não essenciais e elas possuem texto alternativo com o mesmo conteúdo. | Requisito |
| 5.2.6 | Texto alternativo para mapas de imagens | Todos os mapas de imagens possuem texto alternativo para cada área interativa. | Requisito |

---

## 3. Estrutura de Cabeçalhos

Os níveis de cabeçalho organizam a estrutura, a ordem de importância e a subordinação dos conteúdos da página, facilitando a leitura e a compreensão. Além disso, funcionam como ferramenta de navegação para que as pessoas que usam tecnologia assistiva encontrem facilmente o conteúdo desejado.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.3.1 | Semântica de cabeçalho | Todos os cabeçalhos possuem semântica determinada programaticamente. | Requisito |
| 5.3.2 | Uso de cabeçalhos | Todos os cabeçalhos são utilizados para identificar seções de conteúdo. | Requisito |
| 5.3.3 | Cabeçalho principal | Há um, e somente um, cabeçalho de nível 1, que identifica a página. | Recomendação |
| 5.3.4 | Seções com cabeçalhos | Todas as seções de conteúdo possuem um cabeçalho que as identifica. | Recomendação |
| 5.3.5 | Estrutura de cabeçalhos | Todos os cabeçalhos seguem uma estrutura hierárquica, lógica e semântica. | Requisito |

---

## 4. Regiões / Marcos (Landmarks)

Regiões (marcos) ajudam a comunicar o "layout" e as áreas importantes da página, como a de navegação e a do conteúdo principal. O uso de regiões com marcação semântica correta facilita a compreensão da estrutura da página e permite fácil acesso a essas áreas.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.4.1 | Semântica de região | Todas as regiões da página possuem semântica determinada programaticamente e condizente com a sua função e tipo de conteúdo. | Requisito |
| 5.4.2 | Uso de regiões | Todas as regiões são utilizadas para organizar os conteúdos da página de acordo com o tipo de conteúdo. | Requisito |
| 5.4.3 | Conteúdo em regiões | Todo o conteúdo está contido em regiões. | Recomendação |
| 5.4.4 | Regiões únicas | Não há mais do que uma região do tipo 'header'/'banner', 'main' ou 'footer'/'contentinfo'. | Recomendação |
| 5.4.5 | Regiões identificadas unicamente | Todas as regiões do mesmo tipo possuem um nome acessível único que as identifique. | Requisito |

---

## 5. Listas

Listas permitem a identificação do agrupamento de itens relacionados, apresentados de forma sequencial ou não sequencial. Conteúdos organizados em listas facilitam a compreensão e a navegação.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.5.1 | Semântica de lista | Todas as listas possuem semântica determinada programaticamente e condizente com o tipo de relação entre os itens (ordenada, não ordenada e de definições). | Requisito |
| 5.5.2 | Uso de listas | Todas as listas são utilizadas para agrupamento de itens de mesma natureza. | Requisito |

---

## 6. Tabelas

Tabelas são uma forma estruturada de apresentar dados, que facilita a compreensão das relações entre diferentes tipos de informação. A disposição de dados tabulares em estrutura visual e semanticamente identificada beneficia todas as pessoas.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.6.1 | Semântica de tabela | Todas as tabelas de dados possuem semântica determinada programaticamente. | Requisito |
| 5.6.2 | Uso de tabelas | Todas as tabelas são utilizadas para apresentar dados tabulares. Não há tabelas de "layout"; ou todas as tabelas de "layout" não possuem semântica determinada. | Requisito |
| 5.6.3 | Cabeçalhos de tabela | Todas as células de dados de uma tabela estão associadas com os respectivos cabeçalhos de linha e coluna de forma programaticamente determinada. | Requisito |
| 5.6.4 | Título de tabela | Todas as tabelas possuem um título ou legenda que as identifique. | Recomendação |
| 5.6.5 | Título de tabela associado | Todos os títulos ou legendas de tabela estão associados à respectiva tabela de forma programaticamente determinada. | Requisito |
| 5.6.6 | Descrição para tabelas complexas | Todas as tabelas complexas possuem uma descrição da tabela em texto. | Recomendação |

---

## 7. Links e Navegação

Links permitem que a pessoa navegue entre as páginas e entre os conteúdos de uma mesma página. Os links devem informar claramente o seu destino e devem ser facilmente encontrados na página.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.7.1 | Semântica de link | Todos os links possuem semântica determinada programaticamente. | Requisito |
| 5.7.2 | Uso de links | Todos os links são utilizados para navegação. | Requisito |
| 5.7.3 | Propósito do link sem contexto | Todos os links possuem texto, texto alternativo ou nome acessível que indica sua função ou destino. NOTA: Cumprindo este item, cumpre-se também o item 5.7.4 (Propósito do link no contexto). | Recomendação |
| 5.7.4 | Propósito do link no contexto | Todos os links possuem texto, texto alternativo ou nome acessível que, em conjunto com o contexto do link, informa sua função ou destino. | Requisito |
| 5.7.5 | Links com identificação consistente | Não há links com texto, texto alternativo ou nome acessível iguais que levam para destinos diferentes. | Recomendação |
| 5.7.6 | Links que abrem em nova guia ou janela | Não há links que abrem em nova guia ou janela; ou todos os links que abrem em uma nova guia ou janela informam isso para a pessoa que está usando o sistema. | Recomendação |
| 5.7.7 | Links para arquivos (não HTML) | Todos os links para arquivos incluem no texto ou no texto alternativo a informação do formato e tamanho do arquivo; ou o link para arquivo informa isso para a pessoa de outra forma. | Recomendação |
| 5.7.8 | Links para sites externos | Todos os links para sites externos informam isso para a pessoa que está usando o sistema. | Recomendação |
| 5.7.9 | Texto complementar do link | Não há texto complementar que repete o texto, texto alternativo ou nome acessível do link. | Recomendação |
| 5.7.10 | Links adjacentes | Não há links adjacentes que levam para o mesmo destino. | Recomendação |
| 5.7.11 | Contornar blocos de conteúdo | Há um ou mais links (ou outro mecanismo) que permitem contornar blocos de conteúdo na página. | Recomendação |
| 5.7.12 | Contornar blocos em conjunto de páginas | Há links (ou mecanismos) que permitem contornar blocos que se repetem em um conjunto de páginas. | Requisito |
| 5.7.13 | Alternativas para localização | Há mais de uma forma para encontrar uma página em um conjunto de páginas; ou a página é o resultado ou uma etapa de um processo. | Requisito |
| 5.7.14 | Localização em conjunto de páginas | Há informação sobre a localização da pessoa que usa o sistema em relação às demais páginas ou seções do site. | Recomendação |
| 5.7.15 | Navegação consistente | Todos os mecanismos de navegação que se repetem em um conjunto de páginas estão na mesma ordem relativa; ou a posição do mecanismo é alterada pela pessoa que usa o sistema. | Requisito |
| 5.7.16 | Ajuda consistente | Todos os mecanismos de ajuda que se repetem em um conjunto de páginas estão na mesma ordem relativa; ou a posição do mecanismo é alterada pela pessoa que usa o sistema. | Requisito |

---

## 8. Botões e Controles

Elementos interativos, como links e botões, permitem que a pessoa que usa o sistema navegue para um destino ou execute uma ação, respectivamente. É importante que todos os elementos interativos sejam perceptíveis, compreensíveis e passíveis de acionamento para todas as pessoas.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.8.1 | Semântica de botão | Todos os botões possuem semântica determinada programaticamente. | Requisito |
| 5.8.2 | Uso de botões | Todos os botões são utilizados para acionar uma funcionalidade. | Requisito |
| 5.8.3 | Propósito do botão | Todos os botões possuem texto, texto alternativo ou nome acessível que indica sua função. | Requisito |
| 5.8.4 | Identificação consistente na página | Todos os componentes que possuem a mesma funcionalidade e se repetem na página são identificados de maneira consistente. | Recomendação |
| 5.8.5 | Identificação consistente em conjunto de páginas | Todos os componentes que possuem a mesma funcionalidade e se repetem em um conjunto de páginas são identificados de maneira consistente. | Requisito |
| 5.8.6 | Área de acionamento (aprimorada) | Todos os elementos interativos têm área de acionamento de pelo menos 44 pixels CSS de altura e largura; ou existe um controle equivalente na mesma página com pelo menos 44px; ou o elemento está em uma sentença ou bloco de texto; ou o tamanho é determinado pelo agente de usuário; ou o tamanho é essencial para transmitir a informação. NOTA: Cumprindo este item, cumpre-se também o item 5.8.7 (Área de acionamento (mínima)). | Recomendação |
| 5.8.7 | Área de acionamento (mínima) | Todos os elementos interativos têm área de acionamento de pelo menos 24 pixels CSS de altura e largura; ou o elemento tem espaçamento de modo que a soma do tamanho mais o espaçamento é de pelo menos 24px em todas as direções; ou existe controle equivalente com pelo menos 24px; ou o elemento está em sentença ou bloco de texto; ou o tamanho é determinado pelo agente de usuário; ou o tamanho é essencial ou legalmente exigido. | Requisito |
| 5.8.8 | Mudança de contexto previsível | Toda mudança de contexto é iniciada apenas a pedido da pessoa que usa o sistema; ou há um mecanismo para desativar essas mudanças de contexto. | Recomendação |
| 5.8.9 | Mudança de contexto previsível no foco | Não há componentes acionados somente pelo foco do teclado ou posicionamento do cursor que provocam uma mudança de contexto. | Requisito |
| 5.8.10 | Mudança de contexto previsível na entrada | Não há componentes que provocam mudança de contexto enquanto a pessoa insere ou seleciona informações; ou a pessoa que usa o sistema é avisada sobre esse comportamento antes de utilizar o componente. | Requisito |
| 5.8.11 | Acionamento por ponteiro único | Não há funcionalidade operada por ponteiro único que é acionada pelo pressionamento do ponteiro (down-event); ou o acionamento completo só é finalizado ao soltar o ponteiro (up-event), e existe mecanismo para interromper ou desfazer; ou soltar o ponteiro reverte o acionamento do pressionamento; ou o acionamento pelo pressionamento é essencial. | Requisito |
| 5.8.12 | Operação por gestos de ponteiro | Toda funcionalidade operada por gestos multiponto ou baseados em caminhos pode ser operada também por um ponteiro único sem gesto baseado em caminho; ou o gesto multiponto ou baseado em caminho é essencial; ou a funcionalidade é determinada pelo agente de usuário e não modificada pelo desenvolvedor. | Requisito |
| 5.8.13 | Operação por movimento de arrastar | Toda funcionalidade operada por movimento de arrastar pode ser operada também por um ponteiro único sem movimento de arrastar; ou o movimento de arrastar é essencial; ou a funcionalidade é determinada pelo agente de usuário e não modificada pelo desenvolvedor. | Requisito |
| 5.8.14 | Operação por movimento | Toda funcionalidade operada por movimento pode ser operada também por componentes que não exigem esse modo de operação, e a resposta aos movimentos pode ser desabilitada para evitar acionamento acidental; ou existe um mecanismo para operar o controle de movimento de outra forma; ou o movimento é essencial para a funcionalidade, e desabilitá-lo invalidaria a atividade. | Requisito |
| 5.8.15 | Controles com retorno | Todos os controles têm um retorno (feedback) perceptível à pessoa que usa o sistema quando são acionados. | Recomendação |

---

## 9. Formulários e Entrada de Dados

Formulários permitem que as pessoas insiram e enviem informações, e são essenciais para funcionalidades como envio de mensagens, realização de pedidos e cadastros. Instruções claras para inserir e corrigir informações possibilitam que as pessoas preencham dados de forma correta e eficiente.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.9.1 | Rótulo de campo | Todos os campos de formulário possuem um rótulo que os identifica; ou o campo de formulário possui propósito visualmente evidente e um nome acessível que o identifica. | Requisito |
| 5.9.2 | Rótulo de campo previsível | Todos os rótulos estão posicionados de maneira previsível em relação aos respectivos campos de formulário. | Requisito |
| 5.9.3 | Rótulo de campo associado | Todos os rótulos estão associados aos respectivos campos de formulário de forma programaticamente determinada. | Requisito |
| 5.9.4 | Rótulo de campo descritivo | Todos os rótulos identificam o propósito do respectivo campo de formulário; ou o rótulo, em conjunto com o agrupamento do campo, identifica o propósito do respectivo campo de formulário. | Requisito |
| 5.9.5 | Textos de ajuda previsíveis | Todos os textos de ajuda estão posicionados de maneira previsível em relação aos campos do formulário. | Requisito |
| 5.9.6 | Campos relacionados | Todos os campos de entrada relacionados possuem agrupamento determinado programaticamente. | Requisito |
| 5.9.7 | Campos obrigatórios | Todos os campos obrigatórios estão devidamente identificados, de forma que todos possam perceber. | Requisito |
| 5.9.8 | Tipo de dado determinado | Todos os campos de entrada têm seu tipo de dado determinado programaticamente. | Requisito |
| 5.9.9 | Mensagem de erro descritiva | Todas as mensagens de erro descrevem em texto qual é o erro e identificam qual é o campo com erro. | Requisito |
| 5.9.10 | Sugestão de correção | Todas as mensagens de erro fornecem sugestões de correção de entrada de dados, quando conhecidas; ou a sugestão de correção coloca em risco a segurança ou o propósito do conteúdo. | Recomendação |
| 5.9.11 | Prevenção de erro | Todos os formulários permitem uma forma de reverter, verificar ou confirmar os dados. NOTA: Cumprindo este item, cumpre-se também o item 5.9.12 (Prevenção de erro para formulários críticos). | Requisito |
| 5.9.12 | Prevenção de erro para formulários críticos | Todos os formulários críticos permitem uma forma de reverter, verificar ou confirmar os dados. | Requisito |
| 5.9.13 | Ajuda contextual | Há ajuda contextual, como instruções e dicas relevantes, que auxilia a pessoa que usa o sistema a preencher e enviar os formulários. | Recomendação |
| 5.9.14 | Botão de submissão | Todos os formulários possuem um botão para a submissão dos dados. | Recomendação |
| 5.9.15 | Reentrada de dados | Todos os campos de entrada que exigem dados previamente inseridos são preenchidos automaticamente ou estão disponíveis para seleção; ou a reentrada de dados é essencial; ou a informação inserida é necessária por segurança; ou a informação previamente inserida não é mais válida. | Requisito |
| 5.9.16 | Validação sensorial ou por movimento | Todo método de validação que exige uma percepção ou capacidade motora específica possui uma alternativa que não possui a mesma exigência. Equivalente a WCAG 2.2 — 3.3.8 Accessible Authentication (Minimum), Level AA. | Requisito |
| 5.9.17 | Autenticação acessível (aprimorada) | Não há testes de função cognitiva em processos de autenticação; ou há um método de autenticação alternativo sem teste de função cognitiva; ou há um mecanismo para auxiliar a pessoa a completar o teste de função cognitiva. NOTA: Cumprindo este item, cumpre-se também o item 5.9.18 (Autenticação acessível (mínima)). | Recomendação |
| 5.9.18 | Autenticação acessível (mínima) | Não há testes de função cognitiva em processos de autenticação; ou há um método alternativo sem teste de função cognitiva; ou há um mecanismo de auxílio para completar o teste; ou o teste é um método de reconhecimento de objetos; ou o teste serve para identificar um conteúdo não textual fornecido pela pessoa que usa o sistema. | Requisito |

---

## 10. Apresentação

O conteúdo de uma página pode ser apresentado de diversas formas, incluindo variações de cores, fontes, "layouts", imagens e outras características sensoriais. A acessibilidade na estética e no design visual, de acordo com boas práticas, permite a percepção, compreensão e interação com o conteúdo para todas as pessoas.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.10.1 | Características sensoriais | Não há instruções para compreender e utilizar o conteúdo que dependem somente das características sensoriais dos componentes, como forma, cor, tamanho, localização visual, orientação e som. | Requisito |
| 5.10.2 | Ordem de apresentação | A apresentação dos elementos conforme aparecem na tela é tal que preserva o significado e a operabilidade. | Requisito |
| 5.10.3 | Orientação de exibição | O conteúdo não restringe sua visualização e operação a uma única orientação de exibição, como de retrato ou paisagem; ou a orientação específica de exibição é essencial. | Requisito |
| 5.10.4 | Design responsivo | Não há perda de informação ou funcionalidade, nem barra de rolagem em duas dimensões para conteúdo de rolagem horizontal apresentado com altura equivalente a 256 pixels CSS; ou para conteúdo de rolagem vertical apresentado com largura equivalente a 320 pixels CSS; ou o conteúdo exige layout bidimensional para uso ou significado (por exemplo, mapas, diagramas, vídeos, jogos, apresentações, tabelas de dados e interfaces). | Requisito |
| 5.10.5 | Área do indicador de foco visível | O indicador de foco visível dos elementos focáveis tem área pelo menos equivalente ao perímetro do elemento com 2 pixels CSS de espessura. | Recomendação |

---

## 11. Uso de Cores

A cor é um recurso importante no design de conteúdo da web. A acessibilidade no uso de cores permite que pessoas que não podem ver ou perceber as cores também consigam compreender e utilizar o conteúdo.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.11.1 | Uso de cores | Não há elementos que fazem uso somente de cores para transmitir informações, indicar uma ação, pedir uma resposta ou distinguir um elemento visual. | Requisito |
| 5.11.2 | Contraste para texto (aprimorado) | Todo conteúdo de texto, incluindo imagens de texto, tem relação de contraste de pelo menos 7:1 com o fundo; ou o conteúdo de texto está em tamanho grande e tem relação de contraste de pelo menos 4.5:1 com o fundo; ou o texto faz parte de um logotipo ou está em plano secundário. NOTA: Cumprindo este item, cumpre-se também o item 5.11.3 (Contraste para texto (mínimo)). | Recomendação |
| 5.11.3 | Contraste para texto (mínimo) | Todo conteúdo de texto, incluindo imagens de texto, tem relação de contraste de pelo menos 4.5:1 com o fundo; ou o conteúdo de texto está em tamanho grande e tem relação de contraste de pelo menos 3:1 com o fundo; ou o texto faz parte de um logotipo ou está em plano secundário. | Requisito |
| 5.11.4 | Contraste para componentes | Todos os componentes de interface têm relação de contraste de pelo menos 3:1 com o fundo e entre seus estados; ou o componente está em estado inativo. | Requisito |
| 5.11.5 | Contraste para objetos gráficos | Todas as partes de objetos gráficos necessárias para compreender o conteúdo têm relação de contraste de pelo menos 3:1 com o fundo e entre si; ou a apresentação específica dos objetos gráficos é essencial para a informação transmitida. | Requisito |
| 5.11.6 | Contraste para indicador de foco visível | O indicador de foco visível dos elementos focáveis tem relação de contraste de pelo menos 3:1 com o fundo e entre os estados em foco e sem foco. | Requisito |

---

## 12. Conteúdo Textual

Conteúdo em texto é essencial para apresentar informações na web. Textos escritos, estruturados e marcados de forma acessível, e que permitem a formatação mais adequada para cada pessoa que usa o sistema, são mais fáceis de ler e de serem compreendidos por todas as pessoas.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.12.1 | Espaçamento entre as linhas | Todos os blocos de texto têm espaçamento entre as linhas (entrelinhas) de pelo menos 1,5 vez o tamanho da fonte; ou existe um mecanismo para configurar o espaçamento e não há perda de conteúdo ou funcionalidade quando o critério acima é cumprido. | Requisito |
| 5.12.2 | Espaçamento entre os parágrafos | Todos os parágrafos têm espaçamento entre si de pelo menos 2 vezes o tamanho da fonte; ou existe um mecanismo para configurar o espaçamento e não há perda de conteúdo ou funcionalidade quando o critério acima é cumprido. | Requisito |
| 5.12.3 | Espaçamento entre as letras | Todos os blocos de texto têm espaçamento entre as letras (rastreamento) de pelo menos 0,12 vez o tamanho da fonte; ou existe um mecanismo para configurar o espaçamento e não há perda de conteúdo ou funcionalidade quando o critério acima é cumprido. | Requisito |
| 5.12.4 | Espaçamento entre as palavras | Todos os blocos de texto têm espaçamento entre as palavras de pelo menos 0,16 vez o tamanho da fonte; ou existe um mecanismo para configurar o espaçamento e não há perda de conteúdo ou funcionalidade quando o critério acima é cumprido. | Requisito |
| 5.12.5 | Alinhamento de blocos de texto | Todos os blocos de texto estão alinhados à esquerda para idiomas lidos da esquerda para a direita; e todos os blocos de texto estão alinhados à direita para idiomas lidos da direita para a esquerda; ou o alinhamento é essencial para a compreensão do conteúdo. | Recomendação |
| 5.12.6 | Largura de blocos de texto | A largura dos blocos de texto não ultrapassa 80 caracteres (40 caracteres, se o idioma for chinês, japonês ou coreano); ou existe um mecanismo para configurar a largura dos blocos de texto e alcançar esse resultado. | Requisito |
| 5.12.7 | Texto redimensionado | Não há perda de conteúdo ou funcionalidade quando o texto é redimensionado sem o uso de recursos de tecnologia assistiva em até 200%, de modo que a pessoa que usa o sistema não precisa rolar horizontalmente para ler uma linha de texto em uma janela de tela inteira. | Requisito |
| 5.12.8 | Semântica de texto especial | Todos os trechos de texto de ênfase, citação, abreviação ou outro tipo de texto especial possuem semântica determinada programaticamente. | Requisito |
| 5.12.9 | Uso de texto especial | Todos os trechos de texto de ênfase, citação, abreviação ou texto especial são utilizados para transmitir esses propósitos. | Requisito |
| 5.12.10 | Definições de significado | Há um mecanismo para identificar definições específicas de palavras ou frases usadas de forma incomum ou restrita, incluindo expressões idiomáticas e jargões. | Recomendação |
| 5.12.11 | Siglas e abreviaturas | Há um mecanismo para identificar a forma expandida ou o significado das siglas e abreviaturas. | Recomendação |
| 5.12.12 | Nível de linguagem | Todo conteúdo de texto utiliza linguagem simples e clara; ou existe conteúdo suplementar ou uma versão alternativa simplificada para linguagem especializada ou recursos linguísticos complexos. | Recomendação |
| 5.12.13 | Pronúncia identificada | Há um mecanismo para identificar a pronúncia específica de palavras cujo significado no contexto é ambíguo sem se conhecer a pronúncia. | Recomendação |

---

## 13. Codificação e Marcação Semântica

Conjunto de códigos que determina o comportamento e a funcionalidade de todo o site ou aplicação web. Um código com boa qualidade é robusto, o que o torna compatível com uma ampla gama de agentes de usuário (user agents), como navegadores e tecnologias assistivas.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.13.1 | Título da página | A página possui um título único em relação às demais páginas do site, que a identifica. | Requisito |
| 5.13.2 | Idioma da página | A página tem seu idioma declarado de forma programaticamente determinada. | Requisito |
| 5.13.3 | Idioma das partes da página | Todas as partes da página que possuem idioma diferente do principal têm seu idioma declarado de forma programaticamente determinada; ou o texto é um nome próprio, um termo técnico, uma palavra em um idioma indeterminado, ou uma palavra ou frase estrangeira que se tornou parte do vernáculo do texto que a envolve. | Requisito |
| 5.13.4 | Título do frame | Todo frame ou iframe possui um título único, que o identifica. | Requisito |
| 5.13.5 | Zoom não bloqueado | A página não bloqueia o recurso de zoom do agente de usuário (user agent). | Requisito |
| 5.13.6 | Ordem de leitura | A ordem dos elementos conforme aparecem no código é lógica e intuitiva, de modo que preserva o significado e a operabilidade. | Requisito |
| 5.13.7 | Texto visível no nome acessível | Todos os componentes possuem nome acessível igual ao texto visível do componente ou do seu rótulo; ou o nome acessível contém o texto visível, preferencialmente no início. | Requisito |
| 5.13.8 | Mensagens de status | Todas as mensagens de status são determinadas programaticamente, de modo que não seja necessário que as pessoas que usam tecnologia assistiva tenham que dar foco no elemento. | Requisito |
| 5.13.9 | Propósito identificável | A finalidade dos componentes da interface do usuário (UI), ícones e regiões pode ser determinada programaticamente. | Recomendação |
| 5.13.10 | Componentes com nome acessível | Todos os componentes que requerem identificação por nome possuem um nome acessível. | Requisito |
| 5.13.11 | Elementos nativos | Todos os componentes da página utilizam elementos nativos. NOTA: Cumprindo este item, cumpre-se também os itens 5.13.12 (Semântica de componentes customizados) e 5.13.13 (Estados, propriedades e valores de componentes customizados). | Requisito |
| 5.13.12 | Semântica de componentes customizados | Todos os componentes customizados possuem semântica, incluindo função, estados, propriedades e valores, determinada programaticamente, incluindo as alterações desses itens. | Requisito |
| 5.13.13 | Estados, propriedades e valores de componentes customizados | Todos os componentes de interface de usuário (UI), cujos estados, propriedades e valores possam ser definidos pela pessoa que usa o sistema, permitem que esses atributos sejam definidos programaticamente. | Requisito |

---

## 14. Áudio e Vídeo

Conteúdo multimídia, incluindo áudio e vídeo ao vivo ou pré-gravado, é um dos tipos de recursos para a web. Todos podem perceber e interagir com esse tipo de conteúdo se forem oferecidas alternativas equivalentes.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.14.1 | Alternativa em texto para áudio | Todo áudio pré-gravado tem uma alternativa em texto que transcreve todo o seu conteúdo; ou o áudio é uma alternativa para um vídeo sem áudio ou texto equivalente e está claramente identificado como tal. | Requisito |
| 5.14.2 | Legendas descritivas para vídeo | Todo vídeo com áudio pré-gravado tem legendas descritivas disponíveis e equivalentes ao conteúdo do áudio; ou o vídeo é uma alternativa para um texto equivalente e está claramente identificado como tal. | Requisito |
| 5.14.3 | Transcrição para vídeo | Todo conteúdo em vídeo pré-gravado tem uma alternativa em texto que transcreve todo o seu conteúdo, visual e sonoro. | Recomendação |
| 5.14.4 | Audiodescrição para vídeo | Todos os vídeos pré-gravados têm audiodescrição para todo o conteúdo visual; ou o áudio original é suficiente para a compreensão do conteúdo do vídeo sem o uso da visão. | Requisito |
| 5.14.5 | Audiodescrição estendida para vídeo | Todo conteúdo em vídeo pré-gravado, cujas pausas não sejam suficientes para audiodescrição, tem uma versão com audiodescrição estendida para todo o vídeo. | Recomendação |
| 5.14.6 | Janela de Libras para conteúdo em áudio | Janela de Libras está disponível em todo o conteúdo de áudio pré-gravado em mídia sincronizada. | Recomendação |
| 5.14.7 | Controle de áudio | Não há áudio que toque automaticamente e dure mais que 3s; ou existe um mecanismo para pausar, parar, silenciar ou ajustar o seu volume sem afetar o volume geral do sistema. | Requisito |
| 5.14.8 | Áudio sem ruído | Não há conteúdo em áudio que possua sons de fundo; ou não há conteúdo em áudio focado principalmente na fala com sons de fundo que possam distrair ou interferir na compreensão; ou o áudio é uma vocalização com intenção de expressão musical ou parte de um CAPTCHA; ou há um mecanismo para desligar os sons de fundo; ou os sons de fundo têm volume que não interferem no som principal. | Recomendação |
| 5.14.9 | Legendas para áudio e vídeo ao vivo | Todo conteúdo em áudio ou áudio e vídeo ao vivo tem legendas disponíveis. | Requisito |
| 5.14.10 | Transcrição para áudio ao vivo | Existe uma transcrição para todo o conteúdo em áudio ao vivo. | Recomendação |

---

## 15. Animação

Conteúdos que se movem, piscam ou rolam, que mudam de estado de modo que transmitem uma sensação de movimento, sejam autonomamente ou em resposta a uma ação da pessoa que usa o sistema. Animações podem gerar barreiras ou distrações para pessoas que têm dificuldade para acompanhar o movimento ou que possuem deficit de atenção.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.15.1 | Controle de animação | Não há animação que inicie automaticamente, dure mais que 5s e seja apresentada em paralelo com outro conteúdo; ou existe um mecanismo para pausar, parar ou ocultar a animação; ou a animação é essencial para a atividade. | Requisito |
| 5.15.2 | Animações acionadas por interação | Não há animações de movimento acionadas pela interação da pessoa que usa o sistema; ou existe um mecanismo para desativar as animações de movimento acionadas pela interação da pessoa que usa o sistema; ou a animação de movimento é essencial para a funcionalidade ou informação transmitida. | Recomendação |
| 5.15.3 | Flash intermitente | Não há conteúdo que pisque mais de três vezes em qualquer período de 1s. NOTA: Cumprindo este item, cumpre-se também o item 5.15.4 (Flash intermitente limitado). | Recomendação |
| 5.15.4 | Flash intermitente limitado | Todo conteúdo Flash que pisca está abaixo dos limites de flash geral e flash vermelho. | Requisito |

---

## 16. Tempo

Algumas atividades na web exigem limites de tempo para a sua realização. Esses limites devem considerar pessoas que necessitam de mais tempo para ler ou completar tarefas.

| Nº | Item | Como cumprir | Classificação |
|---|---|---|---|
| 5.16.1 | Limite de tempo | Não há evento ou atividade no conteúdo com limite de tempo; ou o limite de tempo não é parte essencial do evento ou da atividade; ou o conteúdo é uma mídia sincronizada não interativa ou um evento em tempo real. NOTA: Cumprindo este item, cumpre-se também o item 5.16.2 (Limite de tempo ajustável). | Recomendação |
| 5.16.2 | Limite de tempo ajustável | Há um mecanismo para desligar, ajustar ou estender o limite de tempo antes de atingi-lo; ou o limite de tempo é intrínseco ao conteúdo, essencial ou superior a 20h. | Requisito |
| 5.16.3 | Controle de atualização | Não há atualização que inicie automaticamente e seja apresentada em paralelo com outro conteúdo; ou existe um mecanismo para pausar, parar ou ocultar a atualização, ou para controlar a frequência da atualização; ou a atualização é essencial para a atividade. | Requisito |
| 5.16.4 | Interrupções | Não há interrupções; ou existe um mecanismo para adiar ou bloquear as interrupções; ou as interrupções envolvem uma emergência. | Recomendação |
| 5.16.5 | Reautenticação | Não há perda de dados quando uma sessão autenticada expira. A pessoa que usa o sistema pode continuar a atividade sem perda de dados após a nova autenticação; ou a perda de dados é essencial. | Recomendação |
| 5.16.6 | Tempo de inatividade | Não há perda de dados quando um limite de tempo de inatividade da pessoa que usa o sistema é atingido; ou há um aviso sobre o limite de tempo de inatividade da pessoa que usa o sistema antes da perda de dados; ou o limite de tempo de inatividade da pessoa que usa o sistema sem perda de dados é de pelo menos 20h. | Recomendação |
