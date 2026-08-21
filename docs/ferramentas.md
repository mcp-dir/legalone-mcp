# Ferramentas

LegalOne expõe 39 ferramentas.

### 1. `legalone_odata_get`
**Input**: `$filter` (opcional), `$expand` (opcional), `$select` (opcional), `$orderby` (opcional), `$top` (opcional), `$skip` (opcional), `$count` (opcional), `query` (opcional), `entity`, `id` (opcional), `ids` (opcional)

GET genérico em qualquer coleção/recurso OData do LegalOne.

### 2. `legalone_request`
**Input**: `method`, `path`, `query` (opcional), `body` (opcional)

Escape hatch: chamada OData crua.

### 3. `legalone_metadata`
**Input**: nenhum input

Metadados da conexão: escopos que a Thomson Reuters liberou para este escritório, produtos da API, base da API e as coleções disponíveis com as tools de cada uma.

### 4. `legalone_customfield_options`
**Input**: `id`, `ids` (opcional)

Opções de um campo personalizado (/CustomFieldsDefinitions/{id}/options), resolve o texto por trás dos valores listItemId que aparecem em customFields.

### 5. `legalone_list_litigations`
**Input**: `$filter` (opcional), `$expand` (opcional), `$select` (opcional), `$orderby` (opcional), `$top` (opcional), `$skip` (opcional), `$count` (opcional), `query` (opcional)

Lista Processos/litígios, visão consolidada do contencioso (OData /Litigations).

### 6. `legalone_get_litigations`
**Input**: `id`, `$expand` (opcional), `$select` (opcional), `query` (opcional), `ids` (opcional)

Busca um(a) Processos/litígios, visão consolidada do contencioso por id (OData /Litigations/{id}).

### 7. `legalone_create_litigations`
**Input**: `data`

Cria um(a) Processos/litígios, visão consolidada do contencioso (OData POST /Litigations).

### 8. `legalone_update_litigations`
**Input**: `id`, `data`, `ids` (opcional)

Atualiza um(a) Processos/litígios, visão consolidada do contencioso (OData PATCH /Litigations/{id}).

### 9. `legalone_list_lawsuits`
**Input**: `$filter` (opcional), `$expand` (opcional), `$select` (opcional), `$orderby` (opcional), `$top` (opcional), `$skip` (opcional), `$count` (opcional), `query` (opcional)

Lista Processos judiciais com os campos próprios do módulo (valor da causa, partes, pedidos) (OData /Lawsuits).

### 10. `legalone_get_lawsuits`
**Input**: `id`, `$expand` (opcional), `$select` (opcional), `query` (opcional), `ids` (opcional)

Busca um(a) Processos judiciais com os campos próprios do módulo (valor da causa, partes, pedidos) por id (OData /Lawsuits/{id}).

### 11. `legalone_create_lawsuits`
**Input**: `data`

Cria um(a) Processos judiciais com os campos próprios do módulo (valor da causa, partes, pedidos) (OData POST /Lawsuits).

### 12. `legalone_update_lawsuits`
**Input**: `id`, `data`, `ids` (opcional)

Atualiza um(a) Processos judiciais com os campos próprios do módulo (valor da causa, partes, pedidos) (OData PATCH /Lawsuits/{id}).

### 13. `legalone_list_contacts`
**Input**: `$filter` (opcional), `$expand` (opcional), `$select` (opcional), `$orderby` (opcional), `$top` (opcional), `$skip` (opcional), `$count` (opcional), `query` (opcional)

Lista Contatos (pessoas físicas/jurídicas: clientes, partes, advogados) (OData /Contacts).

### 14. `legalone_get_contacts`
**Input**: `id`, `$expand` (opcional), `$select` (opcional), `query` (opcional), `ids` (opcional)

Busca um(a) Contatos (pessoas físicas/jurídicas: clientes, partes, advogados) por id (OData /Contacts/{id}).

### 15. `legalone_create_contacts`
**Input**: `data`

Cria um(a) Contatos (pessoas físicas/jurídicas: clientes, partes, advogados) (OData POST /Contacts).

### 16. `legalone_update_contacts`
**Input**: `id`, `data`, `ids` (opcional)

Atualiza um(a) Contatos (pessoas físicas/jurídicas: clientes, partes, advogados) (OData PATCH /Contacts/{id}).

### 17. `legalone_list_appointments`
**Input**: `$filter` (opcional), `$expand` (opcional), `$select` (opcional), `$orderby` (opcional), `$top` (opcional), `$skip` (opcional), `$count` (opcional), `query` (opcional)

Lista Compromissos/agenda (OData /Appointments).

### 18. `legalone_get_appointments`
**Input**: `id`, `$expand` (opcional), `$select` (opcional), `query` (opcional), `ids` (opcional)

Busca um(a) Compromissos/agenda por id (OData /Appointments/{id}).

### 19. `legalone_create_appointments`
**Input**: `data`

Cria um(a) Compromissos/agenda (OData POST /Appointments).

### 20. `legalone_update_appointments`
**Input**: `id`, `data`, `ids` (opcional)

Atualiza um(a) Compromissos/agenda (OData PATCH /Appointments/{id}).

