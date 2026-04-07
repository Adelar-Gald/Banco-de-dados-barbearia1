# Projeto de Banco de Dados - Barbearia (Modelo Lógico)

## Descrição do Projeto

Este projeto apresenta a **modelagem lógica** de um banco de dados para uma barbearia/salão, desenvolvido com base no Tema 3 da disciplina. O modelo foi criado a partir da análise e correção de um modelo conceitual inicial, transformando-o em um modelo lógico completo, com tabelas, chaves primárias, chaves estrangeiras e tipos de dados adequados.

O objetivo é estruturar as principais informações do sistema, permitindo o cadastro de clientes, o registro de agendamentos, a definição dos serviços oferecidos e a relação entre profissionais e serviços executados.

---

## Objetivo do Banco de Dados

O objetivo deste banco de dados é organizar e gerenciar as informações essenciais para o funcionamento de uma barbearia, facilitando:

- Cadastro de clientes com nome e WhatsApp;
- Controle de agendamentos com data e hora;
- Registro dos serviços oferecidos (descrição, preço e duração);
- Identificação dos profissionais e suas comissões;
- Relacionamento entre profissionais e os serviços que cada um pode executar.

---

## Regras de Negócio

As principais regras de negócio consideradas neste projeto são:

1. **Um cliente pode realizar vários agendamentos.**
2. **Cada agendamento pertence a um único cliente.**
3. **Cada agendamento registra apenas um serviço.**
4. **Um mesmo tipo de serviço pode aparecer em vários agendamentos.**
5. **Um profissional pode executar vários serviços.**
6. **Um mesmo serviço pode ser executado por vários profissionais.**

---

## Modelo Lógico (Estrutura das Tabelas)

### Tabela: CLIENTE
| Campo | Tipo | Descrição |
|-------|------|------------|
| id_cliente | INT (PK) | Identificador único do cliente |
| nome | VARCHAR(100) | Nome do cliente |
| whatsapp | VARCHAR(20) | Número de WhatsApp |

### Tabela: SERVICO
| Campo | Tipo | Descrição |
|-------|------|------------|
| id_servico | INT (PK) | Identificador único do serviço |
| descricao | VARCHAR(100) | Descrição do serviço (Corte, Barba, Pintura) |
| preco | DECIMAL(10,2) | Preço do serviço |
| duracao | INT | Duração em minutos |

### Tabela: PROFISSIONAL
| Campo | Tipo | Descrição |
|-------|------|------------|
| id_profissional | INT (PK) | Identificador único do profissional |
| nome | VARCHAR(100) | Nome do profissional |
| comissao | DECIMAL(5,2) | Percentual de comissão |

### Tabela: AGENDAMENTO
| Campo | Tipo | Descrição |
|-------|------|------------|
| id_agendamento | INT (PK) | Identificador único do agendamento |
| data | DATE | Data do agendamento |
| hora | TIME | Horário do agendamento |
| id_cliente | INT (FK) | Referência ao cliente |
| id_servico | INT (FK) | Referência ao serviço |

### Tabela: PROFISSIONAL_SERVICO (associativa)
| Campo | Tipo | Descrição |
|-------|------|------------|
| id_profissional | INT (PK, FK) | Referência ao profissional |
| id_servico | INT (PK, FK) | Referência ao serviço |

---

## Relacionamentos e Cardinalidades

| Relacionamento | Cardinalidade | Explicação |
|----------------|---------------|-------------|
| CLIENTE → AGENDAMENTO | 1 : N | Um cliente pode fazer vários agendamentos |
| AGENDAMENTO → SERVICO | N : 1 | Vários agendamentos podem registrar o mesmo serviço |
| PROFISSIONAL ↔ SERVICO | N : N | Um profissional faz vários serviços; um serviço é feito por vários profissionais |

---

## Ferramentas Utilizadas

- **Visual Studio Code (VS Code)** como ambiente de edição do arquivo do diagrama;
- **Extensão PlantUML** no VS Code para modelagem e geração do diagrama lógico;
- **GitHub** para hospedagem do repositório e entrega da atividade.

---

## Arquivos do Repositório

Este repositório contém os seguintes arquivos:

- `README.md` → Documentação completa do projeto
- `modelo_logico_barbearia.puml` → Código fonte do diagrama em PlantUML
- `modelo_logico_barbearia.png` → Imagem do diagrama lógico gerada

---

## Diagrama do Projeto

![Diagrama Lógico Barbearia](02_modelo_logico_barbearia.png)

---

## Autor

Projeto desenvolvido para atividade acadêmica da disciplina de Banco de Dados.

Baseado no Tema 3 – Gerenciamento de Barbearia/Salão.
