# Capítulo 2 — Conceitos e Arquitetura do Sistema de Banco de Dados

### Modelo de dados, esquema e estado (Seção 2.1)
- **Abstração de dados**: supressão de detalhes de organização/armazenamento, destacando só o que é essencial para o usuário conhecer.
- **Modelo de dados**: coleção de conceitos usados para descrever a **estrutura** de um banco de dados (tipos, relacionamentos, restrições) **+** um conjunto de **operações básicas** para especificar recuperações e atualizações. Também pode incluir o **aspecto dinâmico/comportamento** (operações definidas pelo usuário, ex.: `CALCULA_MEDIA`).
- **3 categorias de modelos de dados**:
  1. **Alto nível / conceituais** — próximos de como o usuário percebe os dados: usam **entidade** (objeto do mundo real), **atributo** (propriedade que descreve a entidade) e **relacionamento** (associação entre entidades). Ex.: modelo Entidade-Relacionamento.
  2. **Baixo nível / físicos** — descrevem como os dados são armazenados no computador (discos).
  3. **Representativos (de implementação)** — meio-termo, entendidos pelo usuário final mas próximos de como o SGBD organiza os dados. Ex.: **modelo relacional** (o mais usado nos SGBDs comerciais), e os legados **modelo de rede** e **hierárquico**.
  - O **modelo de dados de objeto** é uma família mais recente e de nível mais alto que os representativos tradicionais, mais próxima dos modelos conceituais (padrão **ODMG**).
- **Caminho de acesso**: estrutura (ex.: **índice**) que torna eficiente a busca por registros de um banco de dados físico.
- **Esquema de banco de dados**: a **descrição** do banco de dados (especificada no projeto; não muda com frequência). Representado visualmente por um **diagrama de esquema**; cada objeto do diagrama é um **construtor do esquema**. O diagrama mostra só nomes de tipos de registro e itens de dados — **não** mostra restrições.
- **Estado do banco de dados** (ou **ocorrência/instância**): os **dados reais** armazenados em um dado momento — muda toda vez que há inserção, exclusão ou alteração.
  - **Estado vazio** → só esquema, sem dados. **Estado inicial** → quando o BD é populado/carregado. **Estado válido** → satisfaz a estrutura e restrições do esquema.
  - Esquema no catálogo = **metadados**; esquema também é chamado de **intenção**; estado do BD também é chamado de **extensão**.

### Arquitetura de três esquemas e independência de dados (Seção 2.2)
- Objetivo: separar as aplicações do usuário do banco de dados físico.
1. **Esquema interno**: descreve a estrutura de **armazenamento físico** (usa modelo de dados físico).
2. **Esquema conceitual**: descreve a estrutura do **BD inteiro** para toda a comunidade de usuários; oculta detalhes físicos; foco em entidades, tipos de dados, relacionamentos, operações, restrições. Normalmente descrito com um modelo de dados representativo.
3. **Esquema(s) externo(s)** (ou **visões de usuário**): cada um descreve a parte do BD que interessa a **um grupo específico** de usuários, ocultando o resto.
- Os três esquemas são só **descrições** — os dados reais só existem no **nível físico**.
- **Mapeamentos**: processos que transformam solicitações/resultados entre os níveis (mapeamento externo/conceitual e mapeamento conceitual/interno) — necessários justamente porque os três níveis são descrições separadas dos mesmos dados reais.
- **Independência lógica de dados**: capacidade de alterar o **esquema conceitual** sem alterar os esquemas externos nem os programas de aplicação (só a visão e os mapeamentos mudam).
- **Independência física de dados**: capacidade de alterar o **esquema interno** sem alterar o esquema conceitual (nem os externos) — ex.: criar novos índices para melhorar desempenho.
- A **independência lógica é mais difícil de alcançar** porque programas de aplicação costumam depender bastante da estrutura lógica dos dados que acessam; alterar essa estrutura sem quebrar os programas é um requisito muito mais rígido do que só reorganizar o armazenamento físico.
- Desvantagem da arquitetura de três esquemas: os mapeamentos geram **sobrecarga em tempo de execução** → baixa eficiência → por isso poucos SGBDs a implementam por completo.

### Linguagens do SGBD (Seção 2.3.1)
- **DDL (Data Definition Language)**: usada pelo DBA/projetistas para definir o **esquema conceitual** (e, em sistemas com separação clara, também o interno).
- **SDL (Storage Definition Language)**: especifica o **esquema interno** — na maioria dos SGBDs relacionais não existe uma linguagem separada para isso; é feito por funções/parâmetros de armazenamento.
- **VDL (View Definition Language)**: especifica as **visões (esquemas externos)** e seus mapeamentos ao esquema conceitual — na prática, a própria DDL costuma cumprir esse papel também (ex.: SQL).
- **DML (Data Manipulation Language)**: conjunto de operações para **recuperar, inserir, excluir e modificar** dados.
- Nos SGBDs atuais essas linguagens normalmente **não são distintas** — uma única linguagem integrada (como o **SQL**) cobre DDL, VDL e DML.
- **DML procedural (baixo nível)**: recupera/processa **um registro de cada vez**, precisa de laços (*looping*), deve ser embutida em uma linguagem de programação de uso geral.
- **DML não procedural (alto nível / declarativa)**: especifica **o que** recuperar (não como); recupera **um conjunto de registros de cada vez**; pode ser usada de forma independente (interativa) ou embutida. Ex.: SQL.
- Quando a DML de alto nível é usada de forma interativa, é chamada de **linguagem de consulta**.
- Linguagem em que a DML é embutida = **linguagem hospedeira**; a DML embutida nela = **sublinguagem de dados**.

