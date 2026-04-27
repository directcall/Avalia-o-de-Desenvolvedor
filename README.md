# Directcall Telecom - Avaliação de Desenvolvedor

**Documento:** Roteiro do Teste Técnico  
**Versão:** 1.0  
**Site:** directcall.com.br  
**Perfil avaliado:** Desenvolvedor Sênior  
**Stack principal:** Ruby + MySQL no backend e TypeScript no frontend

---

## 1. Objetivo da avaliação

O objetivo deste teste técnico é avaliar a capacidade do candidato de projetar, desenvolver, documentar e entregar uma aplicação web simples, porém bem estruturada, simulando um sistema de **fila de atendimento**.

A avaliação deve observar não apenas se o sistema funciona, mas principalmente a forma como o candidato pensa arquitetura, modelagem de dados, organização de código, autenticação, comunicação em tempo real, integração externa, tratamento de erros e documentação.

---

## 2. Contexto do sistema

A Directcall Telecom deseja avaliar a construção de um sistema simples de fila de atendimento.

O sistema deve permitir que um operador administrativo cadastre clientes, adicione clientes a uma fila e chame o próximo cliente para atendimento.

Quando o cliente for chamado, o sistema deve atualizar o frontend em tempo real usando WebSocket e enviar um SMS para o cliente por meio de uma integração com a API da Directcall.

---

## 3. Tecnologias obrigatórias

### Backend

- Ruby.
- Framework Ruby à escolha do candidato, como Rails, Sinatra ou outro devidamente justificado.
- MySQL.
- API REST.
- WebSocket.
- Autenticação.
- Testes automatizados.

### Frontend

- TypeScript.
- Framework à escolha do candidato, como React, Vue, Angular ou outro devidamente justificado.
- Consumo da API REST.
- Comunicação via WebSocket.

### Infraestrutura

- Docker.
- Docker Compose.
- Variáveis de ambiente.
- README com instruções de execução.

---

## 4. Escopo funcional para o candidato

### 4.1 Autenticação administrativa

O sistema deve possuir uma área administrativa protegida por autenticação.

O candidato deve implementar:

- Login administrativo.
- Proteção das rotas administrativas.
- Controle de sessão ou token.
- Armazenamento seguro de senha.
- Identificação do usuário autenticado.

---

### 4.2 Cadastro de clientes

O sistema deve permitir o gerenciamento de clientes.

Funcionalidades mínimas:

- Criar cliente.
- Listar clientes.
- Visualizar detalhes de um cliente.
- Atualizar cliente.
- Remover cliente.

Informações mínimas esperadas de um cliente:

- Nome.
- Telefone.
- Documento.
- E-mail, quando informado.

O candidato deve definir as validações necessárias.

---

### 4.3 Controle da fila de atendimento

O sistema deve permitir que um cliente seja adicionado à fila de atendimento.

Funcionalidades mínimas:

- Adicionar cliente à fila.
- Listar fila atual.
- Consultar posição do cliente na fila.
- Chamar próximo cliente.
- Iniciar atendimento.
- Finalizar atendimento.
- Cancelar atendimento.

O sistema deve impedir inconsistências, como o mesmo cliente estar mais de uma vez aguardando atendimento na fila.

---

### 4.4 Atualização em tempo real

Sempre que a fila for alterada, o frontend deve ser atualizado automaticamente usando WebSocket.

Eventos esperados:

- Cliente adicionado à fila.
- Cliente removido ou cancelado da fila.
- Próximo cliente chamado.
- Atendimento iniciado.
- Atendimento finalizado.
- Alteração na posição dos clientes.

O candidato deve definir a estrutura dos eventos e justificar sua abordagem.

---

### 4.5 Envio de SMS

Quando o próximo cliente for chamado, o sistema deve enviar um SMS para o telefone cadastrado.

