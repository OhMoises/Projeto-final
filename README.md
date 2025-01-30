# Projeto Final PB
## Equipe: Henrique Palermo Emerick & Moisés Pereira Araujo
### Fase 1: Migração "Lift-and-Shift
### Banco de Dados MySQL:
- Serviço: Utilize o Amazon RDS para MySQL como solução gerenciada.
- Configuração: Crie uma instância RDS em Multi-AZ para alta disponibilidade e backup automático.
- Tamanho: Escolha um tipo de instância que suporte sua carga atual (ex: db.m5.large).

### Servidor da Aplicação (Frontend e Backend):
- Serviço: Crie instâncias EC2 para hospedar o frontend (React) e o backend (APIs com Nginx).
- Configuração: Para o frontend, uma instância t3.micro pode ser suficiente inicialmente. Para o backend, considere uma instância t3.small ou t3.medium.
- Armazenamento: Utilize EBS para armazenamento persistente.

### Configurar Segurança
  - Grupos de Segurança: Configure grupos de segurança para permitir acesso às portas necessárias (80 para HTTP, 443 para HTTPS, e 3306 para MySQL).
  - IAM Roles: Crie roles do IAM para permitir que suas instâncias EC2 acessem outros serviços da AWS, como S3 e RDS.

#

### Quais atividades são necessárias para a migração?
- Avaliação da infraestrutura atual.
- Planejamento da migração, incluindo a definição de um cronograma.
- Configuração das instâncias EC2 e RDS na AWS.
- ransferência de dados dos servidores atuais para o Amazon RDS e EC2.
  
### Quais as ferramentas vão ser utilizadas?
- AWS Application Migration Service para mover aplicações.
- AWS Database Migration Service (DMS) para migrar bancos de dados.
- AWS CLI e AWS Management Console para gerenciar recursos.

### Qual o diagrama da infraestrutura na AWS?
-Diagrama de arquitetura

![imagem (8)](https://github.com/user-attachments/assets/b0ff1138-3084-4172-9bc4-f8c1e2f6a4f1)

- Diagrama de migração
![Projeto Final Kubernets - Diagrama 1 - Migração drawio - Google Drive - Google Chrome 27_01_2025 09_50_59](https://github.com/user-attachments/assets/d8295b85-a256-4214-8416-9264764becb3)



### Como serão garantidos os requisitos de Segurança?
- Uso de grupos de segurança para controlar o tráfego de entrada e saída.
- Implementação de IAM roles para acesso seguro aos serviços AWS.
- Criptografia de dados em trânsito e em repouso usando AWS Key Management Service (KMS).

### Como será realizado o processo de Backup?
- Configuração de backups automáticos no Amazon RDS.
- Utilização de snapshots EBS para instâncias EC2.
- Armazenamento de backups em Amazon S3.

### Qual o custo da infraestrutura na AWS (AWS Calculator)?
- Estimativa de custos utilizando a AWS Pricing Calculator.
- Custo da EC2 é igual a U$ 68.98
- Custo da migração dos serviços é igual a U$ 240.39
- Custo do banco de dados RDS é igual a U$ 151.47

![imagem (5)](https://github.com/user-attachments/assets/f1791167-9ba5-4776-9e25-d05ccadff8ce)

#

# Fase 2: Modernização com Kubernetes
### Quais atividades são necessárias para a migração?
- Containerização das aplicações usando Docker.
- Criação do cluster EKS (Elastic Kubernetes Service).
- Implantação das aplicações no EKS.
### Quais as ferramentas vão ser utilizadas?
- Amazon EKS para gerenciamento do Kubernetes.
- Amazon Elastic Container Registry (ECR) para armazenar imagens Docker.
- AWS CloudFormation ou Terraform para provisionamento da infraestrutura.
### Qual o diagrama da infraestrutura na AWS?
-
![Projeto Final Kubernets - Diagrama 2 drawio](https://github.com/user-attachments/assets/ee18d826-6308-4fc6-a1d8-1ccb212530b9)


### Como serão garantidos os requisitos de Segurança?
- Implementação de Network Policies no Kubernetes para controlar o tráfego entre pods.
- Uso de IAM roles for service accounts (IRSA) no EKS para controle granular de acesso.
- Monitoramento contínuo com AWS CloudTrail e Amazon GuardDuty.
### Como será realizado o processo de Backup?
- Backups automáticos do Amazon RDS configurados com retenção apropriada.
- Uso do Velero ou similar para backups dos volumes persistentes no Kubernetes.
### Qual o custo da infraestrutura na AWS (AWS Calculator)?
- Estimativa dos custos utilizando a AWS Pricing Calculator.
  - Custo dos serviços EKS, RDS, S3, ECR, e outros componentes envolvidos na nova arquitetura.
 ![CALCULADORA 2](https://github.com/user-attachments/assets/5425c1bd-2859-4ca9-9df6-8b7f91232cb7)

![CALCULADORA pt 2](https://github.com/user-attachments/assets/644a37d5-9c04-48b8-b574-824544d7597d)
  
### Configurar o Amazon EKS
- Criar um Cluster EKS:
  - Utilize o Amazon Elastic Kubernetes Service (EKS) para criar um cluster Kubernetes gerenciado.
  - O EKS gerencia automaticamente a infraestrutura do Kubernetes em várias zonas de disponibilidade.
- Configuração do Cluster:
  -  Use o AWS Management Console ou a AWS CLI para criar o cluster EKS.
  -  Configure o kubectl para interagir com seu cluster EKS.
### Implantar Aplicações no EKS
- Containerização das Aplicações:
  - Crie imagens Docker para suas aplicações frontend e backend.
  - Armazene as imagens no Amazon Elastic Container Registry (ECR).
- Implantar no EKS:
  - Use arquivos YAML para definir os deployments e services no Kubernetes.
  - Configure um Load Balancer (ALB) para gerenciar o tráfego entre as instâncias.
### Banco de Dados Gerenciado
- RDS como Serviço PaaS:
  - Continue utilizando o Amazon RDS como seu banco de dados gerenciado.
### Persistência de Objetos
- Amazon S3:
  - Utilize o Amazon S3 para armazenar objetos como imagens e vídeos.
### Segurança
- IAM Roles for Service Accounts (IRSA):
  - Use IRSA para conceder permissões específicas aos pods do Kubernetes.
- Network Policies:
  - Implemente políticas de rede no Kubernetes para controlar o tráfego entre pods.
#
