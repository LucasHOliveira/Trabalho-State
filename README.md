# **Pattern Name and Classification**
 **Template Method**

# **Intent**

 * Permite que um objeto altere seu comportamento de acordo com mudança interna de estado.
 * Dará a impressão que o objeto mudou de classe.


# **Motivation**

1. onsidere a classe TCPConnection que representa uma conexão numa rede de comunicações. Um objeto TCPConnection pode estarem diversos estados diferentes: Established (Estabelecida), Listening (Escutando), Cloded (Fechada). Quando um objeto TCPConnecetion recebe solicitações de outros objetos, ele responde de maneira difente dependendo do seu estado corrente.
2. A idéia chave deste padrão é introduzir uma classe abstrata chamada TCPState para representar os estados da conexão na rede. A classe TCPState declara uma interface comum para todas as classes que representam diferentes estados operacionais. As sublclasses de TCPState implementam comportamentos específicos ao estado.
3. A classe TCPConnection mantém um objeto de estado (uma instância da subclasse de TCPstate) que representa o estado corrente na conexão TCP.
4. Connection delega todas as solicitações específicas de estados para este objeto de estado. TCPConenection usa sua instância da subclasse de TCPState para executar operações específicas ao estado da conexão.
5. Sempre que a conexão muda de estado, o objeto TCPConnection muda o objeto de estado que ele utiliza. Por exemplo, quando a conexão passa do estado Established para o estado Closed, TCPConnection substituirá sua instâncaia de TCPEstablished por uma instância de TCPClosed.

# **Applicability**

 * Como foi mostrado o padrão vai alterar o comportamento de um objeto quando houver alguma mudança no seu estado interno, como se ele tivesse mudado de classe. A solução seria um código que permitisse que sejam respeitados ao menos os princípios: “Encapsule o que varia” (os estados do projeto); “Classes devem estar abertas para expansão, mas fechadas para modificação” (quando há um novo estado temos de modificar os métodos ao invés de apenas acrescentar novos); e “Uma classe deve ter somente uma única razão para mudar”.

Como exemplo trouxe um código que simula o jogo do Mario, onde a cada tipo de ação que aconteça com o Mario é definido um dos estados abaixo:

1. Mario Pequeno: Ele inicia o jogo pequeno e logo após ingeri um cogumelo e é passado para o próximo estado.
2. Mario Grande: Quando o mario consome um cogumelo e deixa de ser o Mario Pequno
3. Mario Fogo: O Mario pegou 1000 pontos e esta no estado de Mario Grande, assim ele vira o Mario de Fogo
4. Mario Capa: O Mario pegou 2000 pontos e esta no estado de Mario Grande, assim ele vira o Mario de Fogo
5. Mario Morto: Essa classe não foi definida, mas está contida dentro do Mario Pequno, onde caso ele receba um dano como Mario Pequeno o jogo acaba e o Mario morre.



# **Structure**

![Imagem](https://github.com/LucasHOliveira/Trabalho-State/blob/main/State.PNG)

# **Participants**

 * Contexto: delega solicitações específicas de estado ao objeto State.
 * State: Responsavel por pegar qual a intenção do contexto e de acordo com a intenção ele chama o ConcreteStateA ou ConcreteStateB
 * ConcreteStateA e ConcreteStateB: Possui o estado do objeto de acordo com o momento que ele foi definido.

# **Sample Code**

[Link para a pasta do código](https://github.com/LucasHOliveira/Trabalho-State/tree/main/State-Codigo/ProjetoState)