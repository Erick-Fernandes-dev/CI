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