# Desk Mini Kiosk para GitHub Pages

Pacote final pronto para publicar uma página estática de kiosk no **Cisco Desk Mini** com **3 botões de chamada para plataformas diferentes**:

- Brasil → Microsoft Teams
- USA → Webex Meeting
- EUR → Google Meet

## Estrutura do pacote

- `index.html` → página principal do kiosk
- `.nojekyll` → evita processamento Jekyll no GitHub Pages
- `README.md` → instruções de publicação

## Ajuste dos links das reuniões

Abra o arquivo `index.html` e localize o bloco `CONFIG.services`.
Substitua os 3 links abaixo pelos links reais das reuniões:

- Brasil → `https://teams.microsoft.com/l/meetup-join/EXEMPLO-BRASIL`
- USA → `https://example.webex.com/meet/EXEMPLO-USA`
- EUR → `https://meet.google.com/EXEMPLO-EUR`

## Como publicar no GitHub Pages

1. Crie um repositório novo no GitHub, por exemplo `desk-mini-kiosk`
2. Faça upload destes 3 arquivos para a raiz do repositório:
   - `index.html`
   - `.nojekyll`
   - `README.md`
3. No GitHub, abra `Settings > Pages`
4. Em **Build and deployment**, selecione:
   - **Source:** Deploy from a branch
   - **Branch:** `main`
   - **Folder:** `/ (root)`
5. Salve e aguarde a publicação

A URL final normalmente será:

`https://SEU-USUARIO.github.io/desk-mini-kiosk/`

## Configuração no Cisco Desk Mini

Depois de publicar, configure a URL do kiosk no equipamento:

```bash
xConfiguration WebEngine Mode: On
xConfiguration UserInterface Kiosk URL: "https://SEU-USUARIO.github.io/desk-mini-kiosk/"
xConfiguration UserInterface Kiosk Mode: On
```

## Recomendações adicionais

```bash
xConfiguration UserInterface SettingsMenu Mode: Locked
xConfiguration Audio Ultrasound MaxVolume: 0
xConfiguration UserInterface Assistant Mode: Off
```

## Observação

O GitHub Pages publica esta página como site estático. A navegação para Microsoft Teams, Webex Meeting e Google Meet é feita pelo WebEngine do Cisco Desk Mini, aproveitando os recursos do equipamento para abrir a chamada no próprio dispositivo. Em ambiente corporativo, é recomendado validar os links finais e o comportamento no equipamento antes de colocar em produção.
