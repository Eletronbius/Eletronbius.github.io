+++
authors = ["Davi Almeida"]
title = "Front-End Fatec Itaquera"
description = "Projeto em que trabalhei como desenvolvedor Front-End estagiário"
date = 2026-06-29
[taxonomies]
tags = ["Front-End", "SPA", "JavaScript", "Performance", "Estágio", "SDLC"]
+++

# Situação

Este projeto foi proposto com a ideia de modernizar o site da instituição. O site antigo estava desatualizado, e novas informações eram jogadas nele sem qualquer organização ou arquitetura de informação. Isso fez com que algumas informações fossem difíceis de encontrar, ficassem perdidas ou fossem colocadas em seções em que não deveriam estar. Além disso, algumas páginas do site estavam quebradas e exibindo o conteúdo de páginas completamente diferentes, vários componentes não estavam funcionando como deveriam, e a barra de navegação estava quebrada.

Esses são alguns, mas não todos, os problemas que o site estava sofrendo. Foi então que surgiu a ideia de iniciar um projeto na instituição em que estudantes desenvolveriam um site novo e moderno.


# Tarefa

Nos foi dada a **tarefa** de modernizar o site. Mas ***como?***

### Stack Tecnológica

Você pode se perguntar quais tecnologias este projeto usou. Nossa maior restrição era que tínhamos que desenvolver tudo do zero sem usar bibliotecas ou frameworks. Uma das razões para essa restrição era a ideia de que futuros estudantes poderiam ajudar a adicionar recursos e realizar manutenção, <span class="spoiler">o que era uma boa ideia, mas não aconteceu</span>. Portanto, a tecnologia utilizada foi HTML, CSS e JavaScript puros.

Para armazenamento, no começo não usaríamos nenhum tipo de banco de dados porque ele seria desenvolvido em um projeto futuro específico para desenvolvimento back-end, que você pode ler mais sobre [aqui](@/Projects/Back-End%20Fatec%20Itaquera/index.md). Então, tenha isso em mente ao ler este texto.

# Ação

Dada a tarefa, nossas restrições e razões. Qual foi a abordagem para **resolver o problema?**

À medida que analisamos o site e desenhamos a arquitetura de informação que consideramos mais útil, desenvolvemos nosso primeiro protótipo e definimos como a barra de navegação ficaria (pelo menos como organizaríamos a informação).

<figure>
{{ image(url="firstprototype.PNG", alt="Este é um exemplo de imagem") }}
  <figcaption>Como era a página inicial do nosso primeiro protótipo</figcaption>
</figure>

Depois que terminamos o protótipo e obtivemos a aprovação de todas as partes interessadas, começamos a fase de implementação do nosso <abbr title="Software Development Life Cycle"> SDLC </abbr>.

## Um novo problema surgiu!

Como resultado da nossa análise, percebemos que seria irracional criar um único HTML e CSS para cada página deste projeto, porque facilmente teríamos mais de 20 pares de arquivos para gerenciar com uma equipe de 3 pessoas. Então, conversamos com nosso supervisor da época para discutir novas ideias de abordagem e ele sugeriu que usássemos um framework de <abbr title="Single-Page Application"> SPA </abbr> para desenvolver o site.

Alguns dos principais pontos positivos dessa abordagem são que poderíamos ter uma aplicação rápida e que poderia funcionar offline por meio do uso de cache local; alguns dos principais pontos negativos seriam um carregamento inicial mais lento e a possível complexidade de gerenciar estado e memória, já que tudo seria gerenciado dinamicamente. Equilibrando prós e contras, decidimos desenvolver um framework de <abbr title="Single-Page Application"> SPA </abbr>. Com isso, o problema foi **resolvido!**

## Meu papel no projeto

Enquanto meus colegas trabalhavam na estilização e na coleta de informações do site antigo, meu papel no projeto era desenvolver as funções centrais do framework, garantindo que ele fosse performático e pudesse funcionar sem problemas.

