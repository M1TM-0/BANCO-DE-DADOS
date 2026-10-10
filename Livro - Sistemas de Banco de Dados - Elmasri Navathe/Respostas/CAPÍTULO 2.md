# Perguntas de revisão

**2.1 Defina os seguintes termos: modelo de dados, esquema de banco de dados, estado de banco de dados, esquema interno, esquema conceitual, esquema externo, independência de dados, DDL, DML, SDL, VDL, linguagem de consulta, linguagem hospedeira, sublinguagem de dados, utilitário de banco de dados, catálogo, arquitetura cliente/servidor, arquitetura de três camadas e arquitetura de n camadas.**

- **Modelo de dados:** conjunto de conceitos usados para descrever a estrutura de um banco de dados, incluindo tipos de dados, relacionamentos e restrições, além de operações básicas para especificar consultas e atualizações.
- **Esquema de banco de dados:** descrição da estrutura de um banco de dados, definida durante seu projeto e que normalmente não muda com frequência. Pode ser representado visualmente por um diagrama de esquema, cujos elementos representam componentes da estrutura do banco.
- **Estado do banco de dados:** conjunto de dados efetivamente armazenados em um determinado momento. Seu estado pode mudar quando dados são inseridos, excluídos ou modificados.
- **Esquema interno:** descreve a organização física dos dados no armazenamento, incluindo estruturas de arquivos e caminhos de acesso.
- **Esquema conceitual:** descreve a estrutura lógica do banco de dados como um todo para uma comunidade de usuários. Oculta os detalhes do armazenamento físico e se concentra nas entidades, nos tipos de dados, nos relacionamentos e nas restrições.
- **Esquema externo ou visão do usuário:** descreve a parte do banco de dados relevante para determinado usuário ou grupo de usuários, ocultando os dados que não são necessários para eles.
- **Independência de dados:** capacidade de alterar o esquema de um nível do sistema sem precisar alterar o esquema do nível imediatamente superior.
  - **Independência lógica de dados:** capacidade de alterar o esquema conceitual sem precisar alterar os esquemas externos ou os programas de aplicação.
  - **Independência física de dados:** capacidade de alterar o esquema interno sem precisar alterar o esquema conceitual. Consequentemente, os esquemas externos também não precisam ser alterados.
- **DDL (Data Definition Language — Linguagem de Definição de Dados):** usada para definir o esquema conceitual e, em alguns sistemas, também aspectos do esquema interno.
- **SDL (Storage Definition Language — Linguagem de Definição de Armazenamento):** usada para especificar o esquema interno. Na maioria dos SGBDs relacionais, não existe uma linguagem SDL separada; as configurações de armazenamento são definidas por outros comandos ou parâmetros.
- **VDL (View Definition Language — Linguagem de Definição de Visões):** usada para definir as visões que compõem os esquemas externos e seus mapeamentos para o esquema conceitual. Em muitos SGBDs relacionais, esse papel é desempenhado por comandos da própria SQL.
- **DML (Data Manipulation Language — Linguagem de Manipulação de Dados):** conjunto de comandos usado para consultar, inserir, excluir e modificar dados.
- **Linguagem de consulta:** linguagem usada para formular consultas ao banco de dados. Em geral, trata-se de uma DML de alto nível que permite especificar os dados desejados sem detalhar todas as etapas para obtê-los.
- **Linguagem hospedeira:** linguagem de programação de uso geral na qual comandos de uma DML podem ser incorporados. Os comandos de DML incorporados são chamados de **sublinguagem de dados**.
- **Utilitários de banco de dados:** ferramentas que auxiliam o administrador do banco de dados (DBA) na manutenção e no gerenciamento do sistema. Entre elas estão:
  - **Carga de dados:** importa arquivos existentes, como arquivos de texto ou sequenciais, para o banco de dados.
  - **Backup:** cria cópias de segurança dos dados. Dependendo da ferramenta e da estratégia utilizada, a cópia pode abranger todo o banco ou apenas parte dele.
  - **Reorganização do armazenamento:** reorganiza arquivos e estruturas de armazenamento e pode criar ou ajustar caminhos de acesso para melhorar o desempenho.
  - **Monitoração de desempenho:** acompanha o uso do banco de dados e fornece estatísticas ao DBA, que pode usá-las para decidir se deve reorganizar arquivos ou criar, alterar ou remover índices.
