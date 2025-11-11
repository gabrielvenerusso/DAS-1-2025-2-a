Turma: das-1-2025-2-a
Aula 1 - 04/08/2025 !!
Principios de projeto de software - Capitulo 5 do livro

Padrões mitigam a complexidade

Abstração:
Seria representar algo do mundo real para resolver um problema

Config <-- configurações

Controller <-- html, api, rest

Entity <-- dados

Repository <-- Con db

Service <-- Lógica

Ocultamento de informação:
Não há necessidade de entender todo o funcionamento de um framework para poder usa-lo

Código Coeso (Coesão)
Um código que realiza uma tarefa muito bem feita! Elementos de um módulo (como classes, funções ou pacotes) estão relacionados e trabalham juntos para um propósito único e bem definido.

Acoplamento
Acoplamento: dependência de uma classe com outra
Autoacoplamento: instanciação e uso de um método no construtor de outra class
UML

Flecha vazia: herança
Flecha tracejada: implementação
Flecha cheia: Associação
---//---

Aula 2 - 05/08/2025 !!
O que é SOLID?

Usar a orientação a objetos do jeito mais correto possível!

S — Single Responsibility Principle (Princípio da responsabilidade única) O — Open-Closed Principle (Princípio Aberto-Fechado) L — Liskov Substitution Principle (Princípio da substituição de Liskov) I — Interface Segregation Principle (Princípio da Segregação da Interface) D — Dependency Inversion Principle (Princípio da inversão da dependência)

Maneira de usar o conceito de responsábildiade única M - Dados V - HTML C - Controlar a tela

package br.univille;

import javax.swing.JButton; import javax.swing.JFrame;

