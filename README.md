# Desk Mini Kiosk para GitHub Pages

Este pacote publica uma página estática pronta para uso em Cisco Desk Mini com 3 opções de suporte via Microsoft Teams:

- Brasil
- USA
- EUR

## Arquivos

- `index.html` → página principal do kiosk
- `.nojekyll` → evita processamento Jekyll no GitHub Pages

## Como publicar no GitHub Pages

1. Crie um repositório novo no GitHub, por exemplo: `desk-mini-kiosk`
2. Envie os arquivos deste pacote para a raiz do repositório
3. No GitHub, abra **Settings > Pages**
4. Em **Build and deployment**, selecione:
   - **Source:** Deploy from a branch
   - **Branch:** `main`
   - **Folder:** `/ (root)`
5. Salve e aguarde a publicação
6. A URL final normalmente fica assim:
   - `https://SEU-USUARIO.github.io/desk-mini-kiosk/`

## Ajuste dos links do Teams

Edite o bloco `services` dentro do `index.html` e substitua:

- `SEU-LINK-BRASIL`
- `SEU-LINK-USA`
- `SEU-LINK-EUR`

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

Para operação estável com Microsoft Teams, substitua os placeholders por links reais de reunião ou atendimento.
