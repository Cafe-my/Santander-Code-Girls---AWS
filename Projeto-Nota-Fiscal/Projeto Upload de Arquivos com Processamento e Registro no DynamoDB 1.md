# O Que Será Feito
1. O Usuário faz o upload de um arquivo (JSON ou CSV) contendo informações de uma nota fiscal (número, cliente, valor, data, etc) em um bucket S3
2. Configuração do Trigger nesse evento para disparar uma Lambda Function (em Python) 
3. A Lambda processa o conteúdo do arquivo e grava os dados importantes em uma tabela no DynamoDB
4. Outro usuário (Postman) pode consultar os dados através de uma API Gateway que acionará outra função Lambda que fará a consulta da tabela
# AWS Local com **LocalStack**
LocalStack é um **emulador de serviços AWS que permite desenvolver e testar aplicativos na sua máquina local, usando contêineres Docker, sem precisar se conectar a uma conta AWS real.**

Ele oferece uma versão open-source, gratuita e com suporte a vários serviços da AWS. Mas também possui versões pagas (Pro e Enterprise) que oferecem recursos avançados.
## Benefícios
- **Desenvolvimento Local e Offline:** 
    Permite que você desenvolva e teste funcionalidades da AWS sem depender de uma conexão com a internet ou uma conta AWS.
- **Redução de Custos:** 
    Evita custos associados ao uso de serviços reais da AWS durante a fase de desenvolvimento e teste.
- **Ambiente Controlado:** 
    Proporciona um ambiente previsível para simular diferentes cenários e configurações sem impactar ambientes de produção.
## Instalação e Primeiros Passos
1. Criação de uma conta LocalStack
2. Instalação (https://docs.localstack.cloud/aws/getting-started/installation/)
3. Para conferir se a instalação ocorreu corretamente: `localstack --version`
4. Para iniciar: `localstack start # start localstack in background with -d flag`
	Saída: 
```
__                     _______ __             __
    / /   ____  _________ _/ / ___// /_____ ______/ /__
   / /   / __ \/ ___/ __ `/ /\__ \/ __/ __ `/ ___/ //_/
  / /___/ /_/ / /__/ /_/ / /___/ / /_/ /_/ / /__/ ,<
 /_____/\____/\___/\__,_/_//____/\__/\__,_/\___/_/|_|

 💻 LocalStack CLI ${LOCALSTACK_VERSION}
 👤 Profile: default

[12:47:13] starting LocalStack in Docker mode 🐳                       localstack.py:494
           preparing environment                                       bootstrap.py:1240
           configuring container                                       bootstrap.py:1248
           starting container                                          bootstrap.py:1258
[12:47:15] detaching                                                   bootstrap.py:**1262**
```

Antes de iniciar o LocalStack é necessário instalar o Docker, porque o LocalStack **precisa do Docker** para criar os serviços da AWS simulados (S3, Lambda, DynamoDB etc.).  
Sem Docker, ele não consegue subir os containers internos.
	https://www.docker.com/products/docker-desktop/

5. Configurar o AWS CLI local:
	`aws configure`
	as credenciais **não precisam ser válidas** mas precisam ser definidas
6. Criar e configurar os serviços necessários através do AWS CLI local:
	- Criar o bucket S3
	- Criar a tabela no DynamoDB
	- Criar uma Lambda Function
	- Criar o trigger do S3
	- Criar o API Gateway e associar a uma Lambda Function
