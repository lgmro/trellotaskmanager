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

1. Navegue até a pasta do projeto:

```bash
cd /home/lucasgabriel/Documents/Workspace/Agents-DIO/AgentTrelloDio
```

2. Ative o ambiente virtual:

```bash
source .lab-dio/bin/activate
```

3. Instale as dependências (se ainda não estiverem instaladas):

```bash
pip install -r requirements.txt
```

4. Configure as variáveis de ambiente no arquivo `.env` do projeto:

```env
TRELLO_API_KEY=seu_api_key
TRELLO_API_SECRET=seu_api_secret
TRELLO_TOKEN=seu_token
```

5. Execute o agente usando o comando apropriado para o `adk`, por exemplo:

```bash
adk create agenttaskmanager
```

ou diretamente com o binário do venv:

```bash
./.lab-dio/bin/adk create agenttaskmanager
```

> Se você estiver usando outra pasta ou virtualenv, ajuste o caminho conforme necessário.

## Avisos

- Garanta que o board Trello chamado `DIO` exista e possua listas como `A FAZER`, `EM ANDAMENTO` e `CONCLUIDO`.
- O campo `due` deve ser enviado em formato válido (por exemplo `YYYY-MM-DD` ou `YYYY-MM-DDTHH:MM:SS`).