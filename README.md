## 🔹Estudos em Automação utilizando Cypress

Finalizei meu primeiro projeto de estudos sobre **Automação de Testes E2E**. O intuito desse projeto é a criação de automações, simulando o comportamento real de usuários, ao realizar o cadastro e login no site da Adopet e validar o funcionamento da aplicação, levanto em consideração comportamentos normais e atípicos do usuário.

## 🛠️ Tecnologias utilizadas

O estudo foi feito utilizando ferramentas como:

- Visual Studio Code
- Node.js
- Git
- Cypress
- Cypress Cloud
- DevTools
- Microsoft Edge

As linguagens utilizadas nesse projeto foram:

- JavaScript
- JSON
- Markdown (para documentações e roteiro de testes)

## ℹ️ Informações importantes 

🚨 No arquivo `api-mensagens.cy.js` contém uma request, onde o método chamado `headers: Cypress.env()` utiliza um ID de identificação único que expira. Para executar o teste é necessário atualizar esse ID no arquivo `cypress.env.json`.

````js
describe('Api Adopet', () => {
    it('Mensagens da API', () => {
        cy.request({
            method: 'GET',
            url: 'https://adopet-api-i8qu.onrender.com/mensagem/11643cd6-7112-415b-95d2-07904b0d1a1c',
            // Atualizar o ID antes de executar o teste.
            headers: Cypress.env() 
        }).then((res) => {
            expect(res.status).to.equal(200);
            expect(res.body).is.not.empty;
            expect(res.body).to.have.property('msg');
        })
    })
})
````

1. O ID é o token de identificação gerado no momento do login do usuário no sistema da aplicação web. Ele fica registrado no Armazenamento Local e pode ser localizado pelo DevTools.

![Token no Armazenamento Local](/imagens/token-armazenamento-local.png)

2. Após copiar o token, é necessário substitui-lo no arquivo `cypress.env.json`. 

````json
{
    "authorization": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMTY0M2NkNi03MTEyLTQxNWItOTVkMi0wNzkwNGIwZDFhMWMiLCJhZG9wdGVyTmFtZSI6IkFuYSBkZSBKZXN1cyIsImlhdCI6MTc1MzQ2ODk2MCwiZXhwIjoxNzUzNzI4MTYwfQ.vd_6yZMUZvx0QegrYePLD4FF0O96Cpb3OooDi_656V0"
}
````

Depois de alterar o token, lembre-se de salvar as alterações antes de rodar os testes.

## ✅ Como executar os testes

Para utilizar o projeto é necessário seguir as etapas abaixo:

- Clonar o repositório para o seu computador
- Instalar os softwares necessários:
    - Verificar o tópico `Tecnologias utilizadas` desse docuemnto
- Instalar as dependências com `npm install`
- Verificar o tópico `Informações importantes` desse documento
- Executar o comando `npx cypress run` no terminal do VS Code

## 👉 Contribuição

Como você pode colaborar com esse projeto?

- Caso queira contribuir para esse projeto de estudos com alguma melhoria, basta criar um `Pull request` com suas alterações.

- Caso encontre qualquer problema e queira colaborar, basta abrir um `Issue` para reportar o ocorrido e sugerir uma melhoria.

## 🔗 Referências

O estudo foi realizado a partir do curso **Testes E2E com Cypress** disponível na plataforma de ensino [Alura](https://www.alura.com.br/).

Outros materiais e exemplos, podem ser acessados através do [GitHub da Alura](https://github.com/alura-cursos/curso-cypress).
