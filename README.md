<h1 align="center">Testes Automatizados com TestCafe</h1>

- TestCafe é uma ferramenta NodeJS para automatização de testes em Javascript e Typescript.
  
- Pode ser utilizando em Linux, Mac e Windows, suporta navegadores de desktop, dispositivos móveis, remotos e na nuvem.

- Você pode executar em um console é seus relatórios podem ser visualizados na interface de um sistema de CI.

### Documentação
- [Documentação Oficial do TestCafe](https://devexpress.github.io/testcafe/documentation/getting-started/)

### Instalação
 
Primeiro vamos instalar o NVM (essa forma que vou mostrar como instalar é em Linux e Mac)

```sh
$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```
Para instalar o NVM no Windows tem as instruções nesse [link](https://github.com/coreybutler/nvm-windows) 

Após instalar o NVM, devemos selecionar a versão do Node.js que irá utilizar (digite no terminal)

```sh
nvm install 12.16.3
```
Verifique a versão do Node.js digitando no seu terminal:

```sh
node --version
```
No seu terminal deverá retornar a versão:

```sh
v12.16.3
```

<h1 align="center">E agora vamos ver a mágica de como e realizar teste automatizado</h1>

Após todas as configurações necessárias vamos digitar no terminal:

```sh
npm install -g testcafe
```
E irá ser realizada a instalação do TestCafe, as vezes pode demorar um pouquinho, não se preocupe.

Agora vamos criar um diretório com o nome "tests" e dentro dele vamos digitar o comando no terminal:

```sh
npm init -y
```
E irá ser criado um `${package.json}`

E dentro do seu diretório vamos criar um arquivo com o nome "login.test.js" e dentro dele vamos colocar esse código:

```sh
import { Selector } from 'testcafe';

fixture `Testes de Login`
    .page `https://the-internet.herokuapp.com/login`;

test('Teste de login positivo', async t => {
    await t
    .typeText('#username', 'tomsmith')
    .typeText('#password', 'SuperSecretPassword!')
    .click('.fa-sign-in')
    .expect(Selector('#flash').innerText).contains('You logged into a secure area!');
});
```

Mas precisamos antes analisar e compreender o que foi escrito nesse código:

- Nós vamos importar a função "Selector" da biblioteca "testcafe"
- Vamos declarar o objeto que vamos testar é também será declaramos a url que será testada
- Nesse teste damos o nome de "Teste de Login Positivo"
- No "typeText" demos a instrução que é o comando necessário para inserir um texto no elemento "#username" e em seguida fazemos a mesma coisa com o seletor "#password"
- O elemento ".fa-sign-in" é o botão de login, e o nosso teste dirá que o elemento "#flash" deve conter o texto "You logged into a secure area!"

Salve o arquivo executando o atalho:

```sh
crtl + s
```
Agora vamos executar nosso teste, irei ensinar como executa o comando se você usa o Google Chrome, Firefox ou Safari como navegador:

### Google Chrome 

```sh
testcafe chrome tests/login.test.js
```
### Firefox 

```sh
testcafe firefox tests/login.test.js
```
### Safari

```sh
testcafe safari tests/login.test.js
```
Pode demorar um poquinho a rodar, ele irá abrir a página e vai executar mágica e você vai ver como é um teste automatizado! :D

### Creditos 

- Primeiramente o meu amigo havia mostrado a como realizar a primeira parte de teste automatizados também, ele é QA Senior e Community Manager da PerifaCode vou deixar o link dos artigos dele aqui [JuniorRocha](https://jrocha.dev/)

### Observações

- Você pode usar esse repositório para poder montar seu ambiente de testes
- Eu vou usar esse repositório para tentar ajudar outras pessoas que estão aprendendo sobre testes, então pretendo sempre que der atualizar esse repositório com algo bacana
- Esse repositório tem como objetivo compartilhar conhecimento e contribuir para profissionais da área de testes de software e coisas relacionadas para também dar visibilidade a esses profissionais.
- Lembre-se sempre que testar é importante, mantém a qualidade, segurança e outras coisas importantes para aplicações, nunca deixe de realizar testes!

Até a próxima é boa caças a bugs é realização de testes!