### Interfaces de SGBD (Seção 2.3.2)
- **Baseadas em menu** (Web/navegação): lista de opções, sem precisar decorar sintaxe — comuns para usuários casuais.
- **Baseadas em formulário**: um formulário por tipo de consulta — muito usadas por **usuários paramétricos** (transações programadas).
- **Gráficas (GUI)**: esquema apresentado como diagrama, manipulado com mouse.
- **De linguagem natural**: aceitam pedidos em português/inglês; têm esquema próprio (dicionário de palavras).
- **De entrada/saída de voz**: uso ainda limitado, vocabulário restrito.
- **Para usuários paramétricos**: pequeno conjunto de comandos abreviados/teclas de função.
- **Para o DBA**: comandos privilegiados (criar contas, definir parâmetros, conceder autorização, alterar esquema, reorganizar armazenamento).

### Ambiente e componentes do SGBD (Seção 2.4)
- **Compilador DDL**: processa definições de esquema → armazena metadados no **catálogo**.
- **Compilador de consulta** + **otimizador de consulta**: analisam/validam a sintaxe e reorganizam a consulta (eliminando redundâncias, escolhendo algoritmos e índices) antes de executar.
- **Pré-compilador**: extrai comandos DML de um programa de aplicação, que vão para o **compilador DML**; o restante do programa vai para o compilador da linguagem hospedeira — juntos formam a **transação programada**.
- **Processador de BD em tempo de execução**: executa comandos privilegiados, planos de consulta e transações programadas, usando o catálogo, o gerenciador de dados armazenados, e (indiretamente) o sistema operacional.
- **Gerenciador de buffer / gerenciador de dados armazenados**: cuidam da leitura/escrita eficiente em disco.
- **Utilitários do banco de dados**:
  - **Carga**: importa arquivos de dados existentes para o BD.
  - **Backup**: cópia de segurança do BD (backups **incrementais** só registram mudanças desde o último backup).
  - **Reorganização do armazenamento**: reorganiza arquivos para melhorar desempenho.
  - **Monitoração de desempenho**: gera estatísticas de uso para o DBA decidir sobre reorganização/índices.
- **Outros softwares com que o SGBD interage**: **sistema operacional** (I/O em disco), **compiladores das linguagens hospedeiras**, e **software de comunicações** (para acesso remoto via rede — sistema **DB/DC** quando integrado).
- **Ferramentas CASE**, **dicionário/repositório de dados** (info de catálogo + padrões de uso + documentação) e **ambientes de desenvolvimento de aplicação** (ex.: PowerBuilder) também fazem parte do ambiente do SGBD.

### Arquiteturas centralizadas e cliente/servidor (Seção 2.5)
- **Centralizada**: todo o processamento (BD, SGBD, aplicações, interface) roda em uma única máquina; terminais antigos só exibiam informação.
- **Cliente/servidor básica**: **servidor** = hardware+software que presta serviço às máquinas **cliente** (arquivo, impressão, BD, Web, e-mail); cliente oferece interface + processamento local.
- **Duas camadas**: cliente cuida da interface/aplicação; servidor cuida do processamento de dados (ex.: SQL). Ponto de divisão lógico é a própria SQL. Padrões **ODBC** e **JDBC** permitem que o cliente se conecte a diferentes SGBDs por uma API padrão. Vantagens: simplicidade e compatibilidade com sistemas legados.
- **Três camadas**: acrescenta uma **camada intermediária** (servidor de aplicação/servidor Web) entre cliente e servidor de BD — trata regras de negócio, pode reforçar segurança (verifica credenciais antes de acessar o BD), e formata resultados para a interface do cliente. Muito usada em **aplicações Web**.
- **n camadas (n > 3)**: divide a camada de lógica de negócios em **componentes ainda mais detalhados**, cada um podendo rodar em plataforma própria e ser tratado de forma independente — usada por sistemas **ERP/CRM** com uma **camada de middleware** que conecta vários bancos de dados de back-end.

### Classificação dos SGBDs (Seção 2.6)
Critérios principais:
1. **Modelo de dados**: relacional (dominante), objeto, objeto-relacional, XML nativo, e os legados hierárquico e de rede.
2. **Número de usuários**: monousuário vs. multiusuário.
3. **Número de locais**: centralizado vs. distribuído (homogêneo ou heterogêneo); **BD federado/multibanco de dados** usa middleware para acessar BDs autônomos heterogêneos.
4. **Custo**: de código aberto/gratuito (MySQL, PostgreSQL) até licenças corporativas caras.
- Também pode ser classificado por **tipo de caminho de acesso** e por ser de **uso geral** ou **uso especial** (ex.: sistemas OLTP como reservas aéreas).

