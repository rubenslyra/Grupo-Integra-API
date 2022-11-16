# Grupo-Integra-API | <img src="https://user-images.githubusercontent.com/37023108/202020758-685c1737-34f8-48e9-a16b-56cd9fd51547.jpg" alt="logo-solution" width="55px" line-height="1.5rem">

API de gestão e controle de dados empresariais. No exemplo, a API deve fornecer dados de performances das marcas e empresas pertencentes ao Grupo Integra, uma multimarcas fake criado para o exmeplo.

## Em Desenvolvimento

ROTEIRO DE CRIAÇÃO E EXECUÇÃO

1) CRIAR E CONFIGURAR O PROJETO

Criar projeto:
```CSharp
dotnet new webapi IntegraBG_API -f net6.0
```
Pacotes:
```CSharp
dotnet add package Microsoft.AspNetCore.Authentication
dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer
```

Criar classe Settgins.cs
- conteúdo: SecretKey = 'valorDaChave';

Encriptação da chave no arquivo Program.cs:
```CSharp

var key	= Encogind.ASCII.GetBytes(Settings.Secret);
Services.AddAuthentication(x => 
{
x.DefaultAuthenticationScheme = JwtBearerDefaults.AuthenticationScheme;
x.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
})
.Add.JwtBearer(x => {
x.RequireHttpsMetadata = false;
x.SaveToken = True;
x.TokenValidationParameters = new TokenValidationParameters
{
ValidateIssuerSigningKey = true;
IssuerSigningKey = new SymmetricSecurityKey(key),
ValidateAudience = false
};
});
```
Adicionar abaixo da chamada da função 'UseRouting();':

- [ ] app.UseAuthentication();
- [ ] app.UseAuthorization();


2) CRIAR USUARIO PARA TESTES

Criar classe User.cs dentro do diretório Models/
Como cada modelo desse projeto depende de um repositório dedicado,
devemos criar a classe UserRepository.cs do diretório 'Respositories/'

- [ ] Estrutura da classe UserRepository.cs [anexo]
- [ ] Estrutura da classe User.cs [anexo]


3) CRIAR SERVICES
Vamos criar o TokenService.cs dentro da pasta Services.
Em seguida, devemos implementar o método GenerateToken, que contém o IEnumerable<Clains>

4) CRIAR CONTROLLERS
A primeira classe será a LoginController.cs.








_______
⚠️Importantes!⚠️
Cuidado ao armazenar o token e localstorage
