# Projeto Final PB
## Equipe: Henrique Palermo Emerick & Moisés Pereira Araujo
### Fase 1: Migração "Lift-and-Shift
### Banco de Dados MySQL:
- Serviço: Utilize o Amazon RDS para MySQL como solução gerenciada.
- Configuração: Crie uma instância RDS em Multi-AZ para alta disponibilidade e backup automático.
- Tamanho: Escolha um tipo de instância que suporte sua carga atual (ex: db.t3.medium ou db.m5.large).

### Servidor da Aplicação (Frontend e Backend):
- Serviço: Crie instâncias EC2 para hospedar o frontend (React) e o backend (APIs com Nginx).
- Configuração: Para o frontend, uma instância t2.micro ou t3.micro pode ser suficiente inicialmente. Para o backend, considere uma instância t3.small ou t3.medium.
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

![imagem (3)](https://github.com/user-attachments/assets/de4dc7a8-764f-49fe-848d-dafe0fe1ece6)

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
- 
#
#
