# Capítulo 1 — Bancos de Dados e Usuários de Banco de Dados

---

## PARTE 1 — CONCEITOS ESSENCIAIS PARA MEMORIZAR

### Definições-chave
- **Dados**: fatos conhecidos que podem ser registrados e que possuem significado implícito.
- **Banco de dados**: coleção de dados relacionados, com um significado implícito.
- **Minimundo (ou Universo de Discurso — UoD)**: o pedaço do mundo real que o banco de dados representa. Mudanças no minimundo devem se refletir no banco de dados.
- **SGBD (Sistema Gerenciador de Banco de Dados / DBMS)**: coleção de programas de uso geral que permite **criar e manter** um banco de dados — ou seja, definir, construir, manipular e compartilhar dados entre vários usuários e aplicações.
- **Sistema de banco de dados** = Banco de dados + software de SGBD (a união dos dois).
- **Catálogo / dicionário de dados**: onde o SGBD armazena a definição/descrição do banco de dados (a estrutura de cada arquivo, tipo e formato de cada item de dado, restrições). Essa informação é chamada de **metadados**.
- **Programa de aplicação**: acessa o banco de dados enviando consultas e solicitações ao SGBD.
- **Consulta**: normalmente resulta na recuperação de dados, sem alterá-los.
- **Transação**: programa em execução (ou processo) que inclui um ou mais acessos ao banco de dados, podendo envolver leitura e gravação.

### As 3 propriedades que tornam um banco de dados "banco de dados" (e não só "dados")
1. Representa algum aspecto do minimundo — mudanças nele se refletem no BD.
2. É uma coleção **logicamente coerente** de dados com significado inerente (dados aleatórios não formam um banco de dados).
3. É **projetado, construído e populado** com uma finalidade específica, para um grupo de usuários e aplicações previamente concebidos.

### As 4 ações/funções que um SGBD deve prover (ligado ao termo "definir, construir, manipular, compartilhar")
- **Definir**: especificar tipos, estruturas e restrições dos dados.
- **Construir**: processo de armazenar os dados em um meio controlado pelo SGBD.
- **Manipular**: consultar, atualizar, gerar relatórios.
- **Compartilhar**: permitir que vários usuários/programas acessem o BD simultaneamente.

### As 4 características da abordagem de banco de dados (fundamental — cai direto na prova)
1. **Natureza de autodescrição** — o catálogo guarda os metadados (estrutura + restrições).
2. **Isolamento entre programas e dados + abstração de dados** — a estrutura dos dados fica no catálogo, não embutida no programa (→ **independência de dados**); o **modelo de dados** é o que permite essa abstração.
3. **Suporte a múltiplas visões (views)** dos dados — cada usuário pode ter uma visão diferente/parcial do BD.
4. **Compartilhamento de dados e processamento de transação multiusuário** — exige **controle de concorrência**, com as propriedades de **isolamento** (cada transação executa como se fosse a única) e **atomicidade** (todas as operações da transação ocorrem ou nenhuma ocorre). Chamado de **OLTP** (On-Line Transaction Processing).

### Atores em cena (quem trabalha com o BD)
- **DBA (Administrador de banco de dados)**: autoriza acesso, coordena e monitora o uso, adquire recursos de hardware/software, resolve problemas de segurança e desempenho.
- **Projetistas de banco de dados**: identificam os dados a armazenar, escolhem estruturas apropriadas, conversam com os usuários **antes** do BD existir, criam as visões de cada grupo.
- **Usuários finais** (4 tipos — ver Parte 2, questão 1.5).
- **Analistas de sistemas / programadores de aplicações**: analistas levantam necessidades dos usuários finais; programadores implementam essas especificações como programas (transações programadas).

### Trabalhadores dos bastidores (não usam o conteúdo do BD diretamente)
- Projetistas e implementadores do **SGBD em si** (módulos internos).
- **Desenvolvedores de ferramentas** (softwares opcionais: modelagem, desempenho, GUIs, geração de dados de teste).
- **Operadores e pessoal de manutenção** (hardware/software do ambiente).

### As 10 vantagens de usar um SGBD (memorizar pelo menos os nomes)
1. Controle da redundância (→ **normalização**).
2. Restrição de acesso não autorizado (segurança).
3. Armazenamento persistente para objetos de programa.
4. Estruturas de armazenamento e pesquisa eficientes (**índices**).
5. Backup e recuperação.
6. Múltiplas interfaces de usuário.
7. Representação de relacionamentos complexos.
8. Imposição de restrições de integridade.
9. Dedução e ações usando regras (**gatilhos/triggers**, **procedimentos armazenados**).
10. Padronização, menor tempo de desenvolvimento, flexibilidade, dados sempre atualizados, economia de escala.

### Quando NÃO usar um SGBD
- Aplicações simples e estáveis (sem mudanças esperadas).
- Requisitos rígidos de tempo real.
- Sistemas embarcados com pouco espaço de armazenamento.
- Sem necessidade de acesso multiusuário.