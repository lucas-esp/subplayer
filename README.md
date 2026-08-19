# SubPlayer

**SubPlayer** é um aplicativo nativo para TVs LG Smart (webOS) que permite assistir canais IPTV, VOD (Vídeo sob Demanda) e Séries usando as credenciais do seu provedor **Xtream Codes**.

> Versão: 2.5.0

---

## Funcionalidades

- TV ao vivo com lista de canais e navegação por categorias
- EPG (Guia de Programação Eletrônico) com informações em tempo real
- Suporte a VOD e Séries com navegação por episódios
- Sistema de favoritos para acesso rápido aos canais preferidos
- Navegador de canais sobreposto enquanto assiste TV ao vivo
- Busca por canais e categorias
- Navegação completa pelo controle remoto (sem necessidade de mouse)
- App leve em arquivo único — rápido e responsivo

---

## Requisitos

- TV LG Smart rodando **webOS 3.x ou superior**
- TV deve estar em **Modo Desenvolvedor** (veja a configuração abaixo)
- Uma assinatura **Xtream Codes** válida (URL, usuário e senha)
- Um computador com **Node.js** e **ares-cli** instalados

---

## Instalação

### 1. Instalar o ares-cli

#### macOS (via Homebrew)

```bash
brew install node
npm install -g @webosose/ares-cli
```

#### Windows

```bash
npm install -g @webosose/ares-cli
```

---

### 2. Ativar o Modo Desenvolvedor na sua TV LG

1. Na TV, vá em **Configurações → Sobre esta TV**
2. Clique no número da versão **5 vezes rapidamente** para desbloquear o menu secreto
3. Ative o **Modo Desenvolvedor**
4. Anote o **endereço IP da TV** (Configurações → Rede → Conexão Wi-Fi → Configurações avançadas)

---

### 3. Configurar o dispositivo no ares-cli

```bash
ares-setup-device
```

Preencha os campos:
- **Nome do dispositivo:** `minhatv` (ou qualquer nome)
- **Endereço IP:** o IP da sua TV (ex: `192.168.1.100`)
- **Porta:** `9922`
- **Usuário:** `prisoner`
- **Autenticação:** password
- **Senha:** *(deixe em branco, só pressione Enter)*

Verifique a conexão:

```bash
ares-novacom --device minhatv --getkey
```

Uma mensagem de confirmação aparecerá na TV — aceite.

---

### 4. Empacotar e Instalar o App

Clone este repositório:

```bash
git clone https://github.com/lucas-esp/subplayer.git
cd subplayer
```

Empacote o app:

```bash
ares-package .
```

Isso gera um arquivo `.ipk` (ex: `com.streamplayer.app_2.5.0_all.ipk`).

Instale na TV:

```bash
ares-install --device minhatv com.streamplayer.app_2.5.0_all.ipk
```

Abra o app:

```bash
ares-launch --device minhatv com.streamplayer.app
```

---

## Configuração Inicial

1. Abra o **SubPlayer** na sua TV
2. Na **Tela Inicial**, selecione **Conectar / Configurações**
3. Informe as credenciais do seu provedor Xtream Codes:
   - **URL do servidor** (ex: `http://seuprovedor.com:8080`)
   - **Usuário**
   - **Senha**
4. Pressione **Conectar** — os canais e categorias carregarão automaticamente

---

## Navegação pelo Controle Remoto

| Botão | Ação |
|-------|------|
| Setas direcionais | Navegar pelos menus |
| OK / Enter | Selecionar / Confirmar |
| Voltar | Retroceder / Fechar |
| Play/Pause | Controlar reprodução |
| Canal +/- | Trocar canal durante a reprodução |
| 0–9 | Digitar número do canal diretamente |

---

## Solução de Problemas

**App não instala?**
- Verifique se o Modo Desenvolvedor está ativo e que a TV está na mesma rede que o computador.

**TV não encontrada pelo ares-cli?**
- Confira o endereço IP e se a porta `9922` está acessível.

**Canais não carregam?**
- Verifique se a URL, usuário e senha do Xtream Codes estão corretos.

**Tela preta ao reproduzir?**
- Alguns streams exigem codecs específicos. Teste outro canal para confirmar que o app está funcionando.

---

## Licença

MIT — livre para usar e modificar.