- **Catálogo:** repositório de metadados do banco de dados. Pode conter informações sobre tabelas, colunas, tipos de dados, arquivos, armazenamento, mapeamentos entre esquemas e restrições.
- **Arquitetura cliente/servidor:** modelo no qual o servidor oferece serviços aos clientes. Em um sistema de banco de dados, o cliente costuma cuidar da interface e de parte da lógica da aplicação, enquanto o servidor executa o SGBD e gerencia os dados.
- **Arquitetura de três camadas:** acrescenta uma camada intermediária entre o cliente e o servidor de banco de dados. Essa camada, geralmente chamada de servidor de aplicação, processa regras de negócio e intermedeia a comunicação com o banco.
- **Arquitetura de n camadas:** divide a aplicação em várias camadas ou componentes, que podem ser executados e mantidos separadamente. Essa arquitetura pode aumentar a modularidade e a escalabilidade e é comum em sistemas corporativos, como ERP e CRM. Uma camada de middleware pode intermediar a comunicação entre componentes e serviços.

**2.2 Discuta as principais categorias de modelos de dados. Quais são as diferenças básicas entre os modelos relacional, de objetos e XML?**

Os modelos de dados podem ser classificados, de forma geral, em modelos de alto nível ou conceituais, modelos representacionais ou de implementação e modelos de baixo nível ou físicos. Eles se diferenciam pelo nível de abstração e pelos detalhes que representam.

- **Modelo relacional:** representa os dados por meio de relações, geralmente apresentadas como tabelas compostas por linhas e colunas. As tabelas se relacionam por atributos e restrições, como chaves primárias e estrangeiras.
- **Modelo de objetos:** representa os dados por meio de objetos que possuem propriedades e operações. Objetos com estrutura e comportamento semelhantes pertencem a uma classe, e as classes podem ser organizadas em hierarquias. As operações associadas às classes são implementadas por métodos.
- **Modelo XML:** representa os dados por meio de estruturas hierárquicas, geralmente em forma de árvore, usando elementos e atributos. Ele combina características de representação de dados com recursos próprios da marcação de documentos.

**2.3 Qual é a diferença entre um esquema de banco de dados e um estado de banco de dados?**

O **esquema de banco de dados** é a descrição de sua estrutura, definida durante o projeto e alterada com pouca frequência. Pode ser representado por um diagrama de esquema.

O **estado do banco de dados** corresponde aos dados armazenados em um determinado momento. Ele pode mudar sempre que ocorre uma inserção, exclusão ou atualização de dados.

**2.4 Descreva a arquitetura de três esquemas. Por que precisamos de mapeamentos entre os níveis de esquema? Como diferentes linguagens de definição de esquema dão suporte a essa arquitetura?**

A arquitetura de três esquemas organiza as descrições do banco de dados em três níveis:

- **Esquema interno:** descreve a organização física dos dados no armazenamento.
- **Esquema conceitual:** descreve a estrutura lógica do banco de dados como um todo, incluindo entidades, tipos de dados, relacionamentos e restrições, sem detalhar como os dados são armazenados fisicamente.
- **Esquemas externos:** descrevem as partes do banco de dados relevantes para diferentes usuários ou grupos de usuários.

São necessários **mapeamentos** entre os níveis para que o SGBD possa traduzir consultas e operações de um nível para outro e apresentar os resultados no formato esperado. Dessa forma, os diferentes esquemas oferecem visões distintas do mesmo banco de dados.

Quanto às linguagens, a **DDL** é usada para definir o esquema conceitual e, em alguns sistemas, aspectos do esquema interno; a **SDL**, quando disponível separadamente, define o esquema interno; e a **VDL** define os esquemas externos e seus mapeamentos. Em muitos SGBDs relacionais, comandos da SQL também são usados para definir visões.

**2.5 Qual é a diferença entre independência lógica e independência física dos dados? Qual delas é mais difícil de alcançar? Por quê?**

- **Independência lógica:** permite alterar o esquema conceitual sem precisar modificar os esquemas externos ou os programas de aplicação.
- **Independência física:** permite alterar o esquema interno sem precisar modificar o esquema conceitual nem, consequentemente, os esquemas externos.

