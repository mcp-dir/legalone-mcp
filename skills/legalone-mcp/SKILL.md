---
name: legalone-mcp
description: Skill da REST API do LegalOne na MCP.AI: 39 endpoints em /api/legalone. Wrapper da API oficial do LegalOne (Thomson Reuters / Novajus, pacote Premium): processos e litígios, contatos, agenda de compromissos e tarefas, andamentos, documentos, áreas, tipos de serviço e campos personalizados. Leitura, criação e edição, com filtros no padrão OData. Autenticação OAuth2 (client_credentials) provisionada pela Thomson Reuters por escritório. Cada coleção depende do escopo contratado com a TR, e tools genéricas cobrem qualquer endpoint fora da lista. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# LegalOne — REST API skill

Você tem acesso à **LegalOne** REST API na MCP.AI.

> Wrapper da API oficial do LegalOne (Thomson Reuters / Novajus, pacote Premium): processos e litígios, contatos, agenda de compromissos e tarefas, andamentos, documentos, áreas, tipos de serviço e campos personalizados. Leitura, criação e edição, com filtros no padrão OData. Autenticação OAuth2 (client_credentials) provisionada pela Thomson Reuters por escritório. Cada coleção depende do escopo contratado com a TR, e tools genéricas cobrem qualquer endpoint fora da lista.

## Base URL

```
https://api.mcp.ai/api/legalone
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/legalone/create/appointments \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"data":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/legalone/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (39)

#### `legalone_create_appointments`

Cria um(a) Compromissos/agenda (OData POST /Appointments). _(POST /api/legalone/create/appointments)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `data` | object | Sim | Corpo da entidade Appointments (campos conforme o Swagger oficial). |

#### `legalone_create_contacts`

Cria um(a) Contatos (pessoas físicas/jurídicas: clientes, partes, advogados) (OData POST /Contacts). _(POST /api/legalone/create/contacts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `data` | object | Sim | Corpo da entidade Contacts (campos conforme o Swagger oficial). |

#### `legalone_create_lawsuits`

Cria um(a) Processos judiciais com os campos próprios do módulo (valor da causa, partes, pedidos) (OData POST /Lawsuits). _(POST /api/legalone/create/lawsuits)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `data` | object | Sim | Corpo da entidade Lawsuits (campos conforme o Swagger oficial). |

#### `legalone_create_litigations`

Cria um(a) Processos/litígios, visão consolidada do contencioso (OData POST /Litigations). _(POST /api/legalone/create/litigations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `data` | object | Sim | Corpo da entidade Litigations (campos conforme o Swagger oficial). |

#### `legalone_create_tasks`

Cria um(a) Tarefas/providências (o prazo vem no campo deadLine) (OData POST /Tasks). _(POST /api/legalone/create/tasks)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `data` | object | Sim | Corpo da entidade Tasks (campos conforme o Swagger oficial). |

#### `legalone_create_updates`

Cria um(a) Andamentos/publicações/atualizações do processo (OData POST /Updates). _(POST /api/legalone/create/updates)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `data` | object | Sim | Corpo da entidade Updates (campos conforme o Swagger oficial). |

#### `legalone_customfield_options`

Opções de um campo personalizado (/CustomFieldsDefinitions/{id}/options), resolve o texto por trás dos valores listItemId que aparecem em customFields. _(POST /api/legalone/customfield/options)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id da definição de campo personalizado. |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_get_appointments`

Busca um(a) Compromissos/agenda por id (OData /Appointments/{id}). _(POST /api/legalone/get/appointments)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Appointments. |
| `$expand` | string | Não | OData $expand. |
| `$select` | string | Não | OData $select. |
| `query` | object | Não |  |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_get_appointmentstasks`

Busca um(a) Agenda unificada: compromissos e tarefas na mesma lista por id (OData /AppointmentsTasks/{id}). _(POST /api/legalone/get/appointmentstasks)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em AppointmentsTasks. |
| `$expand` | string | Não | OData $expand. |
| `$select` | string | Não | OData $select. |
| `query` | object | Não |  |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_get_areas`

