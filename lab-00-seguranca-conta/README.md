Lab 00 – Segurança inicial da conta AWS


Objetivo

Preparar uma conta AWS nova seguindo boas práticas de segurança e controle de custos antes de criar qualquer recurso.

Serviços utilizados
AWS IAM – usuários, grupos e políticas
MFA – autenticação multifator
AWS Budgets – alertas de custo
O que foi feito
Criação da conta no Free Plan
MFA ativado no usuário root
Acesso ao faturamento liberado para usuários IAM
Grupo Administradores criado com a política AdministratorAccess
Usuário IAM debora-admin criado dentro do grupo, com MFA
Alias da conta criado para facilitar o login; o root deixou de ser usado no dia a dia
Dois alertas de custo no AWS Budgets:
Zero spend budget – avisa no primeiro centavo cobrado
Orçamento mensal de US$5 – alerta ao atingir 80%
Arquitetura
Usuário root (MFA, guardado para emergências)
        │
        └── IAM
             └── Grupo: Administradores (AdministratorAccess)
                    └── Usuário: debora-admin (MFA) ← uso diário

AWS Budgets ──► alertas por e-mail (US$0 e US$5/mês)
Evidências
Etapa	Print
MFA no root	MFA root
Grupo Administradores	Grupo
Usuário com MFA	Usuário
Alertas de orçamento	Budgets

Prints com ID da conta e e-mails ocultados.

Conceitos aplicados
Menor privilégio e uso de grupos: permissões atribuídas ao grupo, não direto ao usuário
Proteção do root: usado apenas para tarefas que exigem root
Modelo de responsabilidade compartilhada: a segurança do acesso à conta é responsabilidade do cliente
Controle de custos: alertas configurados antes de criar recursos
Dificuldades e aprendizados
<!-- Escreva aqui com suas palavras: o que deu errado, o que você não sabia e como resolveu. Recrutadores leem esta parte. -->
Próximo lab

Lab 01 – Site estático no S3 + CloudFront
