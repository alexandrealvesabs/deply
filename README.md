Parte 1: Criar a API com ASP.NET Core
1. Instalar o .NET SDK
Antes de começarmos, você precisa ter o .NET SDK instalado. Você pode baixar a versão mais recente do .NET SDK.

2. Criar um Novo Projeto de API
Abra o terminal ou o Prompt de Comando.
Execute o seguinte comando para criar um novo projeto de API:
dotnet new webapi -n MinhaApi
Navegue até o diretório do projeto:
cd MinhaApi
3. Criar um Controller Simples
Abra o projeto em seu editor de código favorito (por exemplo, Visual Studio, Visual Studio Code).

No diretório Controllers, crie um novo arquivo chamado HelloController.cs e adicione o seguinte código:

using Microsoft.AspNetCore.Mvc;

namespace MinhaApi.Controllers
{
    [ApiController]
    [Route("[controller]")]
    public class HelloController : ControllerBase
    {
        [HttpGet]
        public ActionResult<string> Get()
        {
            return "Hello, World!";
        }
    }
}
4. Testar a API Localmente
No terminal, execute o seguinte comando para iniciar a aplicação:
dotnet run
Acesse https://localhost:5001/hello no seu navegador ou use uma ferramenta como Postman para testar. Você deve ver a mensagem "Hello, World!".
Parte 2: Criar o Deploy no Azure
1. Criar uma Conta no Azure
Se você ainda não tem uma, crie uma conta gratuita no Azure.

2. Criar um Grupo de Recursos
Acesse o Portal do Azure.
Clique em "Criar um recurso".
Selecione "Grupo de Recursos".
Dê um nome ao grupo de recursos (por exemplo, MeuGrupoDeRecursos) e escolha uma região.
Clique em "Revisar + Criar" e depois em "Criar".
3. Criar um App Service
Clique em "Criar um recurso".
Selecione "App Service".
Preencha as informações:
Nome da Aplicação: Um nome único (por exemplo, minha-api-2023).
Publicar: Selecione "Código".
Pilha de Runtime: Escolha .NET Core.
Região: Escolha a mesma região do grupo de recursos.
Plano de Serviço: Escolha um plano gratuito (ou o que preferir).
Clique em "Revisar + Criar" e depois em "Criar".
4. Configurar a API para Deploy
Publicar Configurações: No Visual Studio ou Visual Studio Code, abra o arquivo launchSettings.json localizado em Properties e certifique-se de que a configuração de launchUrl está apontando para o endpoint correto.
5. Publicar a API
Usando Visual Studio:

No Visual Studio, clique com o botão direito do mouse no projeto e selecione "Publicar".
Selecione "Azure" e depois "App Service".
Escolha a assinatura do Azure e o App Service que você criou.
Clique em "Publicar". O Visual Studio irá compilar e fazer o deploy automaticamente.
Usando Azure CLI:

Abra o terminal e faça login na sua conta do Azure:
az login
Navegue até o diretório da sua API:
cd /caminho/para/sua/MinhaApi
Execute o comando para fazer o deploy:
az webapp up --name minha-api-2023 --resource-group MeuGrupoDeRecursos --runtime "DOTNETCORE|6.0"
Certifique-se de substituir minha-api-2023 e MeuGrupoDeRecursos pelos nomes que você definiu.
Parte 3: Testar a API no Azure
Após a publicação, você receberá uma URL para acessar sua API.
Acesse https://minha-api-2023.azurewebsites.net/hello no seu navegador ou use o Postman para testar. Você deve ver a mensagem "Hello, World!".
Parte 4: Monitorar e Gerenciar
No portal do Azure, você pode acessar seu App Service para monitorar o desempenho da aplicação.
Utilize o Application Insights para monitoramento avançado, se necessário.
Dicas Finais
Segurança: Considere implementar autenticação e autorização.
CORS: Habilite CORS se sua API for consumida por aplicações de diferentes origens.
Escalabilidade: Escolha um plano que atenda às suas necessidades de escalabilidade.
