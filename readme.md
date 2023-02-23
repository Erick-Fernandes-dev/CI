# Integração Contínua - CI

**O que CI?**
  - Sempre que falamos em CI estamos nos referindo ao processo de juntar o código antigo com novas funcionalidades de forma automática, realizando testes e compilando o código para evitar problemas de lógica ou funcionalidades pré-existentes.
  - Também temos as pipelines, que são as rotinas que devemos executar com todos os comandos que veremos mais à frente. As pipelines funcionam como um script ou um passo a passo, em que os códigos são executados em sequência.

**OBS! O que é troubleshooting?**
> **O troubleshooting consiste em ações que visam a descoberta, análise e diagnóstico de problemas, com o objetivo de reparar falhas em sistemas ou processos. É um termo muito difundido na área de tecnologia para reparo de falhas em sistemas ou na própria infraestrutura de uma organização.**

### Resumo do Módulo

- Ver o que será necessário para executar a aplicação, sendo que no nosso caso é necessário o Docker e o Go, sendo o Docker para o nosso banco de dados e o Go para gerir a aplicação;
- Subir o banco de dados da aplicação através do docker compose, e automatizar assim parte da tarefa, ao invés de ter que lembrar e executar o comando padrão do Docker;
- Corrigir um problema que se encontrava no docker compose, que estava com complicações nos volumes, onde os arquivos são armazenados, permitindo assim que o banco de dados possa ser executado;
- Executar os testes automatizados, de forma manual, o que permite verificar a lógica da aplicação.

### Vantagens do testes automatizados

**Impedir que atualizações criem problemas em funções existentes.**
> OBS! Principalmente em aplicações grandes, com muitas funções diferentes, é possível que uma atualização gere um problema e ela pare de responder corretamente; já se tivermos testes prontos, esses problemas serão detectados e podemos corrigi-los antes do lançamento de uma nova versão.

**Garantir as funcionalidades já implementadas.**
> OBS! É sempre possível que tenhamos pensado em uma lógica para a programação, porém acabamos cometendo erros no momento de sua implementação.Para evitarmos problemas, podemos criar os testes, que contêm apenas as entradas e verificam as saídas, garantindo a lógica da aplicação.

## O que são testes?

Os testes são usados em várias etapas de desenvolvimento e com várias linguagens de programação.

A principal função desses testes é verificar o funcionamento correto de uma aplicação como um todo, um pedaço dessa aplicação ou uma única função. Sendo assim, podemos dividi-los em 3 partes: testes unitários, testes de integração e testes de ponta a ponta.

### Tipos de Testes:

**Testes unitários**

