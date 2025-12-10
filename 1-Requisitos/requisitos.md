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

> Como **usuário autenticado**, quero **criar um ciclo de estudo selecionando um edital disponível**, definindo nome e período (data início/fim) para **organizar melhor meu tempo de preparação**.

**Critérios de Aceite:**

- Usuário seleciona edital de uma lista
- Usuário informa nome do ciclo (máx. 100 caracteres)
- Data fim deve ser posterior à data início
- Ciclo aparece na lista "Meus Ciclos" após criação
- Sistema exibe mensagem de sucesso

### 2. Definição de Pesos

> Como **usuário autenticado**, quero **atribuir pesos de 1 a 10 às disciplinas do meu ciclo** para **priorizar matérias mais importantes ou difíceis**.

**Critérios de Aceite:**

- Usuário seleciona disciplina de uma lista
- Usuário atribui um peso de 1 a 10 para essa disciplina via slider ou input numérico
- O peso padrão é 5
- O sistema recalcula a distribuição de horas entre as disciplinas após o usuário salvar todos os pesos atribuídos

### 3. Registro de Sessões

> Como **usuário autenticado**, quero **registrar sessões de estudo informando disciplina, data e duração(horas:minutos)** para **acompanhar meu progresso**.

**Critérios de Aceite:**

- Usuário seleciona disciplina do ciclo ativo
- Usuário informa data e duração(horas:minutos) via input de tempo
- Data não pode ser futura
- Duração mínima: 10 minutos; Duração máxima: 12 horas
- Total de horas da disciplina é atualizado após registro da sessão

### 4. Visualização de Progresso

> Como **usuário autenticado**, quero **visualizar dashboard com gráfico de pizza (horas por disciplina), gráfico de linha (evolução semanal) e indicadores de meta** para **identificar pontos fracos e fortes**.

**Critérios de Aceite:**

- Gráfico de pizza mostra % de horas por disciplina
- Gráfico de linha mostra evolução semanal de horas por disciplina
- Indicadores de meta mostram horas estudadas vs. meta do ciclo
- Filtros por ciclo e por período

### 5. Gerenciamento de Editais

> Como **administrador**, quero **gerenciar editais informando nome, órgão, data da prova e lista de disciplinas/tópicos** para **disponibilizar novos concursos aos usuários**.

**Critérios de Aceite:**

- Campos obrigatórios: nome, órgão, data da prova
- Admin pode adicionar N disciplinas com seus tópicos
- Admin pode editar e excluir editais
- Edital fica disponível para usuários após publicação
- Admin pode editar/excluir editais não vinculados a ciclos ativos

### 6. Controle de Acesso

> Como **visitante**, quero **me cadastrar com login e senha**, e fazer login para acessar o sistema de forma segura.

**Critérios de Aceite:**

- Cadastro exige email válido e senha conforme RF01
- Email duplicado exibe erro específico
- Login com credenciais inválidas exibe "Email ou senha incorretos"
- Após 5 tentativas falhas, conta é bloqueada por 30 minutos
- Token JWT expira em 24h e usuário é redirecionado ao login

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

| Código   | Descrição                                                                                                                                                                              |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **RF01** | O sistema deve permitir cadastro com email, senha (mín. 8 caracteres, 1 número, 1 especial, 1 letra maiúscula) e autenticação via JWT com token válido por 24h                         |
| **RF02** | O sistema deve permitir o cadastro de editais, disciplinas e tópicos pelos administradores.                                                                                            |
| **RF03** | O usuário deve poder criar ciclos de estudo baseados em editais.                                                                                                                       |
| **RF04** | O usuário deve poder definir pesos (entre 1 e 10) para as disciplinas dentro de cada ciclo, sendo 1 a menor prioridade e 10 a maior, e 5 o valor padrão.                               |
| **RF05** | O usuário deve poder registrar sessões de estudo informando dia, duração(em horas e minutos) e disciplina.                                                                             |
| **RF06** | O sistema deve calcular automaticamente o total de horas estudadas por disciplina e por ciclo.                                                                                         |
| **RF07** | O sistema deve permitir visualizar métricas, mostrando quantidade de horas estudadas por disciplina e por ciclo, e gráficos de desempenho nos simulados e provas de editais anteriores |
| **RF08** | O sistema deve permitir cadastrar provas de editais anteriores, simulados e questões múltipla escolha e discursivas.                                                                   |
| **RF09** | O sistema deve permitir filtros personalizados por data, disciplina ou ciclo.                                                                                                          |

---

## 🔒 Requisitos Não Funcionais

| Código    | Descrição                                                                       |
| --------- | ------------------------------------------------------------------------------- |
| **RNF01** | O sistema deve ser responsivo em dispositivos móveis e acessível(padrões WCAG). |
| **RNF02** | As operações devem ser realizadas em até 2 segundos em condições normais.       |
| **RNF03** | O sistema deve armazenar dados em banco de dados relacional.                    |
| **RNF04** | A API deve seguir arquitetura RESTful.                                          |
| **RNF05** | O frontend deve utilizar framework moderno (React, Angular, Vue).               |
| **RNF06** | Os dados devem ser persistidos com integridade referencial.                     |
| **RNF07** | O sistema deve registrar logs em formato JSON contendo timestamp,               |
|           | user_id, ação e resultado para: autenticação (login/logout/falhas),             |
|           | operações CRUD de editais e erros de sistema. Logs devem ser                    |
|           | retidos por 90 dias.                                                            |
