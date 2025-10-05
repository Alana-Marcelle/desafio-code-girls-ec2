# Desafio Code Girls – Gerenciamento de Instâncias EC2

## Objetivo
Este desafio teve como objetivo aplicar na prática os conceitos de **instâncias EC2** e **Amazon EBS** na AWS. O projeto consolida o conhecimento em criação, configuração, gerenciamento de volumes, segurança e otimização de recursos, servindo como material de estudo e referência futura.

## Descrição do Desafio
Durante o laboratório do Code Girls, explorei a criação e o gerenciamento de instâncias EC2, registrando o processo e os principais aprendizados. O foco foi entender a composição de uma máquina virtual na AWS e aplicar boas práticas de **segurança** e **economia de custos**.

## Conceitos Aplicados

### Instâncias EC2 (Elastic Compute Cloud)
* **Modelo:** IaaS (Infraestrutura como Serviço). A AWS fornece a infraestrutura, e o usuário gerencia o sistema operacional, dados e conexões.
* **Composição:** Cada instância é uma máquina virtual composta por CPU, memória, disco e sistema operacional (Windows ou Linux).
* **Escolha Correta:** Selecionar a **AMI** e o **tipo de instância** corretos é crucial para garantir eficiência, escalabilidade e economia.

### Amazon EBS (Elastic Block Store)
* **Função:** Storage confiável e persistente que pode ser anexado a qualquer instância EC2, funcionando como um "HD externo" na nuvem.
* **Flexibilidade:** Permite criar **volumes adicionais** e realizar expansão de forma rápida, ideal para dados de aplicativos e logs.
* **Exemplos de Uso:** Armazenamento para bancos de dados (MySQL, PostgreSQL) e sistemas de arquivos.

### Otimização de Recursos e Custos
* **Objetivo:** Economia de custo e desempenho eficiente dos recursos provisionados.
* **Boas Práticas:**
  * **Desligar instâncias** em ambientes de teste ou desenvolvimento fora do horário de uso.
  * Escolher o **tipo de instância adequado** para a carga de trabalho.
* **Tipos de Instâncias:**
  * **On-Demand:** Pagamento por hora, ideal para cargas irregulares e testes.
  * **Reservadas:** Mais baratas que On-Demand, pagamento anual obrigatório.
  * **Spot:** Até 90% de desconto, mas podem ser encerradas a qualquer momento.

### Segurança em EC2
* **Security Group (Grupo de Segurança):** Firewall virtual da instância, aplicando o princípio do *least privilege*. Ex.: liberar apenas **porta 22 (SSH)** ou **80/443 (Web)**, limitando acesso a IPs específicos.
* **Key Pair (Par de Chaves):** Essencial para acesso seguro via SSH. A chave privada (`.pem`) é baixada localmente e usada para autenticação, garantindo que apenas usuários autorizados acessem a instância.

---

## Etapas Realizadas
1. **Estudo:** Revisão completa das vídeo-aulas do módulo EC2 para compreensão dos conceitos.
2. **Planejamento:** Escolha da AMI e do tipo de instância ideal para o ambiente de teste.
3. **Segurança:** Criação do **Key Pair** e configuração do **Security Group** com regras restritivas.
4. **Provisionamento:** Inicialização da instância EC2 na região correta da AWS.
5. **Gerenciamento:** Criação e anexação conceitual de volumes EBS adicionais, simulando a organização de partições.
6. **Documentação:** Registro de todas as etapas e insights neste `README.md`.

---

## Comandos e Instruções Práticas (Exemplos Conceituais)

```bash
# 1. Conectar à instância via SSH
ssh -i "minha-chave.pem" ec2-user@<IP-da-instancia>

# 2. Listar volumes anexados
lsblk

# 3. Criar ponto de montagem e montar o volume
sudo mkdir /dados
sudo mount /dev/xvdf /dados

# 4. Criar arquivo de teste
echo "Teste de armazenamento EBS" > /dados/teste.txt
## Conclusão e Insights
Este desafio solidificou a importância de um planejamento cuidadoso antes de provisionar recursos na nuvem.  

**Principais insights adquiridos:**
1. **Otimização de Custos:** A escolha entre instâncias On-Demand, Reservadas e Spot deve ser guiada pela criticidade da carga de trabalho, evitando desperdício de recursos.
2. **Segurança em Camadas:** A combinação do **Key Pair** para acesso restrito e a configuração detalhada do **Security Group** minimizam a superfície de ataque, seguindo boas práticas de infraestrutura.

Este repositório serve como material de referência para futuras implementações de infraestrutura IaaS na AWS.
