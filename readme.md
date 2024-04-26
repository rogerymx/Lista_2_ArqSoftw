# Lista 2 - Refatoração e modelagem

# 1. Single Responsibility Principle (SRP)
Conceito: Este princípio afirma que uma classe deve ter apenas uma razão para mudar, ou seja, deve ter apenas uma responsabilidade. Isso ajuda a tornar o código mais modular, facilita testes e manutenção, e reduz a complexidade.

Implementação e Melhorias:

ContatoManager: Esta nova classe agora é responsável exclusivamente pelo gerenciamento dos contatos (adicionar, remover, listar, buscar). Antes, essas responsabilidades estavam misturadas dentro da classe ContatosFacade.
ContatosNotifier: Uma nova classe dedicada a gerenciar os observadores e enviar notificações. Anteriormente, o ContatosFacade também lidava com a notificação de observadores, o que era uma segunda responsabilidade.
Com essa separação, as classes tornam-se mais coesas e menos acopladas, o que facilita entender e modificar uma parte do sistema sem afetar outras.

# 2. Dependency Inversion Principle (DIP)
Conceito: Este princípio orienta que módulos de alto nível não devem depender de módulos de baixo nível, ambos devem depender de abstrações. Além disso, abstrações não devem depender de detalhes; detalhes devem depender de abstrações.

Implementação e Melhorias:

ContatosFacade: Agora esta classe depende de abstrações (ContatoManager e ContatosNotifier), e não de detalhes concretos. Essas dependências são injetadas no construtor da classe, em vez de serem instanciadas diretamente dentro dela.
Interfaces e abstrações: Foi exemplificado a dependência em abstrações através da herança de ContatosFacade de uma interface abstrata IContatoOperations. No JavaScript real, as interfaces são mais um conceito do que uma estrutura formal, mas você pode emular este comportamento com classes abstratas ou simplesmente seguindo uma convenção de design.
Isso aumenta a flexibilidade do sistema, torna o código mais reutilizável e facilita testes unitários, uma vez que dependências podem ser facilmente simuladas ou substituídas.

# 3. Open/Closed Principle (OCP)
Conceito: Classes ou entidades devem estar abertas para extensão, mas fechadas para modificação. Isso significa que você pode adicionar novos comportamentos sem alterar o código existente.

Implementação e Melhorias:

ContatosNotifier e Observer pattern: A implementação com observadores permite que novos comportamentos (como diferentes maneiras de reagir a mudanças nos contatos) sejam adicionados sem modificar o código existente. Isso é feito através da extensão da classe Observer.
Essa abordagem permite que o sistema cresça e evolua com novos requisitos sem necessidade de refazer ou alterar as implementações existentes, seguindo assim o princípio de estar aberto para extensão, mas fechado para modificação.