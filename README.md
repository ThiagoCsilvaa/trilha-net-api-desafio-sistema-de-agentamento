# Trilha .NET API - Desafio Sistema de Agendamento

API em **.NET 6** para gerenciamento de tarefas, criada como desafio do curso/trilha.

## Tecnologias

- .NET 6
- C#
- Entity Framework Core (EF Core)
- SQL Server (LocalDB / Express)
- Swagger (OpenAPI) para documentação e teste de endpoints

## Funcionalidades

- Criar, listar, atualizar e deletar tarefas
- Buscar tarefas por:
  - Id
  - Título
  - Data
  - Status (EnumStatusTarefa)
- EnumStatusTarefa como string (Pendente / Finalizado)

## Estrutura do Projeto

- **Controllers/TarefaController.cs** → Contém todos os endpoints da API
- **Models/Tarefa.cs** → Modelo da entidade Tarefa
- **Models/EnumStatusTarefa.cs** → Enum de status da tarefa
- **Context/OrganizadorContext.cs** → DbContext para EF Core
- **Migrations/** → Pasta gerada pelo EF Core com a migration `InitialCreate`

## Passo a passo para rodar localmente

1. **Clonar o repositório**
```bash
git clone https://github.com/ThiagoCsilvaa/trilha-net-api-desafio-sistema-de-agentamento.git

2. Abrir pasta do projeto no VS Code
cd trilha-net-api-desafio-sistema-de-agentamento

3. Ajustar connection string em appsettings.Development.json
"ConnectionStrings": {
  "ConexaoPadrao": "Server=localhost\\SQLEXPRESS;Database=TrilhaDb;Trusted_Connection=True;TrustServerCertificate=True;MultipleActiveResultSets=true"
}

4. Garantir que o ambiente seja Development
$Env:ASPNETCORE_ENVIRONMENT = 'Development'

5.Restaurar pacotes
dotnet restore

6.Criar migration e atualizar banco
dotnet ef migrations add InitialCreate
dotnet ef database update

7.Rodar a aplicação
dotnet run --urls "http://localhost:5000"

8.Testar endpoints
http://localhost:5000/swagger


