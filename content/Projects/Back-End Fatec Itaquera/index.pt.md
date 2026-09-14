+++
authors = ["Davi Almeida"]
title = "Back-End Fatec Itaquera"
description = "Project Where I worked as Back-End Intern Developer"
date = 2026-06-29
[taxonomies]
tags = ["Back-End", "PHP", "Microserviços","MySQL","Estágio","SDLC"]
+++

# Situação

Este projeto começa depois [deste](@/Projects/Front-End%20Fatec%20Itaquera/index.md) projeto; portanto, para mais informações, consulte a seção Situação daquele projeto.

Este projeto foi planejado para uma equipe maior, cuja abordagem seria desenvolver o serviço de back-end para gerenciar o conteúdo do [front-end](@/Projects/Front-End%20Fatec%20Itaquera/index.md).

Com uma equipe maior, a dinâmica seria diferente: fomos orientados a trabalhar no estilo de programação em pares, com cada dupla responsável por um microsserviço do site.

# Tarefa

Como mencionado anteriormente, este projeto é uma espécie de sequência de outro [projeto](@/Projects/Front-End%20Fatec%20Itaquera/index.md) em que trabalhei.

A tarefa era criar um serviço de back-end para gerenciar o conteúdo do front-end, essencialmente um painel administrativo onde professores e funcionários pudessem interagir com o conteúdo do site e atualizá-lo conforme necessário. Até então, essa responsabilidade cabia a uma única pessoa sem conhecimentos técnicos, que trabalhava com um template do WordPress e adicionava conteúdo a ele, o que estava se tornando cada vez mais desorganizado.

Com esse contexto apresentado, vamos à solução proposta para o projeto.


# Ação

## Abordagem arquitetural

Nossa abordagem consistia em combinar [microsserviços](https://cloud.google.com/learn/what-is-microservices-architecture) com bancos de dados replicados usando a técnica [Master-Slave](https://dev.mysql.com/doc/refman/9.7/en/replication.html), ou Primary-Secondary ou Source-Replica, dependendo da nomenclatura com a qual você está familiarizado. Dividimos cada microsserviço como uma seção do site; por exemplo, a seção que continha todo o conteúdo sobre os cursos oferecidos pela faculdade seria um único microsserviço responsável por lidar com as informações desse tema.

### Qual é o papel da replicação neste cenário?

O uso dessa técnica funciona como um mecanismo de autenticação de dois fatores para o conteúdo entregue ao site principal, no qual cada microsserviço teria uma réplica do banco de dados principal. As alterações seriam feitas no painel administrativo e enviadas ao microsserviço correspondente, que então as gravaria na réplica. Depois que as alterações fossem aprovadas, elas seriam enviadas ao banco de dados principal, que é lido pela aplicação principal no front-end e exibido ao usuário.

Por exemplo, imagine que um professor altere a descrição de uma disciplina que leciona, adicionando mais informações, e decida confirmar essas alterações. As alterações ficarão marcadas como “Aguardando aprovação” por um administrador do sistema, ou como você preferir chamá-lo. Essa pessoa seria responsável por validar se a alteração foi feita corretamente e não prejudicou o conteúdo do site. Após a aprovação, as alterações armazenadas no banco de dados do microsserviço correspondente teriam seu status alterado para aprovado e seriam enviadas ao banco de dados principal, que contém as informações atuais do site.

## Meu papel no projeto

Desenvolvi o microsserviço responsável por gerenciar a seção de Extensões do site, que exibe informações sobre cursos extracurriculares oferecidos pela faculdade, gratuitos para todos, inclusive não estudantes.

A stack usada no desenvolvimento foi PHP puro devido a algumas restrições <span class="spoiler">(se você estiver curioso sobre elas, sugiro conferir [este](@/Projects/Front-End%20Fatec%20Itaquera/index.md) projeto)</span>; simplificando, um diagrama desse tipo de comunicação seria:

<figure>
{{ image(url="diagram.png", alt="simple diagram", no_hover=true) }}
  <figcaption>Um diagrama simples representando uma visão geral de como as coisas funcionam</figcaption>
</figure>

# Resultado

Embora tenha sido um projeto curto, com duração de alguns meses, ele foi bem-sucedido e cumpriu o prazo estabelecido. Fornecemos uma base satisfatória para o site com este projeto de back-end, que poderia ser aprimorada com mais tempo e uma equipe para mantê-la no longo prazo <span class="spoiler">(o que não aconteceu)</span>, criando uma espécie de microframework PHP no futuro.

Se você tiver alguma dúvida sobre este projeto ou algum feedback sobre este artigo, fique à vontade para falar comigo pelo [LinkedIn](https://www.linkedin.com/in/davialp/).

