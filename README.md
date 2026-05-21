# Trello Task Manager

Este projeto contém um agente Python que integra Trello e usa a biblioteca `google.adk` para gerenciar tarefas automaticamente.

## O que o agente faz

- Cria cards no Trello a partir de tarefas descritas pelo usuário
- Lista tarefas por status (`todas`, `a fazer`, `em andamento`, `concluido`)
- Move cards entre listas para atualizar o status da tarefa
- Usa o contexto temporal para organizar as atividades do dia

## Estrutura principal

O agente está em `AgentTaskManager/agent.py` e define:

- `get_temporal_context()` — retorna data e hora atual
- `adicionar_tarefa(...)` — cria um card no Trello
- `listar_tarefas(...)` — busca tarefas no board
- `mudar_status_tarefa(...)` — move o card para uma lista diferente

## Como rodar o agente

1. Navegue até a pasta do projeto após clonar ou descompactar o repositório:

```bash
cd <pasta-do-projeto>/AgentTrelloDio
```

2. Crie e ative o ambiente virtual (se ainda não existir):

```bash
python3 -m venv .lab-dio
source .lab-dio/bin/activate
```

> O projeto já inclui `.gitignore` para ignorar `.env` e `.lab-dio/`, então você não precisa commitar esses arquivos.

3. Instale as dependências:

```bash
pip install -r requirements.txt
```

4. Copie o exemplo de ambiente e configure as credenciais do Trello em `AgentTaskManager`:

```bash
cp AgentTaskManager/.env.example AgentTaskManager/.env
```

5. Abra `AgentTaskManager/.env` e preencha com seus valores:

```env
TRELLO_API_KEY=seu_api_key
TRELLO_API_SECRET=seu_api_secret
TRELLO_TOKEN=seu_token
GOOGLE_API_KEY=seu_google_api_key
# Se você usar Vertex AI, use uma das opções abaixo em vez de GOOGLE_API_KEY:
# GOOGLE_CLOUD_PROJECT=seu_projeto
# GOOGLE_CLOUD_LOCATION=seu_regiao
```

6. Execute o agente usando o comando `adk`:

```bash
adk web
```

ou diretamente com o binário do venv:

```bash
./.lab-dio/bin/adk web
```

> Se você usar outro ambiente virtual, ajuste os comandos `source` e `./.lab-dio/bin/adk` conforme necessário.

## Avisos

- Garanta que o board Trello chamado `DIO` exista ou mude o nome no código do agente e possua listas como `A FAZER`, `EM ANDAMENTO` e `CONCLUIDO` (ou mude de acordo com sua necessidade).
- O campo `due` deve ser enviado em formato válido (por exemplo `YYYY-MM-DD` ou `YYYY-MM-DDTHH:MM:SS`).