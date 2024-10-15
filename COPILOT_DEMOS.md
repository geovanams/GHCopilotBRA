<!-- Generate a focumentation with a list of sample prompt to demo github copilot capacities -->

# Laboratório Módulo: PLUS - Explorando Github Copilot

## Pré-Requisitos:

- Conta GitHub
- IDE com suporte GitHub Copilot (VS Code, Visual Studio, JetBrains, Vim/Neovim) **Para esse laboratório estaremos usando VS Code**
- [Extensao GitHub Copilot e GitHub Copilot Chat](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)
- Clonar repositório:

Abra o terminal e cole:  

   ```git
   git clone https://github.com/geovanams/github-copilot-demo.git
   cd github-copilot-demo
   code .
   ```
  
## VSCode Shortcuts (Para ir usando durante as atividades)

Quando você começar a realizar os passos dessa atividade digitando prompts e o copilot gerar propostas, você poderá usar os seguintes atalhos para interagir com o Copilot:
- `tab` para aceitar inteiramente a sugestão atual (`mais comum`)
- `ctrl + seta para a direita` para aceitar palavra por palavra a sugestão (`para uso parcial`)
- `alt + ^` para passar para a próxima sugestão
- `shift + tab` para voltar à sugestão anterior
- `ctrl+enter` para exibir o painel do copiloto

Se você não consegue se lembrar, basta passar o ponteiro sobre uma sugestão para que ela apareça.

# Atividades

## Natural Language Translations

GitHub Copilot consegue traduzir linguagem natural e para trazer as sugestões ele considera a contexto do seu código.

- Abra o arquivo `album-viewer/lang/translations.json`
```json
[
    {
        "language": "en",
        "values": {
            "main-title": "Welcome to the world of the future",
            "main-subtitle": "The future is now with copilot",
            "main-button": "Get started"
        }
    }
]
```

- Comece a adicionar um novo bloco adicionando um "," após o último "}" e pressione enter.

Nesse primeiro momento possa ser que ele não traga de imediato uma sugestão, pois é necessário passar mais contexto. Então comece a inserir um novo objeto com o valor da  propriedade "language" como "pt" e após a vírgula pressione Enter. Exemplo:

  ```json
  {
    "language":"pt",
  }
  ```
<br>

## Code Generation

**Gerando código a partir do prompt**

- Abra o arquivo `album-viewer/utils/validators.ts`e inicie com o prompt:
```ts
// validar data de um input string e converter para um objeto do tipo Data
```

- O Copilot também pode ajudá-lo a escrever `padrões RegExp`. Tente :

```ts
// Funçao que valida o formate de uma string de um endereço IPV6
```
<br>

Você pode explorar as alternativas usando o atalho `ctrl+enter` para exibir mais sugestões.

## Infra As Code

O Copilot também pode ajudá-lo a escrever infraestrutura como código. Ele pode gerar código para `Terraform, ARM, Bicep, Pulumi, etc...` e também `arquivos de manifesto do Kubernetes`.

### Bicep
- Abra o arquivo `iac/bicep/main.bicep` in `iac/bicep` e comece a digitar prompts no final do arquivo para adicionar novos recursos:
  
```js
// Container Registry
```

### Terraform
- Abra o arquivo `iac/app.tf`e comece a digitar prompts no final do arquivo para adicionar novos recursos:

```yml
# Azure Congitive Services Custom Vision resource
```

## Gerar Comentários Git Commit

- Na aba Soure Control do VS Code adicione algum arquivo para stage e selecione o ícone de estrelas para gerar mensagens de commit.


## Documentação

O Copilot pode entender um prompt em linguagem natural e gerar código e, como é apenas uma linguagem, também pode "entender o código e explicá-lo em linguagem natural" para ajudá-lo a documentar seu código.


### standardized documentation comment (JavaDoc, JsDoc, etc...)

Para este, para acionar a geração de comentários da documentação, você precisa respeitar o formato específico dos comentários:
-  `/**` (Para JS/TS) no arquivo `albums-viewer/utils/validators.js` por exemplo
- `///` Para C# no arquivo `AlbumController.cs` no método httpGet{id} por exemplo

```cs
/// <summary>
/// function that returns a single album by id
/// </summary>
/// <param name="id"></param>
/// <returns></returns>
[HttpGet("{id}")]
public IActionResult Get(int id)
```

### Markdown e html documentation

Ele pode gerar código markdown e html e acelerar a gravação de seus arquivos readme.md como este, por exemplo.

Você pode testar usando o arquivo demo.md na raiz do projeto e começando a digitar o seguinte prompt:
```md
# Github Copilot documentation
This documentation is generated with Github Copilot to show what the tool can do.

##
```

# Atividades de GitHub Copilot Chat

GitHub Copilot é uma IA generativa e, portanto, perfeita para gerar código, mas possui poderosos recursos de análise de seu código que podem ser usados ​​em diversos casos para melhorar a qualidade do código, como: encontrar problemas de segurança, más práticas em seu código e gerar uma correção, refatorar e adicionar comentários ao código legado, gerar testes, etc...

## Iniciar com Copilot Chat

Instale a extensão GitHub Copilot Chat em sua IDE.

