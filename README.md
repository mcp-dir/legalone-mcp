# LegalOne

### LegalOne para Claude, ChatGPT e agentes de IA

Wrapper da API oficial do LegalOne (Thomson Reuters / Novajus, pacote Premium): processos e litígios, contatos, agenda de compromissos e tarefas, andamentos, documentos, áreas, tipos de serviço e campos personalizados. Leitura, criação e edição, com filtros no padrão OData. Autenticação OAuth2 (client_credentials) provisionada pela Thomson Reuters por escritório. Cada coleção depende do escopo contratado com a TR, e tools genéricas cobrem qualquer endpoint fora da lista.

- 📊 **39 ferramentas**
- ✏️ **Leitura e escrita**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `LegalOne` e **URL** `https://api.mcp.ai/p_legalone`.

### Cursor

[➕ Instalar LegalOne no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=legalone&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9sZWdhbG9uZSJ9)

### VS Code (Copilot Chat)

[➕ Instalar LegalOne no VS Code](vscode:mcp/install?name=legalone&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_legalone%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_legalone
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Liste os processos do LegalOne com movimentação nos últimos 7 dias
Busque o contato (cliente) X no LegalOne e mostre os processos vinculados
Crie um compromisso na agenda do LegalOne vinculado ao processo Y
```

---

## 39 ferramentas disponíveis

| Tool | Descrição |
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

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Planos a partir do tier grátis. Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Sub-processadores**: o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_legalone`.


---

## Suporte

- 📧 [legalone@mcp.ai](mailto:legalone@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/legalone-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_legalone` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