O envio deve ser feito por uma camada de integração com a API da Directcall (O acesso a api pode ser solicitado e a documentação pode ser vista em [docs.](https://docs.api.directcall.com.br/wiki/spaces/cloudapi/pages/950387/APIs+para+enviar+SMS+receber)).

Para fins de teste técnico, a API pode ser mockada, mas a estrutura deve estar preparada para uma integração real.

Requisitos esperados:

- Serviço separado para envio de SMS.
- Uso de variáveis de ambiente para dados da integração.
- Tratamento de sucesso e erro.
- Registro do resultado do envio.
- Não acoplar o envio de SMS diretamente ao controller.

Mensagem sugerida:

> Olá, chegou sua vez de ser atendido. Por favor, dirija-se ao atendimento.

---

## 5. Telas mínimas esperadas

### 5.1 Tela de login

A tela deve permitir que o usuário administrativo acesse o sistema.

Deve conter:

- Campo de e-mail ou usuário.
- Campo de senha.
- Botão de entrar.
- Tratamento visual de erro de autenticação.

---

### 5.2 Tela de clientes

A tela deve permitir gerenciar clientes.

Deve conter:

- Listagem de clientes.
- Cadastro de novo cliente.
- Edição de cliente.
- Remoção de cliente.
- Ação para adicionar cliente à fila.

---

### 5.3 Tela administrativa da fila

A tela deve permitir gerenciar o fluxo da fila.

Deve conter:

- Lista dos clientes aguardando.
- Posição atual na fila.
- Status do atendimento.
- Botão para chamar próximo.
- Botão para iniciar atendimento.
- Botão para finalizar atendimento.
- Botão para cancelar atendimento.

---

### 5.4 Tela pública ou de acompanhamento

A tela deve exibir a fila de atendimento em tempo real.

Deve conter:

- Clientes aguardando.
- Posição na fila.
- Cliente chamado em destaque.
- Atualização automática via WebSocket.

---

## 6. Documentação obrigatória

O candidato deve entregar um `README.md` contendo, no mínimo:

1. Visão geral do projeto.
2. Tecnologias utilizadas.
3. Como rodar o projeto com Docker.
4. Como configurar variáveis de ambiente.
5. Como executar migrations.
6. Como criar ou acessar um usuário administrativo inicial.
7. Como executar os testes.
8. Descrição dos principais endpoints.
9. Descrição dos eventos WebSocket.
10. Explicação da modelagem de dados criada.
11. Explicação das decisões técnicas.
12. Pontos de melhoria que seriam aplicados em produção.

Itens desejáveis:

- Arquivo OpenAPI ou Swagger.
- Collection do Postman ou Insomnia.
- Diagrama simples da arquitetura.
- Diagrama simples da modelagem de dados.
- Diagrama simples do fluxo da fila.

---

## 7. Entrega esperada

O candidato deve entregar um repositório Git contendo:

- Código do backend.
- Código do frontend.
- Migrations do banco de dados.
- Docker Compose.
- Arquivo de exemplo de variáveis de ambiente.
- README completo.
- Testes automatizados.
- Instruções de execução.

---

## 8. Restrições importantes para o candidato

O candidato deve construir sua própria modelagem de dados.

Não será fornecido:

- SQL pronto.
- Código-base.
- Diagrama de banco pronto.
- Estrutura obrigatória de tabelas.
- Payloads finais obrigatórios.

Esses pontos fazem parte da avaliação técnica.

O candidato deve justificar suas escolhas no README.

---

## 9. Critérios de avaliação

### 9.1 Arquitetura e organização — 20 pontos

Avaliar:

- Separação de responsabilidades.
- Organização entre controllers, services, models e camadas auxiliares.
- Clareza dos nomes.
- Baixo acoplamento.
- Facilidade de manutenção.
- Coerência na estrutura do projeto.

---

### 9.2 Modelagem de dados — 15 pontos

Avaliar:

- Coerência das entidades criadas.
- Relacionamentos corretos.
- Uso adequado de constraints.
- Uso adequado de índices.
- Capacidade de manter histórico da fila.
- Capacidade de registrar eventos importantes, como envio de SMS.
- Clareza da modelagem apresentada na documentação.

---

### 9.3 Backend Ruby — 20 pontos

Avaliar:

- Qualidade dos endpoints.
- Validações.
- Tratamento de erros.
- Autenticação.
- Segurança.
- Transações.
- Controle de concorrência ao chamar o próximo cliente.
- Testes automatizados.
- Clareza do código.

---

### 9.4 Frontend TypeScript — 15 pontos

Avaliar:

- Organização dos componentes.
- Uso adequado de TypeScript.
- Consumo da API REST.
- Consumo do WebSocket.
- Tratamento de loading e erro.
- Experiência de uso.
- Separação entre UI e serviços de comunicação.

---

### 9.5 WebSocket — 10 pontos

Avaliar:

- Atualização em tempo real funcionando.
- Eventos bem definidos.
- Tratamento de reconexão ou falha.
- Separação entre regra de negócio e emissão de evento.
- Sincronização correta entre backend e frontend.

---

### 9.6 Integração SMS — 10 pontos

Avaliar:

- Integração isolada em service/client próprio.
- Uso de variáveis de ambiente.
- Mock bem estruturado.
- Tratamento de falhas.
- Registro do resultado do envio.
- Código preparado para integração real.

---

### 9.7 Documentação — 10 pontos

Avaliar:

- README claro.
- Instruções de execução completas.
- Explicação da arquitetura.
- Explicação da modelagem.
- Explicação dos endpoints.
- Explicação dos eventos WebSocket.
- Clareza das decisões técnicas.

---

## 10. Pontos extras

O candidato pode receber pontos extras se implementar:

- Swagger ou OpenAPI.
- Testes de integração.
- Paginação na listagem de clientes.
- Filtro por status da fila.
- Auditoria de ações administrativas.
- Logs estruturados.
- Retry no envio de SMS.
- Controle de múltiplos guichês.
- CI com GitHub Actions.
- Separação entre tela pública e tela administrativa.
- Uso de Redis para suporte ao WebSocket ou filas internas.

---

## 11. Fluxo funcional esperado

1. Administrador acessa o sistema.
2. Administrador faz login.
3. Administrador cadastra um cliente.
4. Administrador adiciona o cliente à fila.
5. Frontend recebe atualização em tempo real.
6. Administrador chama o próximo cliente.
7. Sistema seleciona o próximo cliente da fila.
8. Sistema atualiza o status do cliente.
9. Sistema envia SMS ao cliente chamado.
10. Sistema atualiza o frontend via WebSocket.
11. Administrador inicia o atendimento.
12. Administrador finaliza o atendimento.
13. Sistema atualiza a fila novamente.

---

## 12. Enunciado resumido

Você deverá desenvolver um sistema simples de fila de atendimento.

O backend deve ser desenvolvido em Ruby, utilizando MySQL como banco de dados. O frontend deve ser desenvolvido em TypeScript.

O sistema deve possuir autenticação para usuários administrativos, CRUD de clientes, controle de fila de atendimento, atualização em tempo real via WebSocket e envio de SMS quando o cliente for chamado.

Quando um cliente for adicionado à fila, o frontend deve ser atualizado automaticamente. Quando o administrador chamar o próximo cliente, o sistema deve selecionar o primeiro cliente aguardando, alterar seu status, atualizar a fila em tempo real e enviar um SMS utilizando uma camada de integração com a API da Directcall.

A integração com SMS pode ser mockada, mas deve estar estruturada como se fosse uma integração real, utilizando service próprio, variáveis de ambiente, tratamento de erro e registro de logs.

O projeto deve conter documentação clara explicando como executar, como testar, quais endpoints existem, quais eventos WebSocket são usados, como o banco foi modelado e quais decisões técnicas foram tomadas.

A entrega deve ser feita por meio de um repositório Git contendo backend, frontend, migrations, Docker Compose e README.

---

**Directcall Telecom - Avaliação de Desenvolvedor**  
**directcall.com.br**  
**Versão 1.0**