### 21. `legalone_list_tasks`
**Input**: `$filter` (opcional), `$expand` (opcional), `$select` (opcional), `$orderby` (opcional), `$top` (opcional), `$skip` (opcional), `$count` (opcional), `query` (opcional)

Lista Tarefas/providências (o prazo vem no campo deadLine) (OData /Tasks).

### 22. `legalone_get_tasks`
**Input**: `id`, `$expand` (opcional), `$select` (opcional), `query` (opcional), `ids` (opcional)

Busca um(a) Tarefas/providências (o prazo vem no campo deadLine) por id (OData /Tasks/{id}).

### 23. `legalone_create_tasks`
**Input**: `data`

Cria um(a) Tarefas/providências (o prazo vem no campo deadLine) (OData POST /Tasks).

### 24. `legalone_update_tasks`
**Input**: `id`, `data`, `ids` (opcional)

Atualiza um(a) Tarefas/providências (o prazo vem no campo deadLine) (OData PATCH /Tasks/{id}).

### 25. `legalone_list_appointmentstasks`
**Input**: `$filter` (opcional), `$expand` (opcional), `$select` (opcional), `$orderby` (opcional), `$top` (opcional), `$skip` (opcional), `$count` (opcional), `query` (opcional)

Lista Agenda unificada: compromissos e tarefas na mesma lista (OData /AppointmentsTasks).

### 26. `legalone_get_appointmentstasks`
**Input**: `id`, `$expand` (opcional), `$select` (opcional), `query` (opcional), `ids` (opcional)

Busca um(a) Agenda unificada: compromissos e tarefas na mesma lista por id (OData /AppointmentsTasks/{id}).

### 27. `legalone_list_updates`
**Input**: `$filter` (opcional), `$expand` (opcional), `$select` (opcional), `$orderby` (opcional), `$top` (opcional), `$skip` (opcional), `$count` (opcional), `query` (opcional)

Lista Andamentos/publicações/atualizações do processo (OData /Updates).

### 28. `legalone_get_updates`
**Input**: `id`, `$expand` (opcional), `$select` (opcional), `query` (opcional), `ids` (opcional)

Busca um(a) Andamentos/publicações/atualizações do processo por id (OData /Updates/{id}).

### 29. `legalone_create_updates`
**Input**: `data`

Cria um(a) Andamentos/publicações/atualizações do processo (OData POST /Updates).

### 30. `legalone_list_documents`
**Input**: `$filter` (opcional), `$expand` (opcional), `$select` (opcional), `$orderby` (opcional), `$top` (opcional), `$skip` (opcional), `$count` (opcional), `query` (opcional)

Lista Documentos (GED) (OData /Documents).

### 31. `legalone_get_documents`
**Input**: `id`, `$expand` (opcional), `$select` (opcional), `query` (opcional), `ids` (opcional)

Busca um(a) Documentos (GED) por id (OData /Documents/{id}).

### 32. `legalone_list_areas`
**Input**: `$filter` (opcional), `$expand` (opcional), `$select` (opcional), `$orderby` (opcional), `$top` (opcional), `$skip` (opcional), `$count` (opcional), `query` (opcional)

Lista Áreas de atuação (OData /Areas).

### 33. `legalone_get_areas`
**Input**: `id`, `$expand` (opcional), `$select` (opcional), `query` (opcional), `ids` (opcional)

Busca um(a) Áreas de atuação por id (OData /Areas/{id}).

### 34. `legalone_list_servicetypes`
**Input**: `$filter` (opcional), `$expand` (opcional), `$select` (opcional), `$orderby` (opcional), `$top` (opcional), `$skip` (opcional), `$count` (opcional), `query` (opcional)

Lista Tipos de serviço/processo (OData /ServiceTypes).

### 35. `legalone_get_servicetypes`
**Input**: `id`, `$expand` (opcional), `$select` (opcional), `query` (opcional), `ids` (opcional)

Busca um(a) Tipos de serviço/processo por id (OData /ServiceTypes/{id}).

### 36. `legalone_list_users`
**Input**: `$filter` (opcional), `$expand` (opcional), `$select` (opcional), `$orderby` (opcional), `$top` (opcional), `$skip` (opcional), `$count` (opcional), `query` (opcional)

Lista Usuários/responsáveis do escritório (OData /Users).

### 37. `legalone_get_users`
**Input**: `id`, `$expand` (opcional), `$select` (opcional), `query` (opcional), `ids` (opcional)

Busca um(a) Usuários/responsáveis do escritório por id (OData /Users/{id}).

### 38. `legalone_list_customfielddefinitions`
**Input**: `$filter` (opcional), `$expand` (opcional), `$select` (opcional), `$orderby` (opcional), `$top` (opcional), `$skip` (opcional), `$count` (opcional), `query` (opcional)

Lista Definições de campos personalizados (OData /CustomFieldsDefinitions).

### 39. `legalone_get_customfielddefinitions`
**Input**: `id`, `$expand` (opcional), `$select` (opcional), `query` (opcional), `ids` (opcional)

Busca um(a) Definições de campos personalizados por id (OData /CustomFieldsDefinitions/{id}).

## Prompts de exemplo

```
Liste os processos do LegalOne com movimentação nos últimos 7 dias
Busque o contato (cliente) X no LegalOne e mostre os processos vinculados
Crie um compromisso na agenda do LegalOne vinculado ao processo Y
```