![](https://www.alura.com.br/artigos/assets/tipos-de-testes-principais-por-que-utiliza-los/imagem1.jpg)

Esses testes são feitos em um **nível muito baixo** (próximo ao código fonte) do projeto, por isso, geralmente quem os realiza são os programadores envolvidos no projeto.

Geralmente são realizados de forma isolada do restante do sistema, visto que tem por objetivo assegurar a qualidade das unidades de forma individual e não o sistema como um todo. Podemos entender como **“unidade”** as menores partes do nosso sistema, ou seja, métodos e funções das classes ou pacotes utilizados no projeto.

Esses testes têm como objetivo verificar as menores unidades isoladamente, garantindo que a lógica de cada uma delas está correta e que funciona conforme o esperado. Geralmente têm um baixo custo para automatização e podem ser executados rapidamente, inclusive por um servidor de integração contínua.

### Testes de integração

![](https://www.alura.com.br/artigos/assets/tipos-de-testes-principais-por-que-utiliza-los/imagem2.png)

Como vimos, os testes unitários buscam verificar se elementos individuais (unidades) do sistema estão corretos, mas isso não nos garante que a interação entre essas unidades ocorrerá da forma que planejamos. É nesse momento que utilizamos os **testes de integração.**

Geralmente eles são mais complexos para serem desenvolvidos e mais lentos ao ser executados, pois ao contrário dos testes unitários, nosso objetivo não será testar a lógica nas menores unidades do sistema, mas sim as funcionalidades inteiras, o conjunto funcionando em simultâneo e entregando o resultado esperado.

Por isso, o ideal é realizar testes de integração após a realização dos testes unitários, garantindo que as unidades estão corretas individualmente e também que funcionam em conjunto.

### Testes de ponta a ponta (E2E)

![](https://www.alura.com.br/artigos/assets/tipos-de-testes-principais-por-que-utiliza-los/imagem4.jpg)

Como o próprio nome sugere, esses testes buscam verificar o comportamento do sistema como um todo, “de uma ponta à outra”.


Geralmente simulam a atividade que o usuário final teria, mas feita em um ambiente preparado para ser muito semelhante ao do ambiente de produção. Normalmente ele é o último teste antes de o projeto entrar em produção.

O ambiente no qual os testes são feitos precisa de situações que simulem o uso do produto desenvolvido no mundo real, como interagir com um banco de dados com informações reais, usar comunicações de rede, interagir com outros aplicativos, sistemas ou hardware, se necessário.

Os testes de ponta a ponta também buscam dar uma visão geral do funcionamento do sistema para tomadas de decisão e podem ser utilizados para verificar se ele atende a alguma norma específica, padrões legais ou regulamentações.

Demoram mais para ser escritos e executados, visto que englobam todo o projeto em questão. Além disso, por se tratar de um tipo de teste de **alto nível**, ele não se atêm aos mínimos detalhes da aplicação que está sendo testada… ou seja, geralmente não nos dá muitos detalhes a respeito dos erros encontrados, como os testes unitários por exemplo.

### Teste manual vs. automatizado

O **teste manual**, como o próprio nome nos indica, é feito manualmente por um analista, desenvolvedor ou especialista em qualidade. Nessa situação, a pessoa responsável pelos testes irá executar cada passo necessário para que o teste seja realizado com sucesso, sempre atento para as condições que o teste precisa para ser realizado da forma correta.

O teste manual costuma ter baixo valor de investimento e também permite que a pessoa que os realiza experimente condições semelhantes às do ambiente de produção, já que pode definir os parâmetros do teste manualmente.

Em compensação, testes manuais são mais lentos e como dependem totalmente da interação humana, sempre existe uma alta possibilidade de um problema passar despercebido por quem testa.

Já os testes automatizados nos trazem a praticidade de ter scripts, ferramentas como os mocks, citados neste artigo e técnicas que agilizam o processo. Eles nos ajudam a descobrir rapidamente se o sistema está com o desempenho esperado, e por serem automatizados, podem ser executados sem a necessidade de uma pessoa em todas as etapas de testes.

São mais confiáveis, já que são definidos por uma ferramenta ou scripts específicos; Assim o teste será executado automaticamente, sem interferência humana direta, diminuindo a possibilidade de erros passarem despercebidos.

Costumam ser mais caros, pois dependem de ferramentas específicas e o nível de automação que escolhemos influencia no tipo de ferramenta a ser utilizada, o que pode trazer mais custos. Além disso, existem problemas que apenas um testador humano poderá detectar, como os de usabilidade. Nesses casos não conseguimos utilizar a automatização de forma eficiente.

Por fim, fica a dúvida: Usar testes automatizados ou manuais? Essa é uma daquelas perguntas que têm como resposta um: depende…

O mais comum é que os dois tipos sejam utilizados em simultâneo, pois como vimos, temos vantagens e desvantagens em ambos e existem tipos de testes que preferencialmente serão automatizados, enquanto outros tendem a permanecer manuais, pois se faz necessária uma interação humana real, ou ainda por apresentarem um custo muito elevado.

### O que é Github Actions?

GitHub Actions é um serviço de **integração contínua e entrega contínua (CI/CD)** oferecido pelo GitHub. Ele permite automatizar tarefas, como construir, testar e implantar seu código, sempre que houver uma mudança no repositório do GitHub.

Você pode usar o GitHub Actions para definir fluxos de trabalho personalizados que podem ser executados em várias plataformas, incluindo Windows, macOS e Linux. Além disso, você pode integrar ferramentas de terceiros, como AWS, Azure e Slack, para automatizar ainda mais seus fluxos de trabalho.

### Rotinas sugeridas

Sempre que colocamos um projeto em um repositório no Github é realizada uma análise de forma automática para verificar quais linguagens estão sendo utilizadas, podendo ser Go, Java, HTML, Java Script, Python, entre outras.

Com essa análise, o Actions pode nos sugerir uma linguagem base para as rotinas de CI que vamos criar. Podemos ter múltiplas rotinas, com várias linguagens diferentes, porém não é comum termos 2 ou 3 linguagens de programação em um mesmo projeto.

No nosso caso, foi sugerido o Go por ser a maior parte do repositório, mas você pode testar com outras linguagens e verificar se o Actions já tem uma rotina base para o seu projeto.

E já te aviso que a maioria das linguagens populares têm rotinas prontas para você poder utilizar, sendo necessárias modificações apenas algumas linhas.

### Vantagens do CI

**Garantir a consistência do ambiente e dos testes.**
>OBS! Como a cada vez que executamos usamos um ambiente novo e limpo, se estiver faltando uma dependência ou formos usar um código que não está no repositório o código retornará um erro, mostrando que não está pronto para ser disponibilizado.

**Executar o mais rápido possível.**
>OBS! Como os testes podem ser executados logo que subimos uma atualização no repositório, não é necessário avisar alguém para baixar a aplicação e depois executar os testes, pois a rotina executa diretamente no repositório,e assim reduz o tempo do processo (apesar dos testes serem executados na mesma velocidade).

### Resumo do Módulo

- Executar os testes automatizados para o Go, e por meio disso verificar se existem problemas de lógica na aplicação, para que sejam corrigidos;
- Executar os testes de forma verbosa, para que assim seja possível ver todos os testes que estão sendo executados e como estão sendo executados. Assim podemos ver se algum deles retornou um erro;
- Acessar o Github Actions, para que possamos começar a criar as rotinas de integração contínua;
- Criar a sua primeira rotina de CI, utilizando a rotina sugerida pelo Actions, e assim permitir que apenas poucas linhas sejam alteradas.

### Campos dos jobs

Todos os jobs precisam de campos que vão definir como eles são executados. Os principais campos são:


- `runs-on`: define qual máquina deve ser utilizada. Podemos ter 3 sistemas diferentes: Windows, Ubuntu e MacOS, tendo várias versões disponíveis de cada um deles que podem ser encontradas na [documentação](https://docs.github.com/pt/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_idruns-on).
- `steps`: define quais comandos devem ser executados em sequência, como um script.
- `name`: é utilizado para escolher um nome para cada etapa dentro do `steps` ou nomear um job se usado antes do `runs-on`.
- `run`: é onde vamos declarar o que deve ser executado naquele passo, podemos executar apenas um `run` por passo.

```yml
name: Go

on:
  push:
    branches: [ "master" ]
  pull_request:
    branches: [ "master" ]

jobs:

  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3

    - name: Set up Go
      uses: actions/setup-go@v3
      with:
        go-version: 1.19

    - name: Build
#     Executar um comando dentro da máquina em alguma arquivo ./..
      run: go build -v main.go
      
#     Executar um teste dentro da máquina em alguma arquivo ./..
    - name: Test
      run: go test -v main_test.go
```

### Subindo o docker compose

```yml
# This workflow will build a golang project
# For more information see: https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-go

name: Go

on:
  push:
    branches: [ "master" ]
  pull_request:
    branches: [ "master" ]

jobs:

  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3

    - name: Set up Go
      uses: actions/setup-go@v3
      with:
        go-version: 1.19

    - name: Build
#     Executar um comando dentro da máquina em alguma arquivo ./..
      run: go build -v main.go
      
#     criar qualquer imagem necessária no Docker Compose
    - name: Build-DB
      run: docker-compose build
      
#     subir o docker compose
    - name: Create-DB
      run: docker-compose up -d
      
#     Executar um teste dentro da máquina em alguma arquivo ./..
    - name: Test
      run: go test -v main_test.go
```

### Resumo do módulo

- Quais são os principais campos dos jobs, tendo o `runs-on` para escolher o sistema, `steps` em conjunto com run para executar códigos e `name` para nomear cada passo;
- Como executar códigos dentro da rotina de CI, para que assim possamos preparar o ambiente e rodar os testes da aplicação, garantindo a lógica dela;
- Iniciar um container Docker usando o `docker-compose up` dentro de uma pipeline, e com isso conseguimos facilitar a configuração do ambiente.

### O que é um pipeline?

Em tecnologia da informação, "pipeline" é um termo que se refere a uma sequência de etapas ou processos que são executados em um fluxo de trabalho. Essas etapas são executadas sequencialmente, onde a saída de uma etapa se torna a entrada da próxima etapa.

Por exemplo, em ciência de dados, um pipeline pode ser usado para processar dados brutos, realizar transformações de dados, treinar um modelo de aprendizado de máquina e, finalmente, implantar o modelo em produção. Cada uma dessas etapas pode ser considerada um estágio do pipeline.

Aqui está um exemplo de um pipeline de processamento de dados:

1. Leitura dos dados: Os dados brutos são lidos de um arquivo ou fonte de dados.

2. Limpeza dos dados: Os dados são limpos e transformados para remover valores ausentes, corrigir erros e formatar os dados.

3. Pré-processamento: Os dados são normalizados, padronizados, reduzidos dimensionalmente e outras técnicas de pré-processamento podem ser aplicadas.

4. Treinamento do modelo: Os dados processados são usados para treinar um modelo de aprendizado de máquina.

5. Avaliação do modelo: O modelo é avaliado em um conjunto de dados de validação ou teste para determinar sua precisão.

6. Implantação: O modelo é implantado em produção para fazer previsões em novos dados.

Este é apenas um exemplo de pipeline. As etapas e processos podem variar dependendo do objetivo do pipeline e da aplicação específica.


### Separando Rotinas
Para fazer essa separação de rotinas vamos criar outro job, o job de compilação. Então, vamos precisar criar e preencher os campos necessários.

A primeira coisa a fazer é alterar o nome da rotina de testes: vamos alterar de `build`para `test` e criar a rotina de `build`:

```yml
# This workflow will build a golang project
# For more information see: https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-go

name: Go

on:
  push:
    branches: [ "master" ]
  pull_request:
    branches: [ "master" ]

jobs:

# Rotina de teste
  test:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3

    - name: Set up Go
      uses: actions/setup-go@v3
      with:
        go-version: 1.19

    - name: Build
#     Executar um comando dentro da máquina em alguma arquivo ./..
      run: go build -v main.go
      
#     criar qualquer imagem necessária no Docker Compose
    - name: Build-DB
      run: docker-compose build
      
#     subir o docker compose
    - name: Create-DB
      run: docker-compose up -d
      
#     Executar um teste dentro da máquina em alguma arquivo ./..
    # - name: Test
    #   run: go test -v main_test.go
  
  # Rotina de build
  build:
  # precisa
    needs: test
    runs-on: ubuntu-latest
    steps: 
    - uses: actions/checkout@v3
    - name: Build
      run: go build -v main.go
```

Definir a ordem de execução com o `needs`:, e onde vamos colocar o nome do `job` a ser executado antes; então no nosso caso é `needs: test`, e para ficar bem óbvio a ordem de execução, devemos colocar ele na primeira linha do job.

```yml
  build:
    needs: test
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Build
      run: go build -v main.go
```

### Ordem de execução 

No github actions, a ordem de execução dos jobs não é definida pela ordem que eles aparecem no arquivo. A ordem de execução depende do campo ``needs``, então se não usarmos o `needs` no job de `build` ele será executado ao mesmo tempo do job de testes.

Executar múltiplas rotinas simultaneamente pode ser algo vantajoso, reduzindo o tempo que temos que esperar para verificar se o projeto está funcionando corretamente, mas nem sempre é o comportamento que esperamos.

Porém, lembre-se que a execução simultânea ocorre em máquinas separadas, então as instâncias não se conversam e o tempo cobrado pela execução é o tempo somado de ambas as máquinas. Então se uma máquina precisou de 1 minuto e 15 segundos e outra máquina precisou de 1 minuto de 30 segundo, o tempo total de execução é de 2 minutos e 45 segundos, que serão descontados dos 2000 que são disponibilizados todos os meses.

### Resumo

- Alterar a ordem de execução de comandos dentro de cada job, tornando-os mais rápidos, como no caso dos testes e a compilação, nos quais não é necessário gastar tempo com a compilação se os testes falharem;
- Criar um segundo job, o que permite o separar melhor cada função dentro da rotina, facilitando a identificação de problemas e a manutenção a longo prazo;
- Visualizar as rotinas no Github Actions, e verificar se ocorreu algum erro e acessar os logs de execução;
- Forçar um erro, podendo assim entender o que ocorre se for encontrado isso na aplicação e como esse erro é mostrado para que acessa o repositório.

### Estratégia de matriz

Uma estratégia de matriz (matrix strategy) é uma funcionalidade do GitHub Actions que permite executar um fluxo de trabalho (workflow) em várias configurações diferentes. É útil quando você precisa testar ou implantar seu código em diferentes ambientes ou configurações de plataforma.

Com uma matriz de estratégia, você pode definir um conjunto de variáveis ​​de ambiente que serão passadas para o fluxo de trabalho em cada execução. O GitHub Actions então cria um conjunto de trabalhos (jobs) para cada combinação única dessas variáveis ​​de ambiente.

Por exemplo, se você quiser testar seu código em diferentes versões de um sistema operacional ou em diferentes versões de um banco de dados, pode usar uma matriz de estratégia para gerar uma série de trabalhos, cada um com a configuração específica que você precisa testar.

Aqui está um exemplo de como definir uma matriz de estratégia em um arquivo de fluxo de trabalho:

```yml
jobs:
  build:
    strategy:
      matrix:
        os: [ubuntu-latest, windows-latest]
        node-version: [12.x, 14.x, 16.x]
    runs-on: ${{ matrix.os }}
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Setup Node.js
        uses: actions/setup-node@v2
        with:
          node-version: ${{ matrix.node-version }}
      - name: Install dependencies
        run: npm install
      - name: Run tests
        run: npm test

```

Nesse exemplo, a matriz de estratégia é definida com duas variáveis: `os` e `node-version`. Serão gerados um total de seis trabalhos, um para cada combinação única de `os` e `node-version`. Os trabalhos são executados em diferentes sistemas operacionais e versões do Node.js e executam os passos necessários para construir, testar e implantar seu código.

**Outro exemple: em go**

```yml
# This workflow will build a golang project
# For more information see: https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-go

name: Go

on:
  push:
    branches: [ "master" ]
  pull_request:
    branches: [ "master" ]

jobs:

  test:
    runs-on: ubuntu-latest
    
    strategy:
      matrix:
        go_version: ['1.19', '1.18', '>=1.19']
        
    steps:
    - uses: actions/checkout@v3

    - name: Set up Go
      uses: actions/setup-go@v3
      with:
        go-version: ${{ matrix.go_version }}

#     - name: Build
# #     Executar um comando dentro da máquina em alguma arquivo ./..
#       run: go build -v main.go
      
#     criar qualquer imagem necessária no Docker Compose
    - name: Build-DB
      run: docker-compose build
      
#     subir o docker compose
    - name: Create-DB
      run: docker-compose up -d
      
#     Executar um teste dentro da máquina em alguma arquivo ./..
    - name: Test
      run: go test -v main_test.go
  
  build:
  # precisa
    needs: test
    runs-on: ubuntu-latest
    steps: 
    - uses: actions/checkout@v3
    - name: Build
      run: go build -v main.go
      
```

**Passa a passo**

Para implementarmos a estratégia de matrizes vamos precisar declarar que queremos usar uma estratégia e qual que vamos utilizar.

```yml
    strategy:
      matrix:
```

Em seguida, precisamos declarar qual será a variável que vamos utilizar, então, para o código em go. Podemos declarar ela com o nome `go_version` seguida de seus valores em forma de vetor, ou matriz `['1.18', '1.17', '>=1.18']`, ficando com:

```yml
    strategy:
      matrix:
        go_version: ['1.17', '1.18', '>=1.18']
```

Agora que temos a variável com as versões do Go que vamos usar, podemos colocar o seu valor no momento que preparamos o ambiente. No Actions, podemos acessar o valor da variável que criamos usando `${{ tipo.varival }}`, então temos o nosso código como:

```yml
    strategy:
      matrix:
        go_version: ['1.17', '1.18', '>=1.18']
    steps:
    - uses: actions/checkout@v3

    - name: Set up Go
      uses: actions/setup-go@v3
      with:
        go-version: ${{ matrix.go_version }}
```
### Uso dos Segredos

Quando usamos senhas e chaves que não podem ser expostas, não devemos colocá-las no código, devemos sempre usar os segredos, e podemos acessar seus valores de uma forma muito parecida com as variáveis.

Para usar um valor temos que usar `${{ secrets.variavel }}` substituindo o `variavel` pelo nome do segredo de ambiente que foi criado.

Uma vez que o segredo é cadastrado no Actions, não é mais possível recuperá-lo sem expor para todo o público, porém é possível atualizar o seu valor.

Nunca faça um `echo` das chaves e senhas, e não coloque-as diretamente no código. Quando alguém faz um clone ou um fork do repositório as variáveis dos segredos não são copiadas, diferente dos arquivos com os códigos.

### Resumo

- Trabalhar com estratégias de matrizes, o que possibilita a criação de vários ambientes de desenvolvimento diferentes com pouco código, deixando a rotina mais organizada;
- Criar e utilizar variáveis, como a go_version dentro da estratégia de matriz,o que possibilita guardar múltiplos valores para usarmos posteriormente;
- Utilizar o secrets, e criar assim um ambiente, colocando um segredo dentro dele, possibilitando o seu uso dentro da rotina, porém sem compartilhar seu valor.