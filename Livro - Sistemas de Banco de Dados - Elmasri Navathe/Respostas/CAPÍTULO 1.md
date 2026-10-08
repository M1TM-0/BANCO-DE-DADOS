# Perguntas de Revisão

**1.1 Defina os seguintes termos: dados, banco de dados, SGBD, sistema de banco de dados, catálogo de banco de dados, independência entre dados e programas, visão do usuário, DBA, usuário final, transação programada, sistema de banco de dados dedutivo, objeto persistente, metadados e aplicação de processamento de transação.**

- **Dados:** fatos conhecidos que podem ser registrados e que possuem significado implícito.

- **Banco de dados:** coleção de dados relacionados, com um significado implícito.

- **SGBD:** coleção de programas de uso geral que permite criar e manter um banco de dados, ou seja, definir, construir, manipular e compartilhar dados entre vários usuários e aplicações.

- **Sistema de banco de dados:** conjunto formado pelo banco de dados, pelo SGBD e pelos usuários/aplicações que o utilizam.

- **Catálogo de banco de dados:** local onde o SGBD armazena a definição/descrição do banco de dados (a estrutura de cada arquivo, o tipo e o formato de cada item de dado e as restrições). Essas informações são chamadas de metadados.

- **Independência entre dados e programas:** significa que o esquema/estrutura dos dados é definido no SGBD (catálogo/dicionário de dados) e não fica “amarrado” ao código da aplicação. Assim, mudanças na estrutura dos dados podem ocorrer com menor impacto nos programas.

- **Visão do usuário (view):** parte dos dados ou representação dos dados que um usuário vê; é uma visão externa derivada do banco, não um “resultado de consulta armazenado”.

- **DBA (Administrador de Banco de Dados):** autoriza acessos, coordena e monitora o uso, adquire recursos de hardware/software e resolve problemas de segurança e desempenho.

- **Usuários finais:** são pessoas cujas funções exigem acesso ao banco de dados para consulta, atualização e geração de relatórios; o banco de dados existe principalmente para seu uso.

- **Transações programadas:** tipos padrão de consultas e atualizações que foram cuidadosamente programadas e testadas.

- **Sistema de banco de dados dedutivo:** são sistemas de banco de dados que oferecem a capacidade de definir regras de dedução a fim de inferir novas informações com base nos fatos armazenados no banco de dados.

- **Objeto persistente:** um objeto é considerado persistente quando sobrevive ao término da execução e pode ser recuperado mais tarde diretamente por outro programa.

- **Metadados:** informações armazenadas no catálogo, como descrição de construções e restrições do esquema.

- **Aplicação de processamento de transação:** aplicação que executa transações curtas e frequentes, garantindo correção e consistência mesmo com concorrência.


**1.2 Quais os quatro tipos principais de ações que envolvem bancos de dados? Discuta cada tipo brevemente.**

**Definir:** especificar tipos, estruturas e restrições de dados.

**Construir:** processo de armazenar os dados em um meio controlado pelo SGBD.

**Manipular:** consultar, atualizar e gerar relatórios.

**Compartilhar:** permitir que vários usuários/programas acessem o BD simultaneamente.

**1.3 Discuta as principais características da abordagem de banco de dados e como ela difere dos sistemas de arquivo tradicionais.**

No processamento tradicional em arquivos, cada usuário ou departamento criava e mantinha seus próprios arquivos. Isso gerava redundância, inconsistência e falta de independência entre dados e programas, porque mudanças na estrutura dos arquivos exigiam mudanças nos programas. A abordagem de banco de dados resolve isso com estas características principais:

- **Natureza de autodescrição:** o catálogo armazena os metadados.

- **Independência entre programas e dados / abstração de dados:** a estrutura dos dados fica no catálogo, não embutida no programa.

- **Suporte a múltiplas visões dos dados:** cada usuário pode ver uma parte diferente do banco.

- **Compartilhamento de dados e processamento multiusuário:** exige controle de concorrência para garantir isolamento e atomicidade nas transações.


**1.4 Quais são as responsabilidades do DBA e dos projetistas do banco de dados?**

- **DBA:** autoriza acessos, coordena e monitora o uso, adquire recursos de hardware/software e resolve problemas de segurança e desempenho.

- **Projetista de banco de dados:** identifica os dados a armazenar, escolhe estruturas apropriadas, conversa com os usuários antes de o BD existir e cria as visões de cada grupo.


**1.5 Quais são os diferentes tipos de usuários finais do banco de dados?**

- **Usuários finais casuais:** acessam o banco ocasionalmente e geralmente usam uma interface de consulta para obter informações diferentes a cada vez.

- **Usuários finais iniciantes ou paramétricos:** executam tarefas repetitivas, consultando e atualizando o banco com transações programadas.

- **Usuários finais sofisticados:** engenheiros, cientistas, analistas e outros que conhecem bem as facilidades do SGBD e criam suas próprias aplicações.

- **Usuários autônomos/independentes:** mantêm bancos de dados pessoais usando pacotes prontos, com interface por menus ou gráficos.


**1.6 Discuta as capacidades que devem ser fornecidas por um SGBD.**

- Controle de redundância de dados.

- Restrição do acesso não autorizado.

- Armazenamento persistente de objetos do programa.

- Estruturas de armazenamento e técnicas de pesquisa para o processamento eficiente de consultas.

- Backup e recuperação de dados.

- Múltiplas interfaces para diferentes usuários.

