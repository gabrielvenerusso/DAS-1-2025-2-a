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
