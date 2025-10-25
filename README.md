# Gerenciamento de Instâncias EC2 na AWS

Este repositório faz parte do desafio de laboratório da DIO para consolidação dos conhecimentos práticos em Amazon EC2. O objetivo é registrar e compartilhar o passo a passo, comandos, aprendizados e insights sobre o gerenciamento de instâncias EC2, com documentação clara e estruturada.

## Índice

- [Objetivo](#objetivo)
- [Pré-requisitos](#pré-requisitos)
- [Resumo dos Conceitos de EC2](#resumo-dos-conceitos-de-ec2)
- [Passo a Passo da Prática](#passo-a-passo-da-prática)
- [Comandos Úteis](#comandos-úteis)
- [Insights Pessoais](#insights-pessoais)
- [Referências](#referências)

---

## Objetivo

Consolidar a aprendizagem prática sobre criação, configuração, acesso, gerenciamento e monitoramento de instâncias EC2 na AWS, além de registrar o processo de criação do ambiente e boas práticas.

---

## Pré-requisitos

- Conta válida na AWS (é recomendável usar a camada gratuita para evitar cobranças)
- Conhecimentos básicos de cloud computing, SSH e uso de terminal
- Git e GitHub para versionamento e publicação

---

## Resumo dos Conceitos de EC2

- **EC2 (Elastic Compute Cloud):** Serviço de computação sob demanda para executar máquinas virtuais (instâncias).
- **AMI (Amazon Machine Image):** Imagem que serve como base para instanciar uma máquina.
- **Tipos de Instância:** Determinam capacidade de CPU, memória, armazenamento e rede.
- **Key Pair:** Par de chaves para autenticação SSH.
- **Security Group:** Firewall virtual que permite ou nega tráfego de/para instâncias.
- **Elastic IP:** Endereço IP fixo para instância EC2.
- **EBS (Elastic Block Store):** Volume de armazenamento persistente.

---

## Passo a Passo da Prática

### 1. Criação de uma Instância EC2
- Acesse o [console AWS](https://console.aws.amazon.com/).
- Navegue até EC2 > Instâncias > Lançar Instância.
- Escolha a AMI (exemplo: Amazon Linux 2).
- Escolha tipo de instância (exemplo: t2.micro - elegível para free tier).
- Crie e faça download da Key Pair (`.pem`).
- Configure Security Group (libere portas mínimas necessárias, geralmente 22 para SSH).
- Lance a instância.

### 2. Acesso à Instância via SSH
- No terminal, defina permissão para a chave:
    ```
    chmod 400 nome-da-chave.pem
    ```
- Conecte-se:
    ```
    ssh -i nome-da-chave.pem ec2-user@<IP-público-da-instância>
    ```

### 3. Gerenciamento Básico (Parar/Iniciar/Terminar/Monitorar)
- Use o console ou o AWS CLI para gerenciar ciclo de vida da instância.
- Exemplo de comandos CLI:
    ```bash
    aws ec2 describe-instances
    aws ec2 stop-instances --instance-ids <instance-id>
    aws ec2 start-instances --instance-ids <instance-id>
    aws ec2 terminate-instances --instance-ids <instance-id>
    ```

### 4. Monitoramento
- No painel EC2, acesse **Monitoramento** para visualizar métricas básicas (CPU, disco, rede).
- Configure alarmes simples pelo CloudWatch.

### 5. (Opcional) Capturas de Tela
- Imagens relevantes estão disponíveis na pasta [images/](images/) _(adicione as imagens no repositório e atualize este link)_.

---

## Comandos Úteis

```bash
# Listar instâncias EC2
aws ec2 describe-instances

# Parar uma instância EC2
aws ec2 stop-instances --instance-ids <instance-id>

# Iniciar uma instância EC2
aws ec2 start-instances --instance-ids <instance-id>

# Encerrar uma instância EC2
aws ec2 terminate-instances --instance-ids <instance-id>
```

---

## Insights Pessoais

Durante o laboratório, reforcei a importância de:
- Não expor portas desnecessárias no Security Group
- Fazer download e backup seguro da Key Pair (não é possível baixar novamente da AWS)
- Parar ou terminar instâncias inativas para evitar custos
- Utilizar tags para identificar recursos e facilitar gerenciamento

Pretendo automatizar o provisionamento de instâncias básicas com scripts futuros — o uso do AWS CLI agiliza operações repetitivas.

---

## Referências

- [AWS Documentação EC2](https://docs.aws.amazon.com/pt_br/ec2/)
- [Guia GitHub Markdown](https://guides.github.com/features/mastering-markdown/)
- [Documentação GitHub](https://docs.github.com/pt)
- [DIO - Plataforma de Formação](https://www.dio.me/)

---  
