# LegalOne

### LegalOne for Claude, ChatGPT and AI agents

Wrapper for the official LegalOne API (Thomson Reuters / Novajus, Premium package): lawsuits and litigations, contacts, appointments and tasks, updates, documents, practice areas, service types and custom fields. Read, create and update, with OData style filters. OAuth2 (client_credentials) auth provisioned by Thomson Reuters per firm. Each collection depends on the scope your firm contracted with TR, and generic tools cover any endpoint outside the list.

- 📊 **39 tools**
- ✏️ **Read and write**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → name `LegalOne`, URL `https://api.mcp.ai/p_legalone`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=legalone&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9sZWdhbG9uZSJ9)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=legalone&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_legalone%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_legalone
```

---

## 39 tools

| Tool | Description |
|---|---|
| `legalone_odata_get` | GET genérico em qualquer coleção/recurso OData do LegalOne. |
| `legalone_request` | Escape hatch: chamada OData crua. |
| `legalone_metadata` | Metadados da conexão: escopos que a Thomson Reuters liberou para este escritório, produtos da API, base da API e as coleções disponíveis com as tools de cada uma. |
| `legalone_customfield_options` | Opções de um campo personalizado (/CustomFieldsDefinitions/{id}/options), resolve o texto por trás dos valores listItemId que aparecem em customFields. |
| `legalone_list_litigations` | Lista Processos/litígios, visão consolidada do contencioso (OData /Litigations). |
| `legalone_get_litigations` | Busca um(a) Processos/litígios, visão consolidada do contencioso por id (OData /Litigations/{id}). |
| `legalone_create_litigations` | Cria um(a) Processos/litígios, visão consolidada do contencioso (OData POST /Litigations). |
| `legalone_update_litigations` | Atualiza um(a) Processos/litígios, visão consolidada do contencioso (OData PATCH /Litigations/{id}). |
| `legalone_list_lawsuits` | Lista Processos judiciais com os campos próprios do módulo (valor da causa, partes, pedidos) (OData /Lawsuits). |
| `legalone_get_lawsuits` | Busca um(a) Processos judiciais com os campos próprios do módulo (valor da causa, partes, pedidos) por id (OData /Lawsuits/{id}). |
| `legalone_create_lawsuits` | Cria um(a) Processos judiciais com os campos próprios do módulo (valor da causa, partes, pedidos) (OData POST /Lawsuits). |
| `legalone_update_lawsuits` | Atualiza um(a) Processos judiciais com os campos próprios do módulo (valor da causa, partes, pedidos) (OData PATCH /Lawsuits/{id}). |
| `legalone_list_contacts` | Lista Contatos (pessoas físicas/jurídicas: clientes, partes, advogados) (OData /Contacts). |
| `legalone_get_contacts` | Busca um(a) Contatos (pessoas físicas/jurídicas: clientes, partes, advogados) por id (OData /Contacts/{id}). |
| `legalone_create_contacts` | Cria um(a) Contatos (pessoas físicas/jurídicas: clientes, partes, advogados) (OData POST /Contacts). |
| `legalone_update_contacts` | Atualiza um(a) Contatos (pessoas físicas/jurídicas: clientes, partes, advogados) (OData PATCH /Contacts/{id}). |
| `legalone_list_appointments` | Lista Compromissos/agenda (OData /Appointments). |
| `legalone_get_appointments` | Busca um(a) Compromissos/agenda por id (OData /Appointments/{id}). |
| `legalone_create_appointments` | Cria um(a) Compromissos/agenda (OData POST /Appointments). |
| `legalone_update_appointments` | Atualiza um(a) Compromissos/agenda (OData PATCH /Appointments/{id}). |
| `legalone_list_tasks` | Lista Tarefas/providências (o prazo vem no campo deadLine) (OData /Tasks). |
| `legalone_get_tasks` | Busca um(a) Tarefas/providências (o prazo vem no campo deadLine) por id (OData /Tasks/{id}). |
| `legalone_create_tasks` | Cria um(a) Tarefas/providências (o prazo vem no campo deadLine) (OData POST /Tasks). |
| `legalone_update_tasks` | Atualiza um(a) Tarefas/providências (o prazo vem no campo deadLine) (OData PATCH /Tasks/{id}). |
| `legalone_list_appointmentstasks` | Lista Agenda unificada: compromissos e tarefas na mesma lista (OData /AppointmentsTasks). |
| `legalone_get_appointmentstasks` | Busca um(a) Agenda unificada: compromissos e tarefas na mesma lista por id (OData /AppointmentsTasks/{id}). |
| `legalone_list_updates` | Lista Andamentos/publicações/atualizações do processo (OData /Updates). |
| `legalone_get_updates` | Busca um(a) Andamentos/publicações/atualizações do processo por id (OData /Updates/{id}). |
| `legalone_create_updates` | Cria um(a) Andamentos/publicações/atualizações do processo (OData POST /Updates). |
| `legalone_list_documents` | Lista Documentos (GED) (OData /Documents). |
| `legalone_get_documents` | Busca um(a) Documentos (GED) por id (OData /Documents/{id}). |
| `legalone_list_areas` | Lista Áreas de atuação (OData /Areas). |
| `legalone_get_areas` | Busca um(a) Áreas de atuação por id (OData /Areas/{id}). |
| `legalone_list_servicetypes` | Lista Tipos de serviço/processo (OData /ServiceTypes). |
| `legalone_get_servicetypes` | Busca um(a) Tipos de serviço/processo por id (OData /ServiceTypes/{id}). |
| `legalone_list_users` | Lista Usuários/responsáveis do escritório (OData /Users). |
| `legalone_get_users` | Busca um(a) Usuários/responsáveis do escritório por id (OData /Users/{id}). |
| `legalone_list_customfielddefinitions` | Lista Definições de campos personalizados (OData /CustomFieldsDefinitions). |
| `legalone_get_customfielddefinitions` | Busca um(a) Definições de campos personalizados por id (OData /CustomFieldsDefinitions/{id}). |

---

## Pricing

See [docs/precos.md](docs/precos.md) (PT-BR).

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_legalone` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
