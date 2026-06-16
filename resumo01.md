# Resumo Geral do Semestre — ACM (Ambientes de Computação Modernos)

**Curso:** ETEC 2026 — 1º Semestre — ACM
**Repositório:** https://github.com/crebollobr/etec_2026_s1_acm
**Material de estudo para a Prova 01 (22/06) e a Prova 02 / recuperação (29/06)** — conteúdo **até 15/06**.

---

## 🗺️ Mapa do Semestre (até 15/06)

| Período | Módulo | Pontos-chave |
|---|---|---|
| Fev–Mar | **Linux básico** | Comandos de arquivo, kernel/shell, FHS, disco, processos, rede |
| Abril | **Shell Script** | Variáveis, shebang, permissões, argumentos, condicionais, loops, funções |
| Abr–Mai | **Segurança e Virtualização** | Senhas/hash, PAM; VM × contêiner, hypervisors, QEMU; acesso remoto |
| Maio | **Docker** | Imagem × contêiner, portas, volumes, redes, Dockerfile, Compose |
| 08–15/06 | **Kubernetes (início)** | Pods, MicroK8s, volumes, Deployment, Service, YAML declarativo |

---

## 1) Linux — Comandos Essenciais

- **Navegação/arquivos:** `pwd` (pasta atual), `cd` (muda de pasta), `ls` (lista; `ls -a` mostra ocultos), `mkdir` (cria pasta), `touch` (cria arquivo), `cat` (mostra conteúdo), `mv` (move/renomeia).
- **Busca e empacotamento:** `grep` (procura texto), `find` (procura arquivos), `tar` (empacota/arquiva), `vim` (editor de texto).
- **Kernel × Shell:** o **kernel** gerencia o hardware; o **shell** interpreta os comandos.
- **Ajuda e ambiente:** `man` (manual), `history` (histórico), variáveis de ambiente (`PATH`, `LANG`).

## 2) Linux — Sistema, Disco, Processos e Rede

- **FHS (hierarquia):** `/etc` (configurações), `/home` (usuários), `/var` (logs), `/dev` (dispositivos).
- **Disco:** `df -h` (espaço livre/usado), `du -sh` (tamanho de pastas), `mount`/`umount`.
- **Processos e identidade:** `ps aux` e `top` (processos), `whoami` e `id` (usuário), `uname -a` (kernel).
- **Rede:** `ip addr` (interfaces/IP), `ip route` (rotas), `ping` (testa conexão), `ss` (conexões), **UFW** (firewall).

## 3) Shell Script

- **Shebang:** primeira linha `#!/bin/bash` — diz qual interpretador executa o script.
- **Permissão:** `chmod +x script.sh` transforma o arquivo em executável.
- **Variáveis:** cria com `NOME="Maria"`, usa o valor com `$NOME`.
- **Argumentos:** `$1`, `$2`... são os valores passados ao script (`./script.sh valor1`).
- **Estruturas:** condicionais `[[ ]]`, loops `for` e `while`, aritmética `(( ))`, **funções** para reaproveitar código.

## 4) Segurança

- **Senhas:** ficam em `/etc/shadow`, guardadas como **hash** (SHA-512), nunca em texto puro.
- **PAM:** módulos que decidem **como/onde** validar a autenticação.
- **AAA:** Autenticação, Autorização e Auditoria (Accounting).

## 5) Virtualização

- **Bare metal × hypervisor:** **Tipo 1** roda direto sobre o hardware (datacenter); **Tipo 2** roda como aplicativo dentro de um SO (uso pessoal).
- **QEMU:** emulador/virtualizador de máquinas.
- **VM × Contêiner:** a **VM** simula uma máquina completa (com SO próprio); o **contêiner** **compartilha o kernel** do host — por isso é mais leve e rápido.

## 6) Docker

- **Imagem × Contêiner:** a **imagem** é um molde **somente leitura**; o **contêiner** é a imagem **em execução**.
- **Comandos:** `docker run` (executa), `-d` (segundo plano), `-p` (mapeia porta), `-v` (volume, persiste dados), `docker ps` (lista contêineres), `docker images` (lista imagens).
- **Dockerfile:** arquivo para **construir uma imagem personalizada** (`docker build -t nome .`).
- **Docker Compose:** sobe **vários contêineres** de uma vez, definidos em um único arquivo **YAML** (`docker compose up`).

## 7) Kubernetes (aulas 08/06 e 15/06)

- **Kubernetes (K8s):** **orquestrador de contêineres** — automatiza gerenciamento, recuperação de falhas e escalabilidade.
- **Pod:** a **menor unidade**; "envelope" que embrulha um ou mais contêineres.
- **MicroK8s:** distribuição leve do Kubernetes (instalada via `snap`).
- **Volume (`hostPath`):** guarda os dados **fora** do contêiner para que não se percam quando ele é recriado.
- **YAML / Declarativo:** descreve-se o **estado desejado** em arquivo e aplica-se com `kubectl apply -f`. Isso é **Infraestrutura como Código** (versionável no Git).
- **Deployment:** mantém o **número de réplicas** do Pod sempre rodando; se um Pod morre, o **ReplicaSet** cria outro (pilar da **resiliência**).
- **Service:** dá um **endereço estável** para acessar os Pods (que têm IP/nome efêmeros), encontrando-os pela **label**.

---

## ✅ Checklist de estudo

- [ ] Comandos básicos: `ls`, `cd`, `mkdir`, `cat`, `grep`, `tar`, `df -h`, `ps aux`, `ip addr`.
- [ ] FHS: `/etc` (config) e `/etc/shadow` (senhas).
- [ ] Shell script: shebang, `chmod +x`, `$NOME`, `$1`, loops.
- [ ] Segurança: onde ficam as senhas e o que é hash.
- [ ] Virtualização: VM × contêiner; hypervisor Tipo 1 × Tipo 2.
- [ ] Docker: imagem × contêiner, `-p`, `-v`, Dockerfile, Compose.
- [ ] Kubernetes: Pod, Deployment (réplicas/resiliência), Service, YAML declarativo.
