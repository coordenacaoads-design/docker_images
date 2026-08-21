# Imagens Docker por Período

Um `Dockerfile` por programa, organizado em pastas por período. Todos usam
imagens base oficiais (Ubuntu, Debian slim, ou imagens oficiais das
próprias ferramentas como `python`, `node`, `mysql`, `eclipse-temurin`).

## Como usar

Para cada pasta:

```bash
cd periodoX/nome-do-programa
docker build -t nome-do-programa .
docker run -it --rm nome-do-programa
```

Cada `Dockerfile` tem comentários com observações específicas de uso
(portas, variáveis de ambiente, flags especiais). Os destaques:

- **VS Code** (`vscode`): expõe a porta 8080. Defina uma senha com
  `docker run -e PASSWORD=suasenha -p 8080:8080 vscode`.
- **MySQL Server** (`mysql`): a senha de root não vem embutida na imagem
  por segurança. Rode com
  `docker run -e MYSQL_ROOT_PASSWORD=suasenha -e MYSQL_DATABASE=aula_db -p 3306:3306 mysql`.
  Scripts `.sql` colocados em `mysql/init/` rodam automaticamente na
  primeira inicialização.
- **DBeaver → CloudBeaver** (`dbeaver-cloudbeaver`): expõe a porta 8978.
  A versão do CloudBeaver está fixada no Dockerfile; confira releases
  novas em https://github.com/dbeaver/cloudbeaver/releases se o link
  parar de funcionar.
- **RStudio Desktop → RStudio Server** (`rstudio`): expõe a porta 8787,
  login `rstudio` / senha `rstudio` (troque em produção).
- **Wireshark → tshark** (`wireshark-tshark`): para capturar pacotes de
  verdade, rode com `docker run --cap-add=NET_RAW --cap-add=NET_ADMIN --network host ...`.
- **Postman → Newman** (`postman-newman`): rode collections com
  `docker run -v $(pwd):/etc/newman postman-newman run minha-collection.json`.
- **Android Studio → Android SDK Command-line Tools** (`android-sdk`):
  não inclui a IDE gráfica nem o emulador (o emulador exige KVM/GUI, que
  não funciona bem dentro de container). Serve para compilar/testar apps
  via Gradle/sdkmanager.
- **Docker Community Edition** (`docker-ce`, usado no 4º e 5º período):
  para rodar o Docker Engine dentro do container ("Docker-in-Docker"),
  use `docker run --privileged docker-ce`. Alternativa mais leve e
  recomendada em ambientes de aula: usar só a CLI e apontar para o
  Docker do host com
  `docker run -v /var/run/docker.sock:/var/run/docker.sock docker-ce docker ps`.
- **n8n**: expõe a porta 5678 (`http://localhost:5678`).
- **JMeter / MLflow / Ollama**: expõem, respectivamente, a interface CLI,
  a porta 5000 e a porta 11434.

## Ferramentas gráficas → equivalente de linha de comando

Como combinado, containers Docker não têm tela por padrão. Para os
programas que são apps gráficos de desktop, foi usado o equivalente
oficial mais próximo que roda sem interface gráfica local:

| Programa (GUI)      | Equivalente usado na imagem          |
|----------------------|---------------------------------------|
| VS Code               | code-server (VS Code via navegador)  |
| DBeaver               | CloudBeaver CE (via navegador)       |
| RStudio Desktop       | RStudio Server (via navegador)       |
| Wireshark             | tshark (CLI oficial do projeto)      |
| Postman (Desktop)     | Newman (CLI oficial do Postman)      |
| Android Studio        | Android SDK Command-line Tools       |

Repare que code-server, CloudBeaver e RStudio Server ainda entregam uma
interface **gráfica**, só que servida por HTTP e acessada pelo
navegador — não uma janela nativa. Já tshark, Newman e o SDK do Android
são mesmo só linha de comando, sem nenhuma tela.

## Itens que ficaram de fora

Três programas da lista original não têm um caminho direto e confiável
para virar uma imagem Docker utilizável, e por isso não foram incluídos:

- **VirtualBox + Kali Linux** (3º período): VirtualBox é um hipervisor
  tipo 2, e rodar virtualização aninhada (um hipervisor dentro de um
  container, que por sua vez já roda sobre outro kernel) é instável e
  não tem suporte oficial. O caminho recomendado para isso continua
  sendo instalar o VirtualBox diretamente na máquina física/VM dos
  alunos, e não em Docker.
- **Cisco Packet Tracer** (3º período): é um software proprietário da
  Cisco, distribuído só através de login na Cisco Networking Academy.
  Não existe instalador redistribuível para automatizar em um
  Dockerfile — precisa ser baixado manualmente por cada aluno com
  conta própria.
- **UiPath Community** (4º período, opção junto com n8n): só roda em
  Windows (não tem build Linux), então não é compatível com containers
  Docker convencionais. Optamos apenas pelo **n8n**, que já cobre a
  necessidade de automação de fluxos e roda nativamente em Linux/Docker.

## Programas que se repetem entre períodos

Para manter "um Dockerfile por programa" mesmo quando o mesmo programa
aparece em mais de um período, o mesmo conteúdo foi duplicado nas
pastas correspondentes (sem symlinks, para que cada pasta funcione
sozinha com `docker build .`):

- **VS Code**: `periodo1/vscode` e `periodo2/vscode`
- **JDK**: `periodo2/jdk` e `periodo4/jdk`
- **Docker Community Edition**: `periodo4/docker-ce` e `periodo5/docker-ce`

## Estrutura de pastas

```
docker-imagens/
├── periodo1/
│   ├── vscode/
│   └── python/
├── periodo2/
│   ├── mysql/
│   ├── dbeaver-cloudbeaver/
│   ├── vscode/
│   ├── gcc-mingw/
│   ├── jdk/
│   └── rstudio/
├── periodo3/
│   ├── plantuml/
│   ├── nodejs/
│   ├── postman-newman/
│   └── wireshark-tshark/
├── periodo4/
│   ├── android-sdk/
│   ├── flutter/
│   ├── git/
│   ├── jdk/
│   ├── docker-ce/
│   └── n8n/
└── periodo5/
    ├── pytest-junit/
    ├── jmeter/
    ├── selenium/
    ├── mlflow/
    ├── dvc/
    ├── ollama/
    ├── python-huggingface/
    └── docker-ce/
```

## Observação sobre versões

Algumas imagens baixam um binário/versão específica via `wget`/`curl`
(CloudBeaver, RStudio Server, Gradle, JMeter, Android cmdline-tools,
JUnit console). Esses links podem mudar quando o projeto lança novas
versões — se o build falhar por 404, é sinal de que a versão fixada no
`ENV` do Dockerfile precisa ser atualizada para a mais recente.