A **independência lógica costuma ser mais difícil de alcançar**, pois os programas de aplicação frequentemente dependem da estrutura lógica dos dados que utilizam. Por isso, uma alteração no esquema conceitual pode afetar as visões e os programas. Já as alterações físicas, como reorganizar arquivos ou modificar índices, geralmente podem ser tratadas sem mudar a estrutura lógica, desde que os mapeamentos sejam mantidos corretamente.

**2.6 Qual é a diferença entre DMLs procedurais e não procedurais?**

- **DML procedural:** o usuário especifica quais dados deseja obter e também como recuperá-los, descrevendo as etapas da operação. Em geral, exige mais detalhes sobre o procedimento de acesso aos dados.
- **DML não procedural ou declarativa:** o usuário especifica quais dados deseja obter, sem precisar descrever todas as etapas para recuperá-los. Normalmente, opera sobre conjuntos de registros e permite que o SGBD determine o plano de execução. A SQL é um exemplo de linguagem predominantemente declarativa.

**2.7 Discuta os diferentes tipos de interfaces amigáveis e os usuários que normalmente utilizam cada tipo.**

- **Interfaces baseadas em menus:** apresentam uma lista de opções que orienta o usuário na execução de tarefas. São úteis para usuários casuais ou iniciantes.
- **Aplicativos para dispositivos móveis:** permitem acessar e manipular dados por meio de celulares ou tablets. São usados, por exemplo, por usuários que precisam consultar informações em mobilidade.
- **Interfaces baseadas em formulários:** apresentam campos para consulta ou inserção de dados. São comuns entre usuários paramétricos, que executam transações repetitivas e predefinidas.
- **Interfaces gráficas com o usuário (GUI):** usam elementos visuais, como ícones, botões, menus e diagramas, para facilitar a interação com o sistema.
- **Interfaces de linguagem natural:** permitem formular solicitações em linguagem cotidiana, por texto ou, em alguns sistemas, por voz. O sistema tenta interpretar essas solicitações e relacioná-las aos dados disponíveis.
- **Pesquisa baseada em palavras-chave:** permite pesquisar dados ou documentos usando palavras ou expressões, de maneira semelhante à pesquisa na Web.
- **Interfaces de entrada e saída de voz:** permitem fornecer consultas por voz e receber respostas faladas ou outros resultados sonoros.
- **Interfaces para usuários paramétricos:** oferecem comandos abreviados, teclas de função ou telas específicas para executar rapidamente transações repetitivas.
- **Interfaces para o DBA:** disponibilizam comandos e ferramentas administrativas para criar contas, conceder permissões, alterar esquemas, definir parâmetros e gerenciar o armazenamento.

**2.8 Com que outros softwares um SGBD interage?**

Um SGBD pode interagir com o sistema operacional, compiladores ou pré-processadores das linguagens hospedeiras, softwares de comunicação e aplicações que acessam o banco de dados.

**2.9 Qual é a diferença entre as arquiteturas cliente/servidor de duas e de três camadas?**

- **Duas camadas:** o cliente normalmente reúne a interface e parte da lógica da aplicação, enquanto o servidor executa o SGBD e gerencia os dados. A comunicação pode usar APIs e drivers padronizados, como ODBC e JDBC.
- **Três camadas:** acrescenta um servidor de aplicação entre o cliente e o servidor de banco de dados. A camada intermediária processa regras de negócio, pode centralizar controles de segurança e organiza a comunicação entre a interface e o banco. Essa arquitetura é comum em aplicações Web.

A arquitetura de duas camadas tende a ser mais simples, mas a de três camadas facilita a manutenção centralizada da lógica de negócio e pode oferecer maior escalabilidade para aplicações com muitos usuários.

**2.10 Discuta alguns tipos de utilitários e ferramentas de banco de dados e suas funções.**

