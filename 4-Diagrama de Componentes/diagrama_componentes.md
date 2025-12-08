# 🧩 Diagrama de Componentes — Sistema de Gestão de Ciclos de Estudo (C4 - Nível 3)

## 1. Visão Geral

O **Sistema de Gestão de Ciclos de Estudo** é composto por diversos módulos responsáveis pela criação, acompanhamento e análise do progresso do estudante.  
Este diagrama detalha os **principais componentes internos**, suas **responsabilidades** e suas **interações** com serviços externos e o usuário.

---

## 2. Principais Componentes Internos

| Componente                                | Responsabilidade                                                                                                  |
| ----------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Frontend (React / Next.js)**            | Interface de usuário; permite visualizar ciclos, tarefas e estatísticas.                                          |
| **Backend (Quarkus API)**                 | Camada de serviços REST; gerencia regras de negócio e persistência.                                               |
| **CicloService**                          | Controla a criação, atualização e exclusão de ciclos de estudo.                                                   |
| **DisciplinaService**                     | Gerencia disciplinas associadas aos ciclos, incluindo pesos e metas.                                              |
| **RevisaoService**                        | Gera e agenda revisões com base em intervalos definidos (ex: 24h, 7d, 30d).                                       |
| **EstatisticaService**                    | Calcula métricas de desempenho (tempo, acertos, evolução).                                                        |
| **UsuarioService**                        | Garante a autenticação e vincula dados ao usuário logado.                                                         |
| **Repositories (Camada de Persistência)** | Manipula dados no banco (ex: `CicloRepository`, `DisciplinaRepository`, etc.).                                    |
| **Providers**                             | Interfaces que declaram os os métodos que os serviços podem utilizar.                                             |
| **Adapters**                              | Implementam as interfaces Providers e se comunicam os os serviços externos, garantindo a inversão de dependência. |
| **Database (PostgreSQL)**                 | Armazena dados de usuários, ciclos, disciplinas, revisões e estatísticas.                                         |

---

## 3. Interações Externas

| Sistema Externo                           | Papel                                                 |
| ----------------------------------------- | ----------------------------------------------------- |
| **Serviço de Autenticação (OIDC/OAuth2)** | Autentica usuários e fornece tokens JWT para acesso.  |
| **API de Concursos Públicos**             | Fornece dados de concursos, cargos e disciplinas.     |
| **Dashboard (Grafana/Tempo)**             | Exibe métricas e estatísticas coletadas pelo sistema. |
