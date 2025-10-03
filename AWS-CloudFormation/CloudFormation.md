# AWS CloudFormation
É um serviço que **permite definir e gerenciar recursos de infraestrutura da AWS de forma automatizada usando templates no formato YAML ou JSON**.
Podemos utilizar os templates quantas vezes quisermos e pagamos apenas pelas stacks/recursos criados (ex: EC2, RDS, S3 etc).

Então ao invés de criar manualmente cada recurso no console da AWS, você descreve tudo em um arquivo YAML ou JSON, e o CloudFormation cria os recursos para você.
## Benefícios
- **Automação e repetibilidade:** 
    Permite a criação de ambientes de infraestrutura complexos de forma repetida. 
    
- **Infraestrutura como Código:** 
    Trata a infraestrutura como código, facilitando o versionamento e o gerenciamento de alterações. 
    
- **Gerenciamento unificado:** 
    Todos os recursos da sua aplicação são agrupados e gerenciados como uma única unidade, simplificando a orquestração. 
    
- **Segurança:** 
    Ajuda a garantir a segurança e o cumprimento de políticas de conformidade ao automatizar o provisionamento de recursos.
## Como funciona:
1. **Crie um modelo:** 
    Você escreve um arquivo de modelo em YAML ou JSON que descreve todos os recursos da AWS necessários para sua aplicação (como instâncias EC2, buckets de S3, sub-redes, etc.). 
    
2. **Crie uma pilha (stack):** 
    O modelo é carregado para o CloudFormation, que cria um conjunto de recursos da AWS, chamados de "pilha". 
    
3. **Gerencie a pilha:** 
    Você pode gerenciar a pilha através de um console, linha de comando ou API.
    
## Exemplo
Template simples com YAML para criar um bucket S3.
```YAML
AWSTemplateFormatVersion: "2010-09-09"
Description: Exemplo simples - cria um bucket S3

Resources:
  MeuBucketS3:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: meu-bucket-exemplo-cloudformation
```