Depois que o Copilot Chat estiver configurado, você poderá começar a usá-lo:

- Acessando a visualização de bate-papo na barra de ferramentas esquerda do seu IDE (ícone de bate-papo)
- Pressionando Ctrl + Shift + i atalho para uma pergunta rápida embutida no chat

O primeiro é uma versão fixa, muito útil para manter o chat aberto e tirar dúvidas ao Copilot. O segundo é uma maneira rápida de fazer uma pergunta, obter uma resposta e iniciar comandos.

## Chat View

A visualização de chat oferece uma experiência de chat completa, integrada como qualquer outra visualização de ferramenta em seu IDE. Assim que a visualização estiver aberta, você poderá começar a conversar com o Copilot como seu treinador pessoal de código. Ele mantém o histórico da conversa e você pode fazer perguntas relacionadas às respostas anteriores. Ele também fornece sugestões para perguntas ao longo do caminho. Você pode:

- Faça perguntas gerais sobre codificação em qualquer idioma ou práticas recomendadas
- Peça para gerar ou corrigir o código relacionado ao arquivo atual e injetar o código diretamente no arquivo

- Comece criando um script node:

```
Node script calculator
```
- No código gerado, passe o mouse no topo e clique em add file. Será criado um arquivo com o código gerado. Salve o arquivo.

## Code Explanation and documentation

- Com o arquivo aberto, vá ao chat e peça para ele uma explicação do código, você pode usar prompts como:

```
Me explique esse código
```
```
Pode gerar uma função que retorne um número entre 1 and 10?
```

- Você também pode selecionar o código inteiro ou apenas um trecho, clicar com botão direito, clique em copilot e então explain. Será gerado uma explicação que aparecerá no chat.

- Com o chat, você também pode pedir para ele gerar documentação:

```
Generate documentation comments for this code
```

## Slash Commands

Para ajudar ainda mais o Copilot a fornecer respostas mais relevantes, você pode escolher um tópico para suas perguntas por meio de “comandos de barra”.

Você pode preceder suas entradas de bate-papo com um nome de tópico específico para ajudar o Copilot a fornecer uma resposta mais relevante. Ao começar a digitar /, você verá a lista de tópicos possíveis:

- `/explain` Explica passo a passo como funciona o código selecionado.
- `/fix` Propõe uma correção para os bugs no código selecionado.
- `/help` Imprime ajuda geral sobre GitHub Copilot.
- `/tests` gera testes unitários para o código selecionado.
- `/vscode` Perguntas sobre comandos e configurações do VS Code.
- `/clear` Limpa a sessão.

Com um arquivo aberto ou código selecionado, teste alguns desses slash.

## Usar Agents

Os agentes são como especialistas que podem ajudá-lo em tarefas específicas. Você pode mencioná-los no chat usando o símbolo @. Como:

- `@workspace`: este agente tem conhecimento sobre o código em seu espaço de trabalho e pode ajudá-lo a navegar nele, encontrando arquivos ou classes relevantes. O agente @workspace usa um meta prompt para determinar quais informações coletar do workspace para ajudar a responder sua pergunta.

- `@vscode`: Este agente conhece comandos e recursos do próprio editor do VS Code e pode ajudá-lo a usá-los.

Abra o GitHub Copilot e faça uma pergunta sobre o projeto usando @Workspace:

```
What is about this project ?
```
Copilot chat também pode te ajudar a criar um projeto completo:

```
@workspace /new create a new asp.net core 6.0 project, with three views Index, Users and products.
```
Ele vai criar uma estrutura de um projeto completo. Você pode clicar em **Create Workspace** e ele criará um workspace completo contendo o código gerado.

## Segurança de código

Copilot pode ajudar a encontrar problemas de segurança em seu código e sugerir correções. Também pode ajudar a encontrar bad practices e corrigi-lás.

Abra o arquivo album-api/Controllers/UnsecuredController.cs e insira o seguinte prompt no chat:
```
Esse código possui problemas de segurança?
```
O Copilot vai retornar os problemas de segurança identificados e sugestões de correção. Mas você também pode pedir especificamente para ele sugerir as correrções:
```
Pode me recomendar uma solução?
```

## Traduzir código de uma linguagem para outra

Copilot pode entender e gerar linguagem natural e linguagem de código, combinando você pode usar para `traduzir pedaços de código de una linguagem para outra`.

- Abra o arquivo Validators.ts e solicite ao chat para traduzir para linguagem c:

```
translate to C
```

- Copilot também pode ajudar a traduzir códigos de linguagem legadas, porém como ele usa os repositórios públicos do GitHub, linguagens como Java, Javascript e .NET possuem maiores quantidades de código disponível, então a acertividade de retorno para essas linguagens são maiores.

- Com o arquivo legacy/albums.cbl aberto, vamos traduzir para Python,  digite no chat:
```
translate to python
```

Prontinho! Aqui você viu um pouco de como o GitHub Copilot e GitHub Copilot Chat podem ajudar a impulsionar a produtividade no fluxo de desenvolvimento. Continue a explorar essas funcionalidades para aplicar em seus cenários de desenvolvimento diário!

Parabéns por finalizar a última atividade do curso GitHub4Women!! 💜







