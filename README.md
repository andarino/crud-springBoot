## RESTAPI-springboot
######  Projeto para portifólio usando JPA, MySQL and Maven 
![spring](https://img.shields.io/badge/Spring-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![mysql](https://img.shields.io/badge/MySQL-00000F?style=for-the-badge&logo=mysql&logoColor=white)
![bootstrap](https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white)
## Dependências
* Java:
```
$ java --version
openjdk 15.0.2 2021-01-19
OpenJDK Runtime Environment (build 15.0.2+7)
OpenJDK 64-Bit Server VM (build 15.0.2+7, mixed mode)
```
* Maven:
```
$ mvn --version
Apache Maven 3.8.2 (NON_CANONICAL)
Maven home: /opt/maven
Java version: 15.0.2, vendor: N/A, runtime: /usr/lib/jvm/java-15-openjdk
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "5.10.42-1-manjaro", arch: "amd64", family: "unix"
```
## Inicializando o server
1 - Baixe o projeto na máquina com `git clone https://github.com/andarino/crud-springBoot.git` Após o `clone`. Entre na pasta do projeto.
```sh
cd crud-springBoot/
```
Rode o arquivo compilado `projeto-0.0.1-SNAPSHOT.jar` no terminal:
```sh
java -jar projeto-0.0.1-SNAPSHOT.jar.jar
```
>O server estará acessível em `http://localhost:8080`

## Métodos
O prefixo de todos é  `http://localhost:8080/`.
Para fazer as requisições você pode usar o insomnia ou o postman.
Para a tabela `conta` haverá os endpoints...
Método | Recurso | Descricão
-------|---------|----------
GET| /contas/| Lista todos as contas 
GET| /contas/{num_conta}| Lista a conta de acordo com a PK passada 
POST| /conta | Adiciona uma nova conta (envia um json com as informações)
PUT| /conta | Altera dados de uma conta existente
DELETE| /contas/{num_conta} |Exclue a conta com a pk informada

Para a tabela `lancamento` haverá os endpoints...
Método | Recurso | Descricão
-------|---------|----------
GET| /lancamento/| Lista todos os lancamentos e a conta associada ao lancamento 
GET| /lancamento/{numLanc}| Lista o lancamento de acordo com a PK passada 
POST| /lancamento | Adiciona um novo lancamento (envia um json com as informações, o campo "conta" também é um json com os parâmetros do insert de "conta")
PUT| /lancamento | Altera dados de um lancamento existente
DELETE| /lancamento/{numLanc} |Exclue a conta com a PK informada



## Requisição
A requisição suportada é um `json`.
>Content-Type: application/json

## Dados para insert nos endpoints
Os exemplos de como os dados devem ser inseridos estão logo abaixo:

Conta: 
```json
{
  "saldo": "8953453456",
  "cpf": "100.000.00-000",
	"lancamentos": [
		{
		"num_lancamento" : 78,
		"desc_lancamento": "transacao",
		"natureza_lancamento": "F",
		"valor_lancamento": "546",
		"num_conta": "100"
		}
	]
}
```
Obs: O campo `"lancamentos"` pode ser null.

Lancamento: 
```json
{
  "num_lancamento": 56,
  "data_lancamento": null,
  "valor_lancamento": "345435",
  "natureza_lancamento": "C",
  "desc_lancamento": "transacao",
  "conta": {
    "num_conta": 96,
    "saldo": "654",
    "cpf": "10.100.100-90"
  }
}

```
Obs: O campo `"num_conta"`deve coincidir com alguma conta existente no banco.
