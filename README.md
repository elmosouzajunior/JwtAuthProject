# 🔒 JwtAuthProject: Autenticação JWT com ASP.NET Core 8 Web API

## 📝 Descrição do Projeto

Este projeto de portfólio demonstra a implementação completa de um sistema de **Autenticação e Autorização** baseado em **JSON Web Tokens (JWT)** em uma aplicação **ASP.NET Core 8 Web API**.

O objetivo é fornecer uma base sólida e funcional para proteger endpoints de API, utilizando o padrão JWT para validar a identidade do usuário de forma *stateless* (sem estado). O projeto utiliza o `Microsoft.AspNetCore.Identity` para gerenciamento de usuários e o `JwtBearer` para a validação dos tokens.

## 🚀 Funcionalidades

*   **Registro de Usuário (`/api/Auth/register`)**: Criação de novos usuários utilizando o `UserManager` do ASP.NET Core Identity.
*   **Login e Geração de Token (`/api/Auth/login`)**: Autenticação do usuário e geração de um JWT contendo as *claims* necessárias.
*   **Serviço de Geração de Token (`JwtService`)**: Lógica encapsulada para criação e assinatura do JWT.
*   **Proteção de Endpoint (`/api/Protected`)**: Demonstração de um recurso que só pode ser acessado com um token JWT válido, utilizando o atributo `[Authorize]`.
*   **Configuração do Swagger**: Integração do Swagger UI com o esquema de segurança `Bearer Token` para facilitar os testes.

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Versão | Descrição |
| :--- | :--- | :--- |
| **.NET** | 8.0 | Framework principal para o desenvolvimento da API. |
| **ASP.NET Core Web API** | 8.0 | Template base para a API RESTful. |
| **Microsoft.AspNetCore.Identity** | 8.0.0 | Gerenciamento de usuários, senhas e roles. |
| **Microsoft.AspNetCore.Authentication.JwtBearer** | 8.0.0 | Middleware para validação de tokens JWT. |
| **Entity Framework Core** | 8.0.0 | ORM utilizado com banco de dados em memória (`InMemory`) para testes. |
| **Swagger/OpenAPI** | 6.5.0+ | Documentação e interface de teste da API. |

## ⚙️ Pré-requisitos

Para rodar este projeto, você precisará ter instalado:

*   **.NET 8 SDK**
*   **Microsoft Visual Studio 2022** (ou Visual Studio Code com as extensões C# necessárias)

## 💻 Instalação e Configuração

### 1. Clonar o Repositório

```bash
git clone https://github.com/seu-usuario/JwtAuthProject.git
cd JwtAuthProject
```

### 2. Abrir no Visual Studio

1.  Abra o **Microsoft Visual Studio 2022**.
2.  Vá em **Arquivo** > **Abrir** > **Projeto/Solução** e selecione o arquivo `JwtAuthProject.csproj`.

### 3. Instalar Pacotes NuGet

Os pacotes necessários já estão referenciados no arquivo `.csproj`, mas caso seja necessário restaurá-los:

1.  Clique com o botão direito na solução e selecione **"Restaurar Pacotes NuGet"**.
2.  Alternativamente, no terminal do Visual Studio (Package Manager Console), execute:
    ```powershell
    Update-Package -Reinstall
    ```

### 4. Configuração do Token Secreto

O token secreto está configurado no arquivo `appsettings.json`. **Em um ambiente de produção, este valor deve ser armazenado em um local seguro (como Azure Key Vault ou Variáveis de Ambiente).**

```json
// appsettings.json
"JwtSettings": {
  "Secret": "UmaChaveSecretaMuitoLongaEComplexaParaOProjetoDeAutenticacaoJWT",
  "Issuer": "JwtAuthProject",
  "Audience": "JwtAuthProjectClient",
  "TokenExpirationInMinutes": 60
}
```

## 🧪 Como Testar

O projeto é configurado para ser testado via **Swagger UI**.

### 1. Iniciar a Aplicação

1.  No Visual Studio, certifique-se de que o projeto `JwtAuthProject` está selecionado.
2.  Pressione **F5** ou clique no botão **"IIS Express"** para iniciar a aplicação. O Swagger UI será aberto automaticamente no seu navegador.

### 2. Fluxo de Teste

| Passo | Endpoint | Método | Ação |
| :--- | :--- | :--- | :--- |
| **1 (Falha)** | `/api/Protected` | `GET` | Tente executar sem autenticação. **Resultado:** `401 Unauthorized`. |
| **2 (Login)** | `/api/Auth/login` | `POST` | Use as credenciais de teste (criadas automaticamente no `Program.cs`): `Email: teste@exemplo.com`, `Password: Senha@123`. **Resultado:** `200 OK` e o **Token JWT**. |
| **3 (Autorizar)** | **Botão "Authorize"** | N/A | Clique no botão **"Authorize"** no topo do Swagger UI e insira o token copiado no formato `Bearer <SEU_TOKEN>`. |
| **4 (Sucesso)** | `/api/Protected` | `GET` | Execute novamente. **Resultado:** `200 OK` e os dados protegidos. |

## 📞 Contato

Se você tiver alguma dúvida ou sugestão sobre o projeto, sinta-se à vontade para entrar em contato:

*   **Seu Nome/GitHub:** [Seu Nome de Usuário do GitHub]
*   **LinkedIn:** [Seu Perfil do LinkedIn]
*   **Email:** [Seu Email]

---
*Este projeto foi desenvolvido como parte de um portfólio de estudos em .NET.*