- **Carga de dados:** importa arquivos existentes, como arquivos de texto ou sequenciais, para o banco de dados. Algumas ferramentas também auxiliam na conversão de dados entre sistemas com estruturas diferentes.
- **Backup:** cria cópias de segurança dos dados, que podem ser completas ou parciais, conforme a estratégia adotada.
- **Reorganização do armazenamento:** reorganiza arquivos e estruturas de armazenamento e pode ajustar caminhos de acesso para melhorar o desempenho.
- **Monitoração de desempenho:** acompanha o uso do banco de dados e fornece estatísticas ao DBA. Com base nelas, o administrador pode decidir se deve reorganizar arquivos ou criar, alterar ou remover índices.

**2.11 Qual é a funcionalidade adicional incorporada na arquitetura de n camadas (n > 3)?**

A arquitetura de n camadas divide a lógica da aplicação em várias camadas ou componentes menores, que podem ser executados em plataformas diferentes e mantidos de forma independente. Isso pode aumentar a flexibilidade, a modularidade e a escalabilidade. É uma abordagem usada em sistemas corporativos, como ERP e CRM, nos quais diferentes componentes podem se comunicar por meio de middleware e acessar serviços ou bancos de dados distintos.

# Exercícios

**2.12 Pense nos diferentes usuários do banco de dados mostrado na Figura 1.2. De que tipos de aplicações cada usuário precisaria? A que categoria de usuário cada um pertenceria e de que tipo de interface precisaria?**

- **Secretaria ou registro acadêmico** (**usuário paramétrico**): matricular alunos, lançar notas e gerar históricos. Essas tarefas podem ser executadas por meio de transações programadas e de uma **interface baseada em formulários**.
- **Professor** (**usuário casual**): consultar a lista de alunos e as notas das próprias turmas. Poderia usar uma **interface de menu** ou um formulário de consulta.
- **Aluno** (**usuário casual**): consultar o próprio histórico e os pré-requisitos das disciplinas por meio de um portal Web, com **menus e formulários**.
- **Coordenador de curso ou analista** (**usuário sofisticado**): gerar relatórios estatísticos e analisar taxas de aprovação. Poderia utilizar ferramentas de relatórios ou uma **linguagem de consulta**, como SQL.
- **DBA (administrador do banco de dados):** criar contas, definir permissões de acesso às tabelas de alunos e notas e executar tarefas administrativas. Precisaria de uma **interface administrativa** com comandos privilegiados.

**2.13 Escolha uma aplicação de banco de dados com a qual você esteja acostumado. Crie um esquema e mostre um exemplo de banco de dados para essa aplicação, usando a notação das Figuras 1.2 e 2.1. Que tipos de informações e restrições adicionais você gostaria de representar no esquema? Pense nos diversos usuários do banco de dados e projete uma visão para cada tipo.**

## Banco de dados de uma biblioteca

Os CPFs abaixo são valores fictícios de teste, usados apenas para ilustrar o formato e a restrição de unicidade. Eles não são CPFs reais validados. Os valores `—` nas colunas indicam informações ainda não preenchidas; em uma implementação do banco, devem ser representadas como valores ausentes (`NULL`), e não como o caractere `—`.

**CAD_CLIENTE**

| id_cliente (PK) | nome_completo | cpf (único) | idade | endereco |
|---:|---|---|---:|---|
| 1 | Andre de Sousa Lima | 00000000001 | 19 | Rua 20, Q 43 B 31, Parque do Sol |
| 2 | Miranda Mariane Marlei | 00000000002 | 31 | Rua 78, Q 92 L 21, Miguelangelo |
| 3 | Carlos Eduardo Martins | 00000000003 | 25 | Rua das Flores, 120, Centro |
| 4 | Juliana Ferreira Costa | 00000000004 | 22 | Avenida Brasil, 450, Jardim América |
| 5 | Rafael Oliveira Santos | 00000000005 | 35 | Rua das Palmeiras, 80, Boa Vista |

**Restrições sugeridas:** `id_cliente` é a chave primária; `cpf` deve ser obrigatório e único; `nome_completo` não pode ficar vazio; `idade` deve ser maior que zero. Para um sistema real, é preferível armazenar a data de nascimento em vez da idade, pois a idade muda com o tempo.

 **LIVRO**

