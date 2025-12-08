# 📦 Diagrama de Container — Sistema de Gestão de Ciclos de Estudo (Modelo C4 - Nível 2)

## 1. Visão Geral

O **Diagrama de Container (C4 - Nível 2)** decompõe o sistema em seus principais **containers** (aplicações ou serviços que executam separadamente). Cada container representa uma unidade de implantação com responsabilidades específicas dentro da arquitetura.

Este diagrama mostra como o **Frontend Web**, **Backend API**, **Banco de Dados** e **Serviço de Autenticação** interagem entre si para fornecer as funcionalidades do sistema de gestão de ciclos de estudo.

---

## 2. Containers Principais

| Container          | Tecnologia      | Descrição                                                           | Responsabilidades                                                                                                                                                          |
| ------------------ | --------------- | ------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Frontend Web**   | React / Next.js | Interface web responsiva acessada pelo usuário através do navegador | • Apresentar interface interativa<br>• Gerenciar estado da aplicação<br>• Comunicar com Backend API<br>• Exibir dashboards e gráficos                                      |
| **Backend API**    | Quarkus (Java)  | API RESTful que processa regras de negócio e orquestra operações    | • Implementar regras de negócio<br>• Gerenciar ciclos de estudo<br>• Processar cálculos de métricas<br>• Validar e processar requisições<br>• Comunicar com banco de dados |
| **Banco de Dados** | PostgreSQL      | Banco de dados relacional para persistência de dados                | • Armazenar usuários e perfis<br>• Persistir editais e disciplinas<br>• Guardar ciclos de estudo<br>• Registrar sessões de estudo<br>• Manter estatísticas                 |
| **Autenticação**   | OIDC / OAuth2   | Serviço de autenticação e autorização de usuários                   | • Autenticar usuários<br>• Gerenciar tokens de acesso<br>• Controlar permissões<br>• Garantir segurança de acesso                                                          |

---

## 3. Fluxo de Interações

### 3.1 Autenticação do Usuário

1. **Usuário** acessa o **Frontend Web** através do navegador
2. **Frontend Web** redireciona para **Autenticação (OIDC)**
3. **Autenticação** valida credenciais e retorna token de acesso
4. **Frontend Web** armazena token e permite acesso ao sistema

### 3.2 Operações CRUD

1. **Usuário** interage com **Frontend Web** (criar ciclo, registrar sessão, etc.)
2. **Frontend Web** envia requisição HTTP para **Backend API**
3. **Backend API** autentica requisição com **Autenticação**
4. **Backend API** processa regras de negócio
5. **Backend API** realiza operações CRUD no **Banco de Dados (PostgreSQL)**
6. **Banco de Dados** retorna resultado
7. **Backend API** processa resposta e retorna ao **Frontend Web**
8. **Frontend Web** atualiza interface para o **Usuário**

### 3.3 Visualização de Métricas

1. **Usuário** solicita dashboard de estatísticas no **Frontend Web**
2. **Frontend Web** requisita dados ao **Backend API**
3. **Backend API** consulta e agrega dados do **Banco de Dados**
4. **Backend API** calcula métricas (total de horas, progresso por disciplina, etc.)
5. **Backend API** retorna dados formatados
6. **Frontend Web** renderiza gráficos e visualizações

---

## 4. Tecnologias e Protocolos

| Camada           | Tecnologia                               | Protocolo/Padrão  |
| ---------------- | ---------------------------------------- | ----------------- |
| **Apresentação** | React / Next.js, HTML5, CSS3, JavaScript | HTTPS             |
| **API**          | Quarkus, JAX-RS, RESTEasy                | REST, JSON, HTTPS |
| **Autenticação** | OpenID Connect (OIDC), OAuth2            | HTTPS, JWT        |
| **Persistência** | PostgreSQL, JDBC                         | TCP/IP, SQL       |
