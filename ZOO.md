# Cenário: zoológico 

### Descrição do cenário: 
O zoológico de Fortaleza quer construir um software para gerenciar as suas diversas atividades, desde aquelas que envolvem os visitantes diários até aquelas de cuidado com os animais por profissionais capacitados. Para isso, pediram ajuda a um grupo de estudantes da UNIFOR para modelar o sistema, os quais tomaram como base boas práticas e padrões arquiteturais. Nesse sentido, o zoológico gostaria de abordar, num primeiro momento e de forma simplificada, as operações de venda de bilhetes, de alimentação dos animais e de consultas veterinárias. Nas vendas ou transações, é necessário considerar a venda de ingressos do tipo inteira e meia entrada, e o turno ao qual eles se referem, porque uma pessoa pode comprar um bilhete para passar até 4horas no zoológico, tendo em vista as pausas necessárias dos animais. Com relação aos profissionais, dois são essenciais: o veterinário, responsável por examinar os animais, e o tratador, responsável especialmente pela alimentação. Cada um deles trabalha em um turno específico, que dura de 8h a 10h diárias dependendo do cargo. Além disso, existem diversos animais, com características e necessidades diferentes mas que devem ser abarcados pelo sistema. Um dos pontos principais levantados foi a necessidade de registrar as três operações em um banco de dados para posterior geração de relatórios e planilhas.


### Padrões GRASP utilizados:
Especialista
Controlador
Polimorfismo
Invenção Pura

### Justificativas:
- **Padrão Especialista para TransaçãoBilhete:** Existem dois tipos de bilhete, então é necessária uma classe especialista em gerar o subtotal para cada tipo;
- **Padrão Controlador para ControladorAlimentação e ControladorTransação:** Alimentação e Transação são operações iniciadas em um horário específico, e no caso da alimentação são programadas em um momento anterior para que cada tratador a cumpra de acordo com o que foi pré-estabelecido. O controlador serve para manipular essas operações, ambas em uma interface específica para que os funcionários realizem as tarefas. 
- **Padrão Polimorfismo para Veterinário e Tratador, Funcionário e Visitante, relacionados à Pessoa:** No caso, as pessoas (ou usuários) podem ser divididos em duas subclasses, Visitante e Funcionário, o que impacta nas operações que podem ser realizadas no sistema e em suas características (funcionário tem matrícula, por exemplo). E, mais ainda, existem tipos diferentes de funcionários que, novamente, realizam atividades diferentes dependendo de suas especificidades, no caso seriam o Tratador e o Veterinário. Assim, herdam características em comum mas devem ser separados devido às possibilidades de ação no sistema. 
- **Padrão Invenção Pura para classes PersistentStorageBroker:** As classes PersistentStorageBroker são a conexão do sistema com o banco de dados, o que se constitui como um requisitos de fundamental importância para o usuário, e, no contexto do diagrama, é uma classe que não representa necessariamente um objeto no mundo real, e sim um outro sistema (integrações serão feitas na codificação back-end do software).

### Outras sugestões:
- Assim como cenários de vendas, é possível adicionar classes relacionadas às operações de pagamento, controladas pelo controlador, e dependendo ainda das especificações dos requisitos do zoológico;
- É possível também aprofundar em outras atividades dos tratadores e veterinários, para além de alimentar e examinar, como realizar exames, dependendo também das especificações;
- Para o caso das operações de venda, pode-se pensar também numa GUI com a qual um funcionário específico irá realizar a transação propriamente dita;
- Padrão Singleton para uma registradora de caixa, por exemplo, tendo em vista que só será criada uma vez (no caso de uma bilheteria única) mas seus métodos serão chamados várias vezes no sistema.

_Existem uma infinidades de caminhos, aqui estão apenas os primeiros num cenário hipotético priorizando a aplicação de padrões arquiteturais essenciais para aumentar a coesão e diminuir o acoplamento do código, levando em conta também escalabilidade, operacionalidade e manutenção do sistema a ser construído._
