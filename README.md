# Free Claude Code --- Guia de instalação

Guia em português para preparar o computador e instalar o **Free Claude
Code (FCC)** no Windows, Linux ou macOS.

> **Importante:** Free Claude Code é um projeto de terceiros, não um
> produto oficial da Anthropic. Ele funciona como uma camada
> intermediária entre um agente de programação e um provedor/modelo de
> IA. "Gratuito" depende do provedor escolhido, dos limites de uso e das
> condições da conta. Não há garantia de uso ilimitado ou de acesso
> gratuito aos modelos Claude.

## Índice

-   [1. Requisitos](#1-requisitos)
-   [2. Windows 10/11](#2-windows-1011)
-   [3. Ubuntu e outras distribuições
    Linux](#3-ubuntu-e-outras-distribuições-linux)
-   [4. macOS](#4-macos)
-   [5. Configurar um provedor de IA](#5-configurar-um-provedor-de-ia)
-   [6. Iniciar e verificar](#6-iniciar-e-verificar)
-   [7. Problemas comuns](#7-problemas-comuns)
-   [8. Segurança](#8-segurança)
-   [9. Links oficiais do projeto](#9-links-oficiais-do-projeto)

## 1. Requisitos

### Hardware recomendado

-   Computador com processador Intel/AMD de 64 bits ou ARM64 compatível.
-   8 GB de RAM recomendados para uso confortável; 4 GB podem funcionar,
    dependendo do sistema e dos programas abertos.
-   Pelo menos 5--10 GB livres para o sistema, ferramentas e
    dependências; deixe mais espaço para projetos.
-   Conexão com a internet para instalar dependências e acessar
    provedores online.

Esses valores são recomendações práticas, não uma garantia de
compatibilidade. Recursos opcionais de voz/modelos locais podem exigir
mais espaço, memória e, em alguns casos, GPU.

### Software

-   Windows 10/11, Linux ou macOS compatível.
-   **uv**, gerenciador de ferramentas e ambientes Python.
-   **Python 3.14**, instalado/gerenciado pelo `uv`.
-   **Git**, necessário para o método de instalação manual e útil para
    projetos de programação.
-   Um provedor de IA compatível e, quando exigido, uma chave de API.
-   Um terminal: PowerShell no Windows ou Bash/Zsh no Linux/macOS.

O instalador do projeto pode instalar ou verificar algumas dependências.
Consulte o README atual do repositório antes de executar scripts, pois
os requisitos e comandos podem mudar.

## 2. Windows 10/11

### 2.1 Abrir o PowerShell

Abra o menu Iniciar, procure **PowerShell** e abra-o. Para instalar no
seu perfil de usuário, normalmente não é necessário abrir como
administrador.

### 2.2 Instalar o Git

Baixe o Git para Windows no site oficial:

https://git-scm.com/download/win

Execute o instalador e mantenha as opções padrão, a menos que tenha uma
necessidade específica. Depois, feche e reabra o PowerShell e confira:

``` powershell
git --version
```

Se o comando não for reconhecido, reinicie o terminal ou verifique se o
Git foi adicionado ao PATH.

### 2.3 Instalar o uv

O projeto recomenda instalar o `uv` pelo instalador oficial:

``` powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Feche e abra novamente o PowerShell. Verifique:

``` powershell
uv --version
```

Atualize o `uv`:

``` powershell
uv self update
```

### 2.4 Instalar Python 3.14

Peça ao `uv` para instalar o Python compatível:

``` powershell
uv python install 3.14
```

Verifique as versões disponíveis:

``` powershell
uv python list
```

Não é necessário configurar manualmente um Python global se o projeto
for executado usando os comandos `uv` recomendados.

### 2.5 Instalar o Free Claude Code

**Opção A --- instalador do projeto (mais simples):**

Consulte primeiro o script e as instruções atuais no repositório:

https://github.com/Alishahryar1/free-claude-code

O projeto publica um instalador PowerShell. O comando de execução remota
pode mudar; confirme o comando na seção de instalação do README atual
antes de executá-lo. Não execute scripts remotos sem confiar no projeto
e sem entender o que eles fazem.

**Opção B --- instalação manual pelo código-fonte:**

``` powershell
git clone https://github.com/Alishahryar1/free-claude-code.git
cd free-claude-code
uv python install 3.14
uv run fcc-server
```

Esse método executa o servidor a partir do repositório. Se a versão
atual do projeto tiver mudado seus comandos, siga o README e os arquivos
de instalação do repositório.

## 3. Ubuntu e outras distribuições Linux

### 3.1 Instalar ferramentas básicas

No Ubuntu/Debian, abra o terminal e execute:

``` bash
sudo apt update
sudo apt install -y git curl ca-certificates
```

### 3.2 Instalar o uv

``` bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Feche e abra novamente o terminal. Se o comando não for encontrado, siga
a mensagem do instalador para atualizar o `PATH`. Confira:

``` bash
uv --version
uv self update
```

### 3.3 Instalar Python 3.14

``` bash
uv python install 3.14
uv python list
```

### 3.4 Instalar e executar o Free Claude Code

Para clonar e executar o projeto a partir do código-fonte:

``` bash
git clone https://github.com/Alishahryar1/free-claude-code.git
cd free-claude-code
uv python install 3.14
uv run fcc-server
```

Para usar o instalador automatizado em vez do método manual, consulte o
comando Linux/macOS publicado no README atual:

https://github.com/Alishahryar1/free-claude-code

**Observação:** em ambientes ARM64, contêineres, Termux ou Ubuntu dentro
de uma VM, algumas dependências podem não oferecer suporte à plataforma.
A instalação pode falhar mesmo que os comandos sejam digitados
corretamente.

## 4. macOS

1.  Instale as ferramentas de linha de comando da Apple, se necessário.

2.  Instale o Git, caso ainda não esteja disponível:
    https://git-scm.com/download/mac

3.  Instale `uv`:

    ``` bash
    curl -LsSf https://astral.sh/uv/install.sh | sh
    ```

4.  Reabra o terminal e instale Python 3.14:

    ``` bash
    uv self update
    uv python install 3.14
    ```

5.  Siga o método automatizado ou manual descrito no README do projeto:
    https://github.com/Alishahryar1/free-claude-code

## 5. Configurar um provedor de IA

O Free Claude Code não cria capacidade de IA por conta própria: ele
encaminha as solicitações a um provedor configurado. As opções e os
nomes dos campos variam conforme a versão do projeto.

1.  Abra o README do projeto e identifique os provedores atualmente
    suportados.
2.  Crie uma conta diretamente no site do provedor escolhido.
3.  Gere uma chave de API, se esse provedor exigir uma.
4.  Abra a interface administrativa/configuração indicada pelo
    instalador ou configure o arquivo `.env` conforme o modelo fornecido
    pelo projeto.
5.  Se o repositório oferecer `.env.example`, copie-o para `.env` e
    edite apenas as variáveis documentadas.

Exemplo de cópia em Linux/macOS:

``` bash
cp .env.example .env
```

No PowerShell:

``` powershell
Copy-Item .env.example .env
```

Preencha **somente** as variáveis necessárias ao provedor escolhido,
seguindo os exemplos atuais do projeto. Não copie chaves de API de
outras pessoas e não publique o arquivo `.env`.

Alguns provedores oferecem cotas gratuitas limitadas; outros cobram por
uso. Confira preço, limites, região atendida e termos de uso antes de
enviar solicitações.

## 6. Iniciar e verificar

O comando para iniciar depende do método de instalação e da versão
atual. No modo de desenvolvimento a partir do repositório, o projeto
documenta:

``` bash
uv run fcc-server
```

Se o instalador tiver criado um comando próprio, como `fcc-server`, use
o comando indicado por ele. Mantenha o terminal do servidor aberto
enquanto estiver usando o serviço.

Em versões que disponibilizam a interface administrativa local, o
endereço e a porta são mostrados pelo próprio servidor ou pelo README
atual. Use o endereço exibido pelo programa; não presuma que a porta
seja sempre a mesma.

Para testar, configure o provedor e valide a conexão na interface ou
pelo procedimento descrito no README. Depois, siga as instruções atuais
para conectar o agente de programação escolhido (por exemplo, Claude
Code, Codex ou outro agente compatível).

## 7. Problemas comuns

### `uv` não é reconhecido

Feche e abra o terminal. Se continuar, confira o caminho de instalação
mostrado pelo instalador do `uv` e adicione esse diretório ao `PATH`
conforme a documentação oficial: https://docs.astral.sh/uv/

### Falha ao instalar dependências Python

-   Atualize o `uv`: `uv self update`.
-   Confira se há espaço em disco e internet.
-   Use `uv python install 3.14`.
-   Leia a mensagem de erro completa; erros de compilação podem indicar
    dependências de sistema ausentes ou plataforma não suportada.
-   Não force versões aleatórias de dependências sem consultar o
    projeto.

### `git` não é reconhecido no Windows

Instale o Git para Windows e reabra o PowerShell.

### O servidor inicia, mas não há respostas do modelo

Verifique se o provedor está configurado, se a chave está correta, se há
cota disponível e se o modelo informado ainda existe. Consulte os logs
do servidor.

### Erros de API, limite ou cobrança

Eles normalmente dependem do provedor, não do instalador. Consulte o
painel e a documentação do provedor.

### Termux, ARM64 ou Ubuntu em VM

O suporte depende das bibliotecas e dos binários usados pela versão
instalada. Se houver erro como `Unsupported platform`,
`ERR_DLOPEN_FAILED` ou falha ao compilar uma dependência, guarde o log
completo e confira os problemas abertos do projeto antes de tentar
substituir bibliotecas manualmente.

## 8. Segurança

-   Baixe o projeto somente do repositório que você verificou.
-   Leia scripts de instalação antes de executá-los, especialmente
    comandos que baixam e executam conteúdo remoto.
-   Nunca publique chaves de API, tokens ou senhas.
-   Não envie arquivos `.env` para GitHub. Adicione-os ao `.gitignore`.
-   Use chaves com permissões limitadas e defina limites de gasto quando
    o provedor oferecer essa opção.
-   Trate qualquer chave de autenticação local do proxy como segredo,
    mesmo que seja apenas para uso local.
-   Não presuma que um modelo é gratuito só porque o projeto é chamado
    "Free Claude Code".

## 9. Links oficiais do projeto

-   Repositório e README:
    https://github.com/Alishahryar1/free-claude-code
-   Documentação do `uv`: https://docs.astral.sh/uv/
-   Instalação do Git: https://git-scm.com/downloads
-   Documentação oficial do Claude Code (produto Anthropic):
    https://docs.anthropic.com/en/docs/claude-code/getting-started

------------------------------------------------------------------------

**Nota:** Este guia é uma orientação geral. Confira sempre o README e os
comandos do repositório antes de instalar, pois o projeto pode mudar. O
Free Claude Code é um projeto de terceiros e não é endossado pela
Anthropic.