A solução foi baseada no evento [hashchange](https://developer.mozilla.org/en-US/docs/Web/API/Window/hashchange_event) do navegador, que funciona melhor do que detectar [urlChange](https://developer.mozilla.org/en-US/docs/Web/API/Navigation/navigate_event). Portanto, a navegação era baseada em hashchange: quando o usuário clica para navegar para outra página, o navegador apenas altera o hash, e isso é detectado pelo framework, que então muda o conteúdo.

<figure>
{{ image(url="example.png", alt="representação visual") }}
  <figcaption>Uma representação visual de como seria</figcaption>
</figure>

Para ficar mais claro, apenas o conteúdo (área verde) é a área em que o conteúdo será substituído; as áreas laranjas são fixas e não mudam conforme o usuário navega pelo site.

Agora que você já entendeu a solução e espero ter me feito entender, mas agora **como e onde eu armazenaria essa informação?** Simples! Usando <abbr title="JavaScript Object Notation">JSON</abbr>!

### Gerenciamento de armazenamento e tratamento de mudanças dinâmicas

O conteúdo das páginas era armazenado em arquivos JSON, sendo que cada JSON representava uma única página. Quando o hashchange era detectado, o framework buscava o JSON e o passava para o objeto Page, que continha todas as informações do JSON e também construía e retornava o conteúdo HTML da página para substituir o anterior e exibi-lo ao usuário. Pense nisso como um tipo de [Factory Pattern](https://refactoring.guru/design-patterns/factory-method). Depois que o objeto Page era inicializado, ele mantinha o conteúdo HTML em cache internamente para navegação mais performática caso o usuário decidisse retornar àquela página, e o JSON era armazenado em cache no localStorage.

Com essa estratégia, a principal preocupação dessa abordagem era, como já mencionado, que a primeira carga de todos os arquivos JSON demorasse mais.

# Resultado

TL;DR

Se você é nerd de <abbr title="Core Web Vitals">CWV</abbr>, melhoramos todas essas métricas em grande medida, como você pode ver abaixo nas imagens.
Mais estatísticas para os nerds:
- `Tempo de carregamento` caiu 31% mesmo no primeiro carregamento do site antes do conteúdo ser armazenado em cache
- `Navegação entre páginas` com o uso das técnicas mencionadas acima, a navegação ficou, em média e na maioria dos casos, abaixo de 100ms
- `Speed Index` aumentou 47%, o que melhora a experiência do usuário e leva a melhores taxas de rejeição (bounce rate)
- <span class="spoiler solid">devido à má documentação dos testes de desempenho, essa é a informação que consegui registrar, mas testei exaustivamente o desempenho</span>

Bem, diante de todas as restrições e desafios, o projeto foi um sucesso e foi implementado com sucesso como a nova versão do site (<span class="spoiler solid">infelizmente, devido à falta de mantenedores para o projeto, o site acabou sendo substituído por um template simples novamente</span>). Conseguimos resultados muito melhores do que esperávamos; aqui estão alguns deles:

### Core Web Vitals

<abbr title="Core Web Vitals">CWV</abbr> foi uma das métricas usadas para medir desempenho:

### Antes
<figure>
{{ image(url="CWVold.png", alt="site antigo", no_hover=true) }}
  <figcaption>CWV do site antigo</figcaption>
</figure>

### Depois
<figure>
{{ image(url="CWVnew.png", alt="site novo", no_hover=true) }}
  <figcaption>CWV do novo site</figcaption>
</figure>

Não vou detalhar cada uma dessas métricas neste artigo porque não acho que, neste ponto, você seja alguém que nunca ouviu falar sobre elas. Mas, se você não estiver familiarizado com <abbr title="Core Web Vitals">CWV</abbr>, não se preocupe: aqui estão os links que você precisa se estiver interessado em entender o que essas métricas significam:

- [First Contentful Paint (FCP)](https://web.dev/articles/fcp)

- [Total Blocking Time (TBT)](https://web.dev/articles/tbt)

- [Speed Index (SI)](https://developer.chrome.com/docs/lighthouse/performance/speed-index)

- [Largest Contentful Paint (LCP)](https://web.dev/articles/lcp)

- [Cumulative Layout Shift (CLS)](https://web.dev/articles/cls)

### Visão geral

Devido à má documentação, muitos dos resultados dos testes não foram registrados corretamente e acabaram sendo perdidos no momento em que escrevo este artigo. Os resultados documentados eram basicamente sobre tempo de navegação e tempo de carregamento, que mencionei no parágrafo TL;DR.

Se você tiver alguma dúvida sobre este projeto ou qualquer feedback sobre este artigo, sinta-se à vontade para falar comigo no [LinkedIn](https://www.linkedin.com/in/davialp/).