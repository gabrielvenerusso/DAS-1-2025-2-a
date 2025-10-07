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

Aula - 06/10/2025
Ideia central
Além de cumprir as funções do domínio, um sistema só é bem-sucedido se atender a características de arquitetura (muitas vezes chamadas de “não funcionais”). Elas: (1) tratam de preocupações fora do domínio, (2) influenciam a estrutura do design e (3) são críticas para o sucesso da aplicação. Podem ser explícitas (citadas como requisitos) ou implícitas (precisam ser consideradas mesmo sem estarem escritas).

Exemplos de áreas
Auditoria, desempenho, segurança, requisitos/integrações, dados, legalidade/compliance e escalabilidade.

Por que importam
Guiam decisões estruturais (módulos, camadas, integrações, tecnologia). Ex.: usar processador de pagamentos terceirizado pode simplificar segurança e isolamento; processar pagamentos na aplicação exige módulos/serviços específicos e decisões fortes de segurança — a arquitetura muda.

Categorias e exemplos

Operacionais:
Disponibilidade/Continuidade: tempo ativo e recuperação de falhas.
Desempenho: tempos de resposta/throughput.
Recuperabilidade/Confiabilidade/Robustez: restaurar serviço, operar sob falhas, resistir a picos.
Escalabilidade: crescer sem degradação relevante.

Estruturais:
Configuração/Extensão: facilidade de parametrizar e adicionar funções.
Instalabilidade/Atualização: instalar/atualizar com baixo atrito.
Aproveitamento/Reuso e Modularidade.
Localização/Portabilidade/Suporte/Manutenção.

Transversais:
Acessibilidade e Usabilidade.
Armazenamento/Retenção de dados.
Autenticação/Autorização.
Legalidade/Privacidade (LGPD, auditoria).
Segurança (criptografia, chaves, logs).
Suporte/Operabilidade (SLA, monitoramento).

Relação com modelos ISO
A ISO agrupa capacidades como: Eficiência de desempenho, Compatibilidade (coexistência/interoperabilidade), Usabilidade (adequação, aprendizado, acessibilidade), Confiabilidade (maturidade, tolerância a falhas, recuperabilidade), Segurança, Manutenibilidade (análise, modificação, testabilidade) e Portabilidade. “Adequação/totalidade/correção funcional” dizem respeito ao domínio e não são, por si, características arquiteturais.

Ambiguidades e sobreposições
Termos podem conflitar/ser vagos (ex.: interoperabilidade vs. compatibilidade). Muitas características se sobrepõem (ex.: disponibilidade ↔ confiabilidade).

Trade-offs
Toda escolha favorece algumas qualidades e prejudica outras (p.ex., mais segurança pode reduzir desempenho). “Arquitetura menos pior” = tornar explícitos esses compromissos e equilibrá-los com os objetivos do negócio.
Como aplicar na prática
Eleger poucas características prioritárias.
Transformá-las em cenários mensuráveis (estímulo → resposta esperada).
Definir táticas/decisões de design que as suportem.
Mapear e aceitar trade-offs conscientemente.
Validar continuamente (testes, monitoração, SLO/SLA).


Aula - 07/10/2025
🧩 CQRS — Command Query Responsibility Segregation
O CQRS (Command Query Responsibility Segregation) é um padrão arquitetural que separa as operações de escrita (Commands) e leitura (Queries) de um sistema, permitindo maior clareza, performance e escalabilidade.

⚙️ Conceito
Tradicionalmente, o mesmo modelo de dados é usado tanto para atualizar quanto para consultar informações.
Com CQRS, esses dois fluxos são separados:

Tipo	Responsabilidade	Exemplo	Foco
Command	Executa ações que alteram o estado do sistema (criar, atualizar, excluir).	CreateOrderCommand, UpdateClienteCommand	Escrita
Query	Recupera dados sem alterar o estado do sistema.	GetOrderByIdQuery, ListarClientesQuery	Leitura

Essa separação permite otimizações específicas para cada operação e facilita o uso de diferentes modelos de dados ou até bancos independentes.

🚀 Benefícios
🔹 Separação de responsabilidades: leitura e escrita ficam independentes.
🔹 Maior escalabilidade: leitura e escrita podem escalar separadamente.
🔹 Performance otimizada: queries mais rápidas e simples.
🔹 Código mais limpo: fácil manutenção e testes.

⚠️ Pontos de Atenção
🔸 Aumenta a complexidade da arquitetura.
🔸 Pode exigir sincronização entre os modelos de leitura e escrita.