Busca um(a) Áreas de atuação por id (OData /Areas/{id}). _(POST /api/legalone/get/areas)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Areas. |
| `$expand` | string | Não | OData $expand. |
| `$select` | string | Não | OData $select. |
| `query` | object | Não |  |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_get_contacts`

Busca um(a) Contatos (pessoas físicas/jurídicas: clientes, partes, advogados) por id (OData /Contacts/{id}). _(POST /api/legalone/get/contacts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Contacts. |
| `$expand` | string | Não | OData $expand. |
| `$select` | string | Não | OData $select. |
| `query` | object | Não |  |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_get_customfielddefinitions`

Busca um(a) Definições de campos personalizados por id (OData /CustomFieldsDefinitions/{id}). _(POST /api/legalone/get/customfielddefinitions)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em CustomFieldsDefinitions. |
| `$expand` | string | Não | OData $expand. |
| `$select` | string | Não | OData $select. |
| `query` | object | Não |  |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_get_documents`

Busca um(a) Documentos (GED) por id (OData /Documents/{id}). _(POST /api/legalone/get/documents)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Documents. |
| `$expand` | string | Não | OData $expand. |
| `$select` | string | Não | OData $select. |
| `query` | object | Não |  |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_get_lawsuits`

Busca um(a) Processos judiciais com os campos próprios do módulo (valor da causa, partes, pedidos) por id (OData /Lawsuits/{id}). _(POST /api/legalone/get/lawsuits)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Lawsuits. |
| `$expand` | string | Não | OData $expand. |
| `$select` | string | Não | OData $select. |
| `query` | object | Não |  |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_get_litigations`

Busca um(a) Processos/litígios, visão consolidada do contencioso por id (OData /Litigations/{id}). _(POST /api/legalone/get/litigations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Litigations. |
| `$expand` | string | Não | OData $expand. |
| `$select` | string | Não | OData $select. |
| `query` | object | Não |  |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_get_servicetypes`

Busca um(a) Tipos de serviço/processo por id (OData /ServiceTypes/{id}). _(POST /api/legalone/get/servicetypes)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em ServiceTypes. |
| `$expand` | string | Não | OData $expand. |
| `$select` | string | Não | OData $select. |
| `query` | object | Não |  |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_get_tasks`

Busca um(a) Tarefas/providências (o prazo vem no campo deadLine) por id (OData /Tasks/{id}). _(POST /api/legalone/get/tasks)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Tasks. |
| `$expand` | string | Não | OData $expand. |
| `$select` | string | Não | OData $select. |
| `query` | object | Não |  |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_get_updates`

Busca um(a) Andamentos/publicações/atualizações do processo por id (OData /Updates/{id}). _(POST /api/legalone/get/updates)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Updates. |
| `$expand` | string | Não | OData $expand. |
| `$select` | string | Não | OData $select. |
| `query` | object | Não |  |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_get_users`

Busca um(a) Usuários/responsáveis do escritório por id (OData /Users/{id}). _(POST /api/legalone/get/users)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Users. |
| `$expand` | string | Não | OData $expand. |
| `$select` | string | Não | OData $select. |
| `query` | object | Não |  |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_list_appointments`

Lista Compromissos/agenda (OData /Appointments). _(POST /api/legalone/list/appointments)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `$filter` | string | Não | OData $filter (ex.: "contains(name,'Silva')"). |
| `$expand` | string | Não | OData $expand (ex.: "customFields,participants"). |
| `$select` | string | Não | OData $select (campos a retornar). |
| `$orderby` | string | Não | OData $orderby (ex.: "createdDate desc"). |
| `$top` | integer | Não | OData $top (page size, máx 200). |
| `$skip` | integer | Não | OData $skip (offset). |
| `$count` | boolean | Não | OData $count (inclui contagem total). |
| `query` | object | Não | Parâmetros de query adicionais conforme a API OData oficial. |