| id_livro (PK) | nome_livro                       | ano_lancamento | categoria           | quantidade_exemplares | ISBN (único)  | editora                                                                                                                                                  |
| ------------- | -------------------------------- | -------------- | ------------------- | --------------------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1             | Dom Casmurro                     | 1899           | Romance             | 3                     | 9788582850350 | Penguin-Companhia<br><br>![](https://www.google.com/s2/favicons?domain=https://www.companhiadasletras.com.br&sz=32)<br><br>Grupo Companhia das Letras    |
| 2             | O Alienista                      | 1882           | Ficção              | 2                     | 9788577153213 | Hedra<br><br>![](https://www.google.com/s2/favicons?domain=https://www.hedra.com.br&sz=32)<br><br>Hedra Editora                                          |
| 3             | A Hora da Estrela                | 1977           | Romance             | 3                     | 9786555320350 | Rocco<br><br>![](https://www.google.com/s2/favicons?domain=https://rocco.com.br&sz=32)<br><br>Editora Rocco                                              |
| 4             | O Pequeno Príncipe               | 1943           | Literatura infantil | 4                     | 9788595081512 | HarperCollins Brasil<br><br>![](https://www.google.com/s2/favicons?domain=https://harpercollins.com.br&sz=32)<br><br>HarperCollins Brasil                |
| 5             | 1984                             | 1949           | Ficção distópica    | 2                     | 9788535914849 | Companhia das Letras<br><br>![](https://www.google.com/s2/favicons?domain=https://www.companhiadasletras.com.br&sz=32)<br><br>Grupo Companhia das Letras |
| 6             | Harry Potter e a Pedra Filosofal | 1997           | Fantasia            | 3                     | 9788532511010 | Rocco<br><br>![](https://www.google.com/s2/favicons?domain=https://rocco.com.br&sz=32)<br><br>Editora Rocco                                              |
| 7             | Capitães da Areia                | 1937           | Romance             | 2                     | 9788535911695 | Companhia das Letras<br><br>![](https://www.google.com/s2/favicons?domain=https://www.companhiadasletras.com.br&sz=32)<br><br>Grupo Companhia das Letras |
| 8             | O Hobbit                         | 1937           | Fantasia            | 3                     | 9788595084742 | HarperCollins Brasil                                                                                                                                     |

**Restrições sugeridas:** `id_livro` é a chave primária; o ISBN, quando informado, deve ser único; `quantidade_exemplares` não pode ser negativa. O ISBN depende da edição específica do livro, por isso deve ser preenchido com os dados da edição que a biblioteca realmente possui.

**AUTOR**

| id_autor (PK) | nome_completo |
|---:|---|
| 1 | Machado de Assis |
| 2 | Clarice Lispector |
| 3 | Antoine de Saint-Exupéry |
| 4 | George Orwell |
| 5 | J. K. Rowling |
| 6 | Jorge Amado |
| 7 | J. R. R. Tolkien |

**LIVRO_AUTOR**

Esta tabela associativa representa o relacionamento entre livros e autores. Ela permite que um livro tenha mais de um autor e que um autor esteja relacionado a vários livros.

| id_livro (PK, FK) | id_autor (PK, FK) |
|---:|---:|
| 1 | 1 |
| 2 | 1 |
| 3 | 2 |
| 4 | 3 |
| 5 | 4 |
| 6 | 5 |
| 7 | 6 |
| 8 | 7 |

A chave primária de `LIVRO_AUTOR` é composta por `id_livro` e `id_autor`. Os dois campos também são chaves estrangeiras para as tabelas `LIVRO` e `AUTOR`, respectivamente.

**EMPRESTIMO**

| id_emprestimo (PK) | id_cliente (FK) | id_livro (FK) | data_inicial | data_prevista_devolucao | data_devolucao |
|---:|---:|---:|---|---|---|
| 1 | 1 | 1 | 2026-10-01 | 2026-10-15 | — |
| 2 | 2 | 3 | 2026-10-02 | 2026-10-16 | — |
| 3 | 3 | 5 | 2026-10-03 | 2026-10-17 | — |
| 4 | 4 | 4 | 2026-10-04 | 2026-10-18 | — |
| 5 | 5 | 6 | 2026-10-05 | 2026-10-19 | — |
| 6 | 1 | 2 | 2026-10-06 | 2026-10-20 | — |
| 7 | 3 | 8 | 2026-10-07 | 2026-10-21 | — |
| 8 | 2 | 7 | 2026-10-08 | 2026-10-22 | — |

**Restrições sugeridas:** `id_emprestimo` é a chave primária; `id_cliente` e `id_livro` são chaves estrangeiras; a data prevista de devolução não pode ser anterior à data inicial; e a data efetiva da devolução, quando informada, não pode ser anterior à data do empréstimo. Todo empréstimo deve estar associado a um cliente e a um livro existentes. O sistema também deve impedir novos empréstimos quando não houver exemplares disponíveis.

**FUNCIONARIO**

| id_funcionario (PK) | nome_completo | cpf (único) | cargo | salario |
|---:|---|---|---|---:|
| 1 | Fernanda Alves Ribeiro | 00000000006 | Bibliotecária | 3200.00 |
| 2 | Marcos Vinicius Pereira | 00000000007 | Auxiliar de biblioteca | 2100.00 |
| 3 | Beatriz Souza Mendes | 00000000008 | Gerente | 4500.00 |
| 4 | Pedro Henrique Carvalho | 00000000009 | Atendente | 1900.00 |
| 5 | Camila Rodrigues Lima | 00000000010 | Bibliotecária | 3300.00 |

**Restrições sugeridas:** `id_funcionario` é a chave primária; `cpf` deve ser obrigatório e único; `nome_completo` e `cargo` são obrigatórios; e `salario` não pode ser negativo.

Visões e permissões por tipo de usuário

- **Bibliotecário:** pode cadastrar clientes, registrar empréstimos e devoluções e consultar os empréstimos e a disponibilidade dos livros.
- **Atendente:** pode consultar o catálogo, a quantidade de exemplares e a disponibilidade dos livros. A permissão para alterar dados deve ser limitada às tarefas necessárias ao cargo.
- **Gerente:** pode consultar relatórios e administrar os dados dos funcionários, conforme as permissões concedidas.

Essas visões podem ser implementadas com *views* e permissões específicas do SGBD, de modo que cada perfil acesse apenas os dados e as operações necessários às suas funções.

**2.14 Se você estivesse projetando um sistema baseado na Web para fazer reservas e vender passagens aéreas, qual arquitetura de SGBD escolheria, com base na Seção 2.5? Por quê? Por que as outras arquiteturas não seriam uma boa escolha?**

Eu escolheria uma **arquitetura de três camadas ou de n camadas**, pois ela permite separar a interface do usuário, a lógica de negócio e o acesso ao banco de dados. Essa separação facilita a manutenção, favorece a escalabilidade e permite centralizar controles de segurança na camada intermediária. À medida que o número de usuários e de solicitações aumenta, os componentes podem ser ajustados ou distribuídos conforme a necessidade.

Uma arquitetura cliente/servidor de duas camadas pode ser adequada para sistemas menores, mas tende a deixar mais lógica da aplicação no cliente e pode exigir conexões mais diretas com o banco de dados. Isso pode dificultar a manutenção e o controle de acesso em uma aplicação Web de grande porte. A arquitetura centralizada, por sua vez, pode ser menos adequada quando há muitos usuários remotos e necessidade de distribuir o processamento. Isso não significa que essas arquiteturas não possam oferecer segurança; elas apenas podem ser menos convenientes para os requisitos descritos.

**2.15 Considere a Figura 2.1. Além das restrições que relacionam os valores das colunas de uma tabela às colunas de outra tabela, existem restrições que limitam os valores de uma coluna ou de uma combinação de colunas da mesma tabela. Uma dessas restrições exige que uma coluna, ou um grupo de colunas, tenha valores exclusivos em todas as linhas. Por exemplo, na tabela ALUNO, a coluna `Numero_aluno` deve ser exclusiva para impedir que dois alunos tenham o mesmo número. Identifique a coluna ou o grupo de colunas das outras tabelas que deve ter valores exclusivos em todas as linhas.**

- **ALUNO:** `Numero_aluno`.
- **DISCIPLINA:** `Numero_disciplina`.
- **TURMA:** `Identificador_turma`.
- **REGISTRO_NOTA:** combinação de `Numero_aluno` e `Identificador_turma`.
- **PRE_REQUISITO:** combinação de `Numero_disciplina` e `Numero_pre_requisito`.