public class Janelinha extends JFrame {

private JButton botaozinho;
private Controlador controlador;

public Janelinha() {
    setTitle("Eu não acredito");
    setSize(500, 500);
    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

    botaozinho = new JButton("ME CLICA");
    controlador = new Controlador();
    botaozinho.addActionListener(controlador);

    add(botaozinho);

    setVisible(true);
}

public static void main(String[] args) {
    new Janelinha();
}
package br.univille;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JOptionPane;

public class Controlador implements ActionListener {

@Override
public void actionPerformed(ActionEvent e) {
    meClica();
}

private void meClica() {
    JOptionPane.showMessageDialog(null, "NÃO ACREDITO");
}
}
---//---

Aula 3 - 11/08/2025 !!
#Princípio da Inversão de Dependência (Dependency Inversion Principle) Em vez de o Controller depender diretamente de uma implementação concreta, ele deve se comunicar primeiro com uma interface ou abstração. Isso evita o acoplamento direto entre classes, facilitando a manutenção, a troca de implementações e a realização de testes. A ideia central é: módulos de alto nível não devem depender de módulos de baixo nível, ambos devem depender de abstrações.

Prefira Composição à Herança
A herança deve ser usada apenas quando existe uma relação clara do tipo "é um" (is-a), por exemplo:

Animal → Gato

Animal → Cachorro

Um gato nunca se tornará um cachorro, ou vice-versa. Quando a relação não for estritamente hierárquica, prefira composição, ou seja, construir comportamentos combinando diferentes objetos, em vez de criar cadeias de herança profundas.

A composição oferece mais flexibilidade, evita acoplamento excessivo e facilita a reutilização de código.

--//--

Princípio de Demeter (Menor Conhecimento)
Também chamado de Law of Demeter.

A ideia é evitar dependências desnecessárias e não acessar diretamente objetos internos de outros objetos. Fuja de variáveis globais e trabalhe com as informações locais e disponíveis no contexto atual.

--//--

Princípio do Aberto/Fechado (Open/Closed Principle)
Um objeto deve proteger seu comportamento para que ninguém possa quebrá-lo alterando diretamente sua lógica interna. A ideia é que quem cria a classe não quer que ela seja modificada, mas sim estendida com novas funcionalidades.

Aberto para extensão, fechado para modificação Proteja o que a classe já faz, mas permita adicionar novos comportamentos sem alterar o código existente.

Aula 4 - 12/08/2025
SOLID:

L: Princípio de substituição de Liskov - redefinição de métodos de classe base em classe filho (aplicado quando tem herança). Se há uma herança, com vários filhos, o código dos filhos deve ser feita de tal maneira a manter a compatibilidade com o pai, caso elas forem substituídas (sem quebrar o padrão que o pai tem) Filho(método x) -> Pai <- Filho2(Método x) | aplicar os dois filhos não quebra a classe


Aula 5 - 26/08/2025 Fundamentos da Arquitetura de Software

Caracteristicas da Arquitetura = requisitos não funcionais Disponibilidade - estar online por um tempo definido Confiabiliade - o sistema faz o que deve ser feito Segurança - quão seguro o sistema é (cada CPF vazado é no mínimo 50 mil de multa) Testabilidade Escalabildade Agilidade Tolerância a falhas Elasticidade Recuperabilidade Desempenho Implementabilidade Capacidade de aprendizagem

É impossível um sistema atender todas as caracnteristicas da arquitetura, sempre ficará alguma coisa pendente

Supply chain - utilização de bliblioteca abertas não confiáveis

DECISÕES DA ARQUITETURA São regras que precisam ser mantidas no sistema, para que o mesmo tenha o mínimo de padronização. exemplo: iremos utilizar arquitetura baseada em camadas.

Decidir a esturutra do sistema, escolhendo a arquitetura, uma decisão importante, que poderá ter um custo alto se feito de qualquer jeito

A decisão da arquitetura depende das caracteristicas da arquitetura, um depende do outro

PRINCÍPIOS DO DESIGN Boas práticas, princípios que seria ideal sempre ser seguido

(arquitetura distribuida) - micro serviços - pequenas atividades bem feitas, cada micro serviço tem seu próprio banco de dados (cada um tem vida própria)

sistema de mensageria - serviço colocado no meio da arquitetura, que permite a troca de mensagens dos micros serviços, um manda mensagem e o outro recebe

event driven architecture - arquitetura baseada em eventos (alexa - cria máquina virtual, responde a pergunta, e cai a máquina virtual)

Aula 6 - 01/09/2025

EXPECTATIVAS DO ARQUITETO

Tomar decisões de arquitetura - decidir qual arquitetura/ estrutura será utilizada no sistema, utilizando sua experiência no mercado para orientar a sua equipe. "O segredo para tomar decisões arquiteturais eficientes é perguntar se a decisão da arquitetura está ajudando a orientar as equipes ao fazerem a escolha técnica certa ou se a decisão faz a escolha técnica por elas."

Analisar continuamente a arquitetura - todo sistema muda com o tempo, com isso, é função do arquiteto analisar o sistema continuamente e atualizar de acorodo com a arquitetura do sistema. O famoso "não mexe, que está funcionando", não deve ser considerado, e sim tomar decições corretas de acordo com suas análises que facilitarão o sistema

Manter-se atualizando com as últimas tendências - desenvolver software está cada vez mais complexo (Inteligência Artificial)

Assegurar a conformidade com as decisões - o arquiteto verifica continuamente se as equipes de desenvolvimento seguem as decisões da arquitetura e os princípios do design definidos, documentados e comunicados por ele.

Análise estática de código é a inspeção do código-fonte de um software sem executá-lo, utilizando ferramentas automatizadas para identificar bugs, vulnerabilidades de segurança e desvios de padrões de codificação antes da produção

Exposição e experiência diverisades - um bom arquiteto já teve experiência em várias áreaa/funções e linguagens. Essencial ele ter conhecimento da regra de negócio do produto

Ter conhecimento sobre o domínio do negócio -

Ter habilidades interpessoais - um arquiteto precisa ser um gestor tambémm, um líder da equipe, incetivando e extaindo o melhor de cada membro da equipe

Enteder e lidarr bem com questões políticas - fundamental negociar com o cliente, negociar mais prazos, funcionalidades, influenciar e proteger sua equipe

DEADLOCK - (ou interbloqueio) é uma situação de impasse em computação onde dois ou mais processos ficam permanentemente bloqueados, cada um esperando que o outro libere um recurso que ele precisa para continuar sua execução. Isso cria uma espera circular, onde o Processo A espera por um recurso do Processo B, e o Processo B espera por um recurso do Processo A, impedindo que qualquer um deles avance.

OPERAÇÕES - DevOps uma maneira de entregar valor ao meu cliente mais rápido metodologia que vai melhorando cada vez mais

Aula 7 - 02/09/2025

Resuma a diferença entre arquitetura e design ? A arquitetura de software define a estrutura global e os componentes principais de um sistema, ou seja, o que terá no sistema, enquanto o design se concentra nos detalhes de implementação desses componentes e suas interações em um nível mais baixo, ou seja, como será implamentado as decisões tomada pelo arquiteto. A arquitetura é uma visão de alto nível que garante requisitos globais como escalabilidade e segurança, enquanto o design detalha como cada parte do sistema funciona e se comunica.

Como é a formação do conhecimento de um arquiteto modelo T? Uma formação ampla, não se concentra em apenas uma linguagem ou área específica de trabalho. O arquieto tem a capacidade de resolver o mesmo problema, utilizando meios diferentes.

Aula - 07/10/2025 🧩 CQRS — Command Query Responsibility Segregation O CQRS (Command Query Responsibility Segregation) é um padrão arquitetural que separa as operações de escrita (Commands) e leitura (Queries) de um sistema, permitindo maior clareza, performance e escalabilidade.

⚙️ Conceito Tradicionalmente, o mesmo modelo de dados é usado tanto para atualizar quanto para consultar informações. Com CQRS, esses dois fluxos são separados:

Tipo Responsabilidade Exemplo Foco Command Executa ações que alteram o estado do sistema (criar, atualizar, excluir). CreateOrderCommand, UpdateClienteCommand Escrita Query Recupera dados sem alterar o estado do sistema. GetOrderByIdQuery, ListarClientesQuery Leitura

Essa separação permite otimizações específicas para cada operação e facilita o uso de diferentes modelos de dados ou até bancos independentes.

🚀 Benefícios 🔹 Separação de responsabilidades: leitura e escrita ficam independentes. 🔹 Maior escalabilidade: leitura e escrita podem escalar separadamente. 🔹 Performance otimizada: queries mais rápidas e simples. 🔹 Código mais limpo: fácil manutenção e testes.

⚠️ Pontos de Atenção 🔸 Aumenta a complexidade da arquitetura. 🔸 Pode exigir sincronização entre os modelos de leitura e escrita.


Aula - 14/10/2025

A arquitetura em camadas (ou n-tier) é um dos estilos mais comuns por sua simplicidade e baixo custo, sendo usada em muitas aplicações empresariais. Ela organiza o sistema em camadas horizontais com responsabilidades específicas — normalmente: apresentação, comercial (negócios), persistência e banco de dados. Cada camada trata apenas da sua função, promovendo a separação de responsabilidades e facilitando a manutenção e especialização das equipes.
As camadas podem ser fechadas (onde cada requisição passa sequencialmente por todas) ou abertas (permitindo pular níveis). Camadas fechadas aumentam o isolamento e reduzem o acoplamento, mas diminuem a agilidade.
É uma boa escolha para aplicações pequenas ou com recursos limitados, porém apresenta baixa escalabilidade, testabilidade e desempenho em sistemas grandes, podendo gerar o antipadrão sinkhole (camadas que apenas repassam dados sem lógica real).

Aula - 20/10 e 21/10

O Estilo de Arquitetura em Camadas organiza uma aplicação em níveis horizontais, cada um com responsabilidades bem definidas — normalmente: apresentação, negócio (comercial), persistência e banco de dados. Essa separação segue o princípio de isolamento e separação de preocupações, onde cada camada conhece apenas a imediatamente inferior, reduzindo o acoplamento e facilitando a manutenção.
Camadas fechadas obrigam a passagem sequencial entre níveis, promovendo isolamento; já camadas abertas permitem acessos diretos, aumentando a flexibilidade.
É uma arquitetura simples, familiar e de baixo custo, ideal para aplicações pequenas ou médias, mas com limitações em escalabilidade, desempenho e testabilidade em sistemas grandes.
Apesar disso, continua sendo um ponto de partida comum, pois reflete a estrutura típica das equipes (UI, back-end, DBAs) e é fácil de compreender e implementar.

Aula - 27/10 e 28/10

O Estilo de Arquitetura Pipeline é baseado na ideia de processamento sequencial de dados, dividido em estágios independentes, semelhantes a uma linha de montagem. Cada estágio (ou filtro) executa uma transformação específica nos dados e os envia para o próximo estágio, até que o resultado final seja obtido.
Esse estilo favorece a modularidade, reuso e facilidade de manutenção, pois cada componente tem uma responsabilidade única e clara. Além disso, permite paralelismo e escalabilidade, já que diferentes estágios podem processar dados simultaneamente.
É muito usado em processamento de dados, ETL (Extract, Transform, Load), compiladores e streams de processamento em tempo real.
Entretanto, sua principal limitação é a dependência da ordem de execução, o que pode tornar o fluxo rígido e menos adaptável a cenários complexos ou dinâmicos.

Aula - 03/11 e 04/11

O Estilo de Arquitetura Microkernel (ou plug-in architecture) é centrado em um núcleo mínimo e estável — o microkernel — que fornece os serviços básicos e a infraestrutura da aplicação. Ao redor dele, há módulos plugáveis (plugins) que adicionam ou estendem funcionalidades sem alterar o núcleo.
Esse modelo separa claramente a lógica essencial (core system) das funcionalidades variáveis, facilitando manutenção, testes e evolução do sistema. É muito usado em sistemas que precisam de alta extensibilidade, como IDEs (ex: Eclipse, Visual Studio), sistemas operacionais e softwares ERP.
Suas principais vantagens são a modularidade, flexibilidade e a redução do impacto de mudanças.
Por outro lado, exige planejamento cuidadoso das interfaces e pontos de extensão, e pode gerar complexidade na comunicação entre o núcleo e os plugins se mal projetado.

Aula - 10/11 e 11/11

O Estilo de Arquitetura de Microsserviços divide o sistema em pequenos serviços independentes, cada um responsável por uma função específica do domínio. Esses serviços se comunicam entre si por APIs leves (geralmente REST ou mensageria) e podem ser implantados, escalados e mantidos de forma autônoma.
Cada microsserviço possui sua própria base de dados e ciclo de vida, promovendo baixo acoplamento e alta coesão. Isso aumenta a resiliência, escalabilidade e a flexibilidade tecnológica, permitindo o uso de diferentes linguagens ou frameworks conforme a necessidade.
Entretanto, a arquitetura de microsserviços exige boa orquestração, monitoramento, integração contínua e um esforço maior de infraestrutura e comunicação entre serviços.
É ideal para sistemas grandes, dinâmicos e que precisam evoluir rapidamente, sendo amplamente usada por empresas como Netflix, Amazon e Uber.
