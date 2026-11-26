Lab 00 – Segurança inicial da conta AWS


Objetivo

Preparar uma conta AWS nova seguindo boas práticas de segurança e controle de custos antes de criar qualquer recurso.

Serviços utilizados
AWS IAM – usuários, grupos e políticas
MFA – autenticação multifator
AWS Budgets – alertas de custo
O que foi feito
Criação da conta no Free Plan
MFA (TOTP) ativado no AWS Builder ID usado para acessar o console
Usuário IAM debora-admin criado com a política AdministratorAccess, reservado para acesso programático (AWS CLI) nos próximos labs
O Free Plan não permite criar grupos no IAM, então a política foi anexada direto ao usuário. Em ambiente corporativo, o recomendado é atribuir permissões a grupos.
Nas contas novas, usuários IAM não têm login no console nem opção de MFA: o acesso ao console é feito pelo AWS Builder ID.
Dois alertas de custo no AWS Budgets:
Zero spend budget – avisa no primeiro centavo cobrado
Orçamento mensal de US$5 – alerta ao atingir 80%
Arquitetura
AWS Builder ID (MFA) ← login no console


        │
        └── IAM
             └── Usuário: debora-admin (AdministratorAccess) ← acesso via CLI nos próximos labs

AWS Budgets ──► alertas por e-mail (US$0 e US$5/mês)
Evidências
Etapa	Print
MFA no acesso principal	MFA
Permissões do usuário	Permissões
Alertas de orçamento	Budgets

Prints com ID da conta e e-mails ocultados.

Conceitos aplicados
Gestão de identidades: login humano no console protegido com MFA; usuário IAM separado para automação
Grupos x permissão direta: a boa prática é usar grupos; aqui foi aplicada permissão direta por limitação do Free Plan
Modelo de responsabilidade compartilhada: a segurança do acesso à conta é responsabilidade do cliente
Controle de custos: alertas configurados antes de criar recursos
Dificuldades e aprendizados
Em contas criadas a partir de out/2026, o MFA do acesso principal fica em Profile → Gerenciar perfil → Segurança (AWS Builder ID), e não mais em Security credentials.
O Free Plan não permite criar grupos no IAM; a política foi anexada direto ao usuário.
Usuários IAM não têm a seção Console sign-in nem MFA nas contas novas; o login no console é centralizado no AWS Builder ID.

Próximo lab

Lab 01 – Site estático no S3 + CloudFront
