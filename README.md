# LojaApi

API REST desenvolvida em ASP.NET Core com Entity Framework Core e SQLite, como projeto acadêmico da disciplina **Tópicos Especiais** da Universidade Positivo.

## Tecnologias

- .NET 8
- ASP.NET Core (Minimal API)
- Entity Framework Core 8
- SQLite
- Swagger / OpenAPI

## Estrutura do Projeto

```
LojaApi/
├── Controllers/
│   ├── ProdutoController.cs
│   ├── FornecedorController.cs
│   └── VendedorController.cs
├── Data/
│   └── AppDbContext.cs
├── Models/
│   ├── Produto.cs
│   ├── Fornecedor.cs
│   └── Vendedor.cs
├── Migrations/
├── appsettings.json
└── Program.cs
```

## Entidades

### Produto
| Campo | Tipo |
|-------|------|
| Codigo | int (PK) |
| Nome | string |
| Descricao | string |
| Preco | decimal |

### Fornecedor
| Campo | Tipo |
|-------|------|
| Codigo | int (PK) |
| Nome | string |
| Cnpj | string |
| Email | string |
| Telefone | string |

### Vendedor
| Campo | Tipo |
|-------|------|
| Codigo | int (PK) |
| Nome | string |
| Email | string |
| Telefone | string |
| Salario | decimal |

## Endpoints

### Produto
| Método | Rota | Descrição |
|--------|------|-----------|
| GET | /api/produto | Lista todos os produtos |
| POST | /api/produto | Cadastra um produto |
| PUT | /api/produto/{codigo} | Atualiza um produto |
| DELETE | /api/produto/{codigo} | Remove um produto |

### Fornecedor
| Método | Rota | Descrição |
|--------|------|-----------|
| GET | /api/fornecedor | Lista todos os fornecedores |
| POST | /api/fornecedor | Cadastra um fornecedor |
| PUT | /api/fornecedor/{codigo} | Atualiza um fornecedor |
| DELETE | /api/fornecedor/{codigo} | Remove um fornecedor |
| GET | /api/fornecedor/nome/{nome} | Busca fornecedores pelo nome |

### Vendedor
| Método | Rota | Descrição |
|--------|------|-----------|
| GET | /api/vendedor | Lista todos os vendedores |
| POST | /api/vendedor | Cadastra um vendedor |
| PUT | /api/vendedor/{codigo} | Atualiza um vendedor |
| DELETE | /api/vendedor/{codigo} | Remove um vendedor |
| GET | /api/vendedor/salario/{valor} | Busca vendedores com salário maior que o valor |

## Como executar

### Pré-requisitos

- [.NET 8 SDK](https://dotnet.microsoft.com/download)
- [dotnet-ef](https://learn.microsoft.com/en-us/ef/core/cli/dotnet)

### Instalando a ferramenta dotnet-ef

```bash
dotnet tool install --global dotnet-ef --version "8.*"
```

### Clonando e executando

```bash
git clone <url-do-repositorio>
cd LojaApi

# Restaurar pacotes
dotnet restore

# Aplicar migrations e criar o banco
dotnet ef database update

# Rodar a API
dotnet run
```

### Acessar o Swagger

```
http://localhost:5237/swagger
```

## Banco de dados

O projeto utiliza SQLite. O arquivo `loja.db` é gerado automaticamente na raiz do projeto ao executar `dotnet ef database update`.

Para visualizar os dados via terminal:

```bash
sqlite3 loja.db "SELECT * FROM Fornecedores;"
sqlite3 loja.db "SELECT * FROM Vendedores;"
sqlite3 loja.db "SELECT * FROM Produtos;"
```