- Representação de relacionamentos complexos entre os dados.

- Imposição de restrições de integridade.

- Suporte à dedução de informações e à execução de ações por meio de regras e gatilhos (triggers).

- Padronização, menor tempo de desenvolvimento, flexibilidade, dados sempre atualizados e economia de escala.

**1.7 Discuta as diferenças entre sistemas de banco de dados e sistemas de recuperação de informações.**

- **Banco de dados:** aplica-se a dados estruturados e formatados (ex.: manufatura, varejo, bancos, seguros, finanças, saúde — formulários, faturas, registros de pacientes).

- **Recuperação de Informações (RI):** lida com dados menos estruturados — manuscritos e documentos baseados em texto livre (livros, artigos de biblioteca). O dado é indexado/catalogado/anotado por palavras-chave, e a busca é feita por conteúdo, com base nessas palavras-chave (busca em texto livre, localização de documentos por tópico), e não por uma estrutura fixa de registros como no BD.

# Exercícios

**1.8 Identifique algumas operações informais de consulta e atualização que você esperaria aplicar ao banco de dados mostrado na Figura 1.2.**

**Consultas:**

- Quantidade de alunos por curso.
- Professor responsável por uma disciplina.
- Pré-requisitos de uma disciplina.
- Notas de um aluno.

**Atualizações:**

- Alterar tipo/ano de um aluno.
- Criar novas turmas.
- Inserir notas.

**1.9 Qual é a diferença entre redundância controlada e não controlada?**

**Redundância controlada:** o mesmo dado é duplicado propositalmente (geralmente por desempenho, para evitar buscas ou junções repetidas), mas o SGBD verifica automaticamente se os valores duplicados continuam consistentes com a fonte original.

**Redundância não controlada:** o mesmo dado é armazenado em mais de um lugar e pode ficar inconsistente, pois nada garante que uma atualização em um lugar seja replicada nos outros.

- A diferença não é se existe cópia duplicada, e sim se o sistema garante ou não a consistência dessa cópia.

**1.10 Especifique todos os relacionamentos entre os registros do banco de dados mostrado na Figura 1.2.**

`ALUNO <-> REGISTRO_NOTA`: por meio do `Numero_aluno`.

`TURMA <-> REGISTRO_NOTA`: por meio do `Identificador_turma`.

`DISCIPLINA <-> TURMA`: por meio do `Numero_disciplina`.

`DISCIPLINA <-> PRE_REQUISITO`: por meio do `Numero_disciplina`.

**1.11 Mostre algumas visões adicionais que podem ser necessárias a outros grupos de usuários para o banco de dados mostrado na Figura 1.2.**

- **Um professor:** visão com as turmas que ele leciona e os alunos/notas de cada uma.
- **A secretaria/registro acadêmico:** visão com dados cadastrais do aluno e disciplinas concluídas.
- **Um coordenador de departamento:** visão com todas as disciplinas oferecidas pelo seu departamento e em quais turmas/semestres.

**1.12 Cite alguns exemplos de restrições de integridade que você acredita que possam se aplicar ao banco de dados mostrado na Figura 1.2.**

**Restrições de tipo de dado:** `Tipo_aluno` só pode ser um número entre 1 e 5; `Nota` só pode ser um caractere entre `'A'`, `'B'`, `'C'`, `'D'` e `'F'`.

**Restrição de integridade referencial:** o `Numero_disciplina` que aparece nas tabelas `TURMA` e `PRE_REQUISITO` deve realmente existir na tabela `DISCIPLINA`.

**Restrição de chave/singularidade:**

`Numero_disciplina` e `Numero_aluno` devem ser únicos.

**1.13 Dê exemplos de sistemas nos quais pode fazer sentido usar o processamento de arquivos tradicional em vez da abordagem de banco de dados.**

- Em aplicações simples e estáveis (sem mudanças esperadas).
- Requisitos rígidos de tempo real.
- Sistemas embarcados com pouco espaço de armazenamento.
- Sem necessidade de acesso multiusuário.

**1.14 Considere a Figura 1.2.**

_a. Se o nome do departamento ‘CC’ (Ciência da Computação) mudar para ‘CCES’ (Ciência da Computação e Engenharia de Software) e o prefixo correspondente para o número da disciplina também mudar, identifique as colunas no banco de dados que precisariam ser atualizadas._

- `DISCIPLINA.Departamento`: alterar `CC` → `CCES`.
- `DISCIPLINA.Numero_disciplina`: alterar o prefixo `CC` → `CCES`.
- `ALUNO.Curso`: alterar `CC` → `CCES`.
- `TURMA.Numero_disciplina`: alterar o prefixo `CC` → `CCES`.
- `PRE_REQUISITO.Numero_disciplina`: alterar o prefixo `CC` → `CCES`.
- `PRE_REQUISITO.Numero_pre_requisito`: alterar o prefixo `CC` → `CCES`, quando aplicável.

_b. Você consegue reestruturar as colunas nas tabelas DISCIPLINA, TURMA e PRE_REQUISITO de modo que somente uma coluna precise ser atualizada?_

As colunas poderiam ser reestruturadas separando o departamento do número da disciplina. O departamento teria um identificador próprio, utilizado como chave estrangeira nas demais tabelas, enquanto o número da disciplina seria armazenado separadamente. Dessa forma, uma alteração no nome ou código do departamento não exigiria a alteração dos códigos das disciplinas e das referências nas outras tabelas.