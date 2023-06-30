# Apenas Um Readme

Tudo escrito na unha. :grinning:

### Tópicos 

- [Apache Kafka](#apache-kafka)
- [DDD](#ddd-v02)
- [TDD](#tdd)
- [BDD](#bdd)
- [Scrum](#scrum)
- [SOLID](#solid)
- [Diferença entre interface e classe abstrata no Java](#diferença-entre-interface-e-classe-abstrata-no-java)
- [Arquitetura Hexagonal](#arquitetura-hexagonal)
- [Spring Security](#spring-security)

## Apache Kafka

## DDD v0.2
  <small><em>"Se os programadores não estão interessados no domínio, eles aprendem apenas o que a aplicação deve fazer, não os princípios por trás dela."<br> - Eric Evans</em></small>
  
O DDD, Domain-Driven Design ou simplesmente Design Orientado ao Domínio, é uma abordagem para a modelagem de software que tem como foco principal a criação de um modelo de domínio. <br> 
Baseia-se na implementação de modelos que refletem as competências e a complexidade do negócio da organização.<br>
Essa abordagem oferece ferramentas de modelagem estratégica e tática, com o objetivo de entregar um software de alta qualidade. <br> 
É especialmente útil no desenvolvimento de aplicações que lidam com processos de negócios complexos, proporcionando uma aceleração no seu desenvolvimento.</br> Pode ser utilizado independente da linguagem. <br>
<strong> Não é: forma de organizar pastas, organização de código, tecnologia, framework, arquitetura ou metodologia. Também não impõe processos rígidos ao time. </strong> <br>

Alguns dos termos utilizados são: Design estratégico e design tático.

Começando pelo design tático ou modelagem tática, é basicamente a implementação utilizando o Domain Model Pattern <br>
(uma abordagem que diz como escrever as classes que irão mapear os modelos do mundo real e implementar os comportamentos do negócio). <br>
Padrões no design tático: Entities e Value Objects definem os conceitos do domínio. Domain Service assume a responsabilidade que não se encaixa em outros projetos. Aggregates que define fronteiras entre objetos. Factory e repositories que lida com a criação e armazenamento de objetos.

O design estratégico ou modelagem estratégica, é a parte teórica. As informações abaixo fazem parte do padrão estratégico.
 <small><em>"O Design Estratégico é como fazer o rascunho antes de entrar nos detalhes da implementação. Que ele destaca o que é estrategicamente importante para o negócio; como dividir o trabalho por importância; e como fazer integrações da melhor maneira"<br> - Vaughn Vernon</em></small>
 
Diferente da hospedagem de sites, o domínio abordado nesse tópico é o negócio da sua empresa ou o assunto do seu projeto. Então, precisa necessariamente entender o negócio para ser possível
de implementar o DDD em um projeto. Nessa implementação existem 2 papeis: <strong> o time de desenvolvimento e os domain experts </strong> <br>

Existem alguns pilares no DDD:
1. <strong> Linguagem Ubíqua: </strong> utilizada por toda a equipe do projeto. Criada justamente para facilitar a comunicação e o entendimento dos termos específicos utilizados tantos
pelo time de desenvolvimento quanto pelo domain experts, onde cada entidade possui termos onde são necessários "uma tradução" para haver uma comunicação clara entre ambos os times.
2. <strong> Bounded Context: </strong> delimitação do contexto. Uma vez que todo domínio é colocado em um modelo, para evitar que seja complexo demais, delimitará esses contextos baseados nas intenções de negócio.
Cada bounded context pode ter sua linguagem ubíqua, sua abordagem de arquitetura, de armazenamento de dados e até a própria equipe de desenvolvimento.
Para criar esse modelo e entender como os bounded contexts se relacionam e como se comunicam é utilizado o <strong>Context map</strong>(um modelo que dará uma visão geral do software,
geralmente um desenho simples que da para ser feito com uma caneta e um quadro branco).
Existem alguns padrões de relacionamento entre os bounded contexts e implicam diretamente na estratégia de como os times de projeto irão trabalhar. Na dependência entre eles, na arquitetura e até na
estratégia de comunicação. Os principais tipos de relacionamentos entre os contextos são:
Shared Kernel: Quando vários bounded contexts, compartilham do mesmo domínio. Alterando-o, afetará todas as equipes.<br>

Customer-Supplier Development: quando existe um relacionamento de cliente-fornecedor, ou, Downstream e Upstream. A Equipe Upstream pode ter êxito interdependente da equipe Downstream.
Um contexto é o fornecedor do serviço e o outro é o consumidor. As equipes definirão testes de aceitação automatizados que irão validar as interfaces que a equipe de Upstream fornece, com isso as equipes
de fornecedores poderá fazer as modificações sem se preocupar em quebrar o sistema.
Tipos de relacionamentos Customer-Supplier Development:
1. Conformist: relacionamento onde o bounded context downstream se conforma que o modelo upstream não atende suas necessidades e as modificações realizadas por ele impactam diretamente em seu contexto. Mas ele se vira.
2. Partner: nesse relacionamento os bounded contexts parceiros, unidos por uma dependência mutua e deverão trabalhar em conjunto.
3. Anticorruption Layer: ja nesse relacionamento a equipe downstream cria uma camada para proteger o seu contexto das modificações do upstream (comum em sistemas legados).

## TDD

## BDD

## Scrum

## SOLID

## Diferença entre interface e classe abstrata no Java

## Arquitetura Hexagonal

## Spring Security
