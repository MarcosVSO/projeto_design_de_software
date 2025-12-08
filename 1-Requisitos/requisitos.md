# 🧭 Sistema de Gerenciamento de Ciclos de Estudo

## 📘 Contexto

Com o aumento constante na publicação de **editais de concursos, vestibulares e ENEM**, muitos candidatos encontram dificuldades para organizar sua rotina de estudos.  
Cada edital traz uma lista extensa de conteúdos — disciplinas comuns e específicas — tornando o **planejamento e a priorização das matérias** um grande desafio.

---

## 🎯 Proposta

Desenvolver um **sistema de gerenciamento de ciclos de estudo** baseado em editais publicados.

A ferramenta permitirá que o usuário:

- Defina **pesos** para disciplinas consideradas mais difíceis ou prioritárias;
- **Acompanhe** o total de horas dedicadas a cada matéria;
- **Visualize métricas de desempenho** em um dashboard interativo;
- **Aplique filtros personalizados** para ajustar e monitorar seu plano de estudos.

---

## 🧩 Histórias de Usuário

### 1. Criação de Ciclo de Estudo

> Como **usuário**, quero **criar um ciclo de estudo baseado em um edital** para **organizar melhor meu tempo de preparação**.

### 2. Definição de Pesos

> Como **usuário**, quero **atribuir pesos às disciplinas** para **priorizar matérias mais importantes ou difíceis**.

### 3. Registro de Sessões

> Como **usuário**, quero **registrar sessões de estudo com data e duração** para **acompanhar meu progresso**.

### 4. Visualização de Progresso

> Como **usuário**, quero **ver gráficos e métricas** do meu desempenho **para identificar pontos fracos e fortes**.

### 5. Gerenciamento de Editais

> Como **administrador**, quero **cadastrar, editar e excluir editais** para **disponibilizar novos concursos e provas**.

### 6. Controle de Acesso

> Como **usuário**, quero **acessar o sistema com login e senha** para **proteger meus dados pessoais e históricos**.

---

## ⚙️ Casos de Uso Principais

1. Cadastrar Usuário
2. Autenticar Usuário
3. Cadastrar Edital
4. Criar Ciclo de Estudo
5. Definir Pesos das Disciplinas
6. Registrar Sessão de Estudo
7. Consultar Progresso
8. Visualizar Estatísticas e Gráficos
9. Cadastrar Questões e Simulados
10. Consultar Editais

---

## 📋 Requisitos Funcionais

| Código   | Descrição                                                                                      |
| -------- | ---------------------------------------------------------------------------------------------- |
| **RF01** | O sistema deve permitir o cadastro e autenticação de usuários.                                 |
| **RF02** | O sistema deve permitir o cadastro de editais, disciplinas e tópicos.                          |
| **RF03** | O usuário deve poder criar ciclos de estudo baseados em editais.                               |
| **RF04** | O usuário deve poder definir pesos para as disciplinas dentro de cada ciclo.                   |
| **RF05** | O usuário deve poder registrar sessões de estudo informando data, duração e disciplina.        |
| **RF06** | O sistema deve calcular automaticamente o total de horas estudadas por disciplina e por ciclo. |
| **RF07** | O sistema deve permitir visualizar métricas e gráficos de desempenho.                          |
| **RF08** | O sistema deve permitir cadastrar provas, simulados e questões.                                |
| **RF09** | O sistema deve gerar estatísticas de desempenho geral e por disciplina.                        |
| **RF10** | O sistema deve permitir filtros personalizados por data, disciplina ou ciclo.                  |

---

## 🔒 Requisitos Não Funcionais

| Código    | Descrição                                                                 |
| --------- | ------------------------------------------------------------------------- |
| **RNF01** | O sistema deve ser responsivo e acessível em dispositivos móveis.         |
| **RNF02** | As operações devem ser realizadas em até 2 segundos em condições normais. |
| **RNF03** | O sistema deve armazenar dados em banco de dados relacional.              |
| **RNF04** | A API deve seguir arquitetura RESTful.                                    |
| **RNF05** | O frontend deve utilizar framework moderno (React, Angular, Vue).         |
| **RNF06** | Os dados devem ser persistidos com integridade referencial.               |
| **RNF07** | Deve haver logs de autenticação e eventos importantes.                    |
