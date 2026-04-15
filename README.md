# Desafio Prático: Variáveis e Escopos no GitHub Actions

## Estrutura do Workflow

O workflow foi dividido em dois jobs principais:

### build_app

Responsável por testar e demonstrar o uso de variáveis:

* Uso de variáveis em diferentes escopos
* Teste de visibilidade entre steps
* Uso de variáveis padrão do GitHub
* Geração de valor dinâmico (hash aleatório)

---

### deploy_app

Responsável por simular um deploy:

* Acesso a variáveis do repositório (`vars`)
* Acesso a secrets (`secrets`)
* Demonstração de segurança (ocultação de dados sensíveis)

---

## Resultados Obtidos

Durante a execução do workflow:

* Variáveis globais, de job e de step funcionaram corretamente
* A variável `STEP_TEMP` não foi acessível fora do step (comportamento esperado)
* Variáveis padrão exibiram corretamente:

  * Usuário
  * Repositório
  * Sistema operacional
* Um valor aleatório foi gerado e utilizado com sucesso
* A variável `URL_AMBIENTE` foi exibida normalmente
* O secret `API_TOKEN_PROD` foi ocultado como `***`

---

## Perguntas de Reflexão:

### Por que o secret aparece como ***?

Porque o GitHub oculta automaticamente valores de secrets nos logs por segurança, evitando a exposição de dados sensíveis.

---

### O job `deploy_app` consegue acessar a variável `BUILD_VERSION`?

Não.

Cada job roda em um ambiente separado (runner diferente), portanto as variáveis não são compartilhadas automaticamente entre eles.