#### `legalone_list_appointmentstasks`

Lista Agenda unificada: compromissos e tarefas na mesma lista (OData /AppointmentsTasks). _(POST /api/legalone/list/appointmentstasks)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `$filter` | string | Não | OData $filter (ex.: "contains(name,'Silva')"). |
| `$expand` | string | Não | OData $expand (ex.: "customFields,participants"). |
| `$select` | string | Não | OData $select (campos a retornar). |
| `$orderby` | string | Não | OData $orderby (ex.: "createdDate desc"). |
| `$top` | integer | Não | OData $top (page size, máx 200). |
| `$skip` | integer | Não | OData $skip (offset). |
| `$count` | boolean | Não | OData $count (inclui contagem total). |
| `query` | object | Não | Parâmetros de query adicionais conforme a API OData oficial. |

#### `legalone_list_areas`

Lista Áreas de atuação (OData /Areas). _(POST /api/legalone/list/areas)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `$filter` | string | Não | OData $filter (ex.: "contains(name,'Silva')"). |
| `$expand` | string | Não | OData $expand (ex.: "customFields,participants"). |
| `$select` | string | Não | OData $select (campos a retornar). |
| `$orderby` | string | Não | OData $orderby (ex.: "createdDate desc"). |
| `$top` | integer | Não | OData $top (page size, máx 200). |
| `$skip` | integer | Não | OData $skip (offset). |
| `$count` | boolean | Não | OData $count (inclui contagem total). |
| `query` | object | Não | Parâmetros de query adicionais conforme a API OData oficial. |

#### `legalone_list_contacts`

Lista Contatos (pessoas físicas/jurídicas: clientes, partes, advogados) (OData /Contacts). _(POST /api/legalone/list/contacts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `$filter` | string | Não | OData $filter (ex.: "contains(name,'Silva')"). |
| `$expand` | string | Não | OData $expand (ex.: "customFields,participants"). |
| `$select` | string | Não | OData $select (campos a retornar). |
| `$orderby` | string | Não | OData $orderby (ex.: "createdDate desc"). |
| `$top` | integer | Não | OData $top (page size, máx 200). |
| `$skip` | integer | Não | OData $skip (offset). |
| `$count` | boolean | Não | OData $count (inclui contagem total). |
| `query` | object | Não | Parâmetros de query adicionais conforme a API OData oficial. |

#### `legalone_list_customfielddefinitions`

Lista Definições de campos personalizados (OData /CustomFieldsDefinitions). _(POST /api/legalone/list/customfielddefinitions)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `$filter` | string | Não | OData $filter (ex.: "contains(name,'Silva')"). |
| `$expand` | string | Não | OData $expand (ex.: "customFields,participants"). |
| `$select` | string | Não | OData $select (campos a retornar). |
| `$orderby` | string | Não | OData $orderby (ex.: "createdDate desc"). |
| `$top` | integer | Não | OData $top (page size, máx 200). |
| `$skip` | integer | Não | OData $skip (offset). |
| `$count` | boolean | Não | OData $count (inclui contagem total). |
| `query` | object | Não | Parâmetros de query adicionais conforme a API OData oficial. |

#### `legalone_list_documents`

Lista Documentos (GED) (OData /Documents). _(POST /api/legalone/list/documents)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `$filter` | string | Não | OData $filter (ex.: "contains(name,'Silva')"). |
| `$expand` | string | Não | OData $expand (ex.: "customFields,participants"). |
| `$select` | string | Não | OData $select (campos a retornar). |
| `$orderby` | string | Não | OData $orderby (ex.: "createdDate desc"). |
| `$top` | integer | Não | OData $top (page size, máx 200). |
| `$skip` | integer | Não | OData $skip (offset). |
| `$count` | boolean | Não | OData $count (inclui contagem total). |
| `query` | object | Não | Parâmetros de query adicionais conforme a API OData oficial. |

#### `legalone_list_lawsuits`

Lista Processos judiciais com os campos próprios do módulo (valor da causa, partes, pedidos) (OData /Lawsuits). _(POST /api/legalone/list/lawsuits)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `$filter` | string | Não | OData $filter (ex.: "contains(name,'Silva')"). |
| `$expand` | string | Não | OData $expand (ex.: "customFields,participants"). |
| `$select` | string | Não | OData $select (campos a retornar). |
| `$orderby` | string | Não | OData $orderby (ex.: "createdDate desc"). |
| `$top` | integer | Não | OData $top (page size, máx 200). |
| `$skip` | integer | Não | OData $skip (offset). |
| `$count` | boolean | Não | OData $count (inclui contagem total). |
| `query` | object | Não | Parâmetros de query adicionais conforme a API OData oficial. |

#### `legalone_list_litigations`

Lista Processos/litígios, visão consolidada do contencioso (OData /Litigations). _(POST /api/legalone/list/litigations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `$filter` | string | Não | OData $filter (ex.: "contains(name,'Silva')"). |
| `$expand` | string | Não | OData $expand (ex.: "customFields,participants"). |
| `$select` | string | Não | OData $select (campos a retornar). |
| `$orderby` | string | Não | OData $orderby (ex.: "createdDate desc"). |
| `$top` | integer | Não | OData $top (page size, máx 200). |
| `$skip` | integer | Não | OData $skip (offset). |
| `$count` | boolean | Não | OData $count (inclui contagem total). |
| `query` | object | Não | Parâmetros de query adicionais conforme a API OData oficial. |

#### `legalone_list_servicetypes`

Lista Tipos de serviço/processo (OData /ServiceTypes). _(POST /api/legalone/list/servicetypes)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `$filter` | string | Não | OData $filter (ex.: "contains(name,'Silva')"). |
| `$expand` | string | Não | OData $expand (ex.: "customFields,participants"). |
| `$select` | string | Não | OData $select (campos a retornar). |
| `$orderby` | string | Não | OData $orderby (ex.: "createdDate desc"). |
| `$top` | integer | Não | OData $top (page size, máx 200). |
| `$skip` | integer | Não | OData $skip (offset). |
| `$count` | boolean | Não | OData $count (inclui contagem total). |
| `query` | object | Não | Parâmetros de query adicionais conforme a API OData oficial. |

#### `legalone_list_tasks`

Lista Tarefas/providências (o prazo vem no campo deadLine) (OData /Tasks). _(POST /api/legalone/list/tasks)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `$filter` | string | Não | OData $filter (ex.: "contains(name,'Silva')"). |
| `$expand` | string | Não | OData $expand (ex.: "customFields,participants"). |
| `$select` | string | Não | OData $select (campos a retornar). |
| `$orderby` | string | Não | OData $orderby (ex.: "createdDate desc"). |
| `$top` | integer | Não | OData $top (page size, máx 200). |
| `$skip` | integer | Não | OData $skip (offset). |
| `$count` | boolean | Não | OData $count (inclui contagem total). |
| `query` | object | Não | Parâmetros de query adicionais conforme a API OData oficial. |

#### `legalone_list_updates`

Lista Andamentos/publicações/atualizações do processo (OData /Updates). _(POST /api/legalone/list/updates)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `$filter` | string | Não | OData $filter (ex.: "contains(name,'Silva')"). |
| `$expand` | string | Não | OData $expand (ex.: "customFields,participants"). |
| `$select` | string | Não | OData $select (campos a retornar). |
| `$orderby` | string | Não | OData $orderby (ex.: "createdDate desc"). |
| `$top` | integer | Não | OData $top (page size, máx 200). |
| `$skip` | integer | Não | OData $skip (offset). |
| `$count` | boolean | Não | OData $count (inclui contagem total). |
| `query` | object | Não | Parâmetros de query adicionais conforme a API OData oficial. |

#### `legalone_list_users`

Lista Usuários/responsáveis do escritório (OData /Users). _(POST /api/legalone/list/users)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `$filter` | string | Não | OData $filter (ex.: "contains(name,'Silva')"). |
| `$expand` | string | Não | OData $expand (ex.: "customFields,participants"). |
| `$select` | string | Não | OData $select (campos a retornar). |
| `$orderby` | string | Não | OData $orderby (ex.: "createdDate desc"). |
| `$top` | integer | Não | OData $top (page size, máx 200). |
| `$skip` | integer | Não | OData $skip (offset). |
| `$count` | boolean | Não | OData $count (inclui contagem total). |
| `query` | object | Não | Parâmetros de query adicionais conforme a API OData oficial. |

#### `legalone_metadata`

Metadados da conexão: escopos que a Thomson Reuters liberou para este escritório, produtos da API, base da API e as coleções disponíveis com as tools de cada uma. _(POST /api/legalone/metadata)_

#### `legalone_odata_get`

GET genérico em qualquer coleção/recurso OData do LegalOne. _(POST /api/legalone/odata/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `$filter` | string | Não | OData $filter (ex.: "contains(name,'Silva')"). |
| `$expand` | string | Não | OData $expand (ex.: "customFields,participants"). |
| `$select` | string | Não | OData $select (campos a retornar). |
| `$orderby` | string | Não | OData $orderby (ex.: "createdDate desc"). |
| `$top` | integer | Não | OData $top (page size, máx 200). |
| `$skip` | integer | Não | OData $skip (offset). |
| `$count` | boolean | Não | OData $count (inclui contagem total). |
| `query` | object | Não | Parâmetros de query adicionais conforme a API OData oficial. |
| `entity` | string | Sim | Nome da coleção OData (PascalCase), ex.: Litigations, Contacts. |
| `id` | string | Não | Id do recurso (omita para listar a coleção). |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_request`

Escape hatch: chamada OData crua. _(POST /api/legalone/request)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `method` | string | Sim | Método HTTP. (GET, POST, PATCH, PUT, DELETE) |
| `path` | string | Sim | Caminho relativo à base OData (começa com /). |
| `query` | object | Não | Query params (inclui $-options). |
| `body` | object | Não | Corpo JSON (POST/PATCH/PUT). |

#### `legalone_update_appointments`

Atualiza um(a) Compromissos/agenda (OData PATCH /Appointments/{id}). _(POST /api/legalone/update/appointments)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Appointments. |
| `data` | object | Sim | Campos a alterar (merge parcial). |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_update_contacts`

Atualiza um(a) Contatos (pessoas físicas/jurídicas: clientes, partes, advogados) (OData PATCH /Contacts/{id}). _(POST /api/legalone/update/contacts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Contacts. |
| `data` | object | Sim | Campos a alterar (merge parcial). |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_update_lawsuits`

Atualiza um(a) Processos judiciais com os campos próprios do módulo (valor da causa, partes, pedidos) (OData PATCH /Lawsuits/{id}). _(POST /api/legalone/update/lawsuits)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Lawsuits. |
| `data` | object | Sim | Campos a alterar (merge parcial). |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_update_litigations`

Atualiza um(a) Processos/litígios, visão consolidada do contencioso (OData PATCH /Litigations/{id}). _(POST /api/legalone/update/litigations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Litigations. |
| `data` | object | Sim | Campos a alterar (merge parcial). |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `legalone_update_tasks`

Atualiza um(a) Tarefas/providências (o prazo vem no campo deadLine) (OData PATCH /Tasks/{id}). _(POST /api/legalone/update/tasks)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Id do recurso em Tasks. |
| `data` | object | Sim | Campos a alterar (merge parcial). |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_legalone` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
