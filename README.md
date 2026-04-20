# Desk Mini Kiosk para produção

Pacote final pronto para publicar uma página estática de kiosk no **Cisco Desk Mini** com 3 opções de chamada:

- Brasil → Microsoft Teams
- USA → Webex Meeting
- EUR → Google Meet

## Estrutura do pacote

- `index.html` → página principal do kiosk
- `.nojekyll` → evita processamento Jekyll no GitHub Pages
- `README.md` → instruções de publicação e produção

## Links configurados no projeto

O `index.html` já está configurado com os links finais:

- Brasil → `https://teams.microsoft.com/meet/248702429057970?p=RAdyJ7Ml2pNBrDtwiz`
- USA → `sip:25327218092@napit.webex.com`
- EUR → `https://meet.google.com/cjg-wubf-zwh`

## Publicação no GitHub Pages

1. Crie um repositório novo no GitHub, por exemplo `desk-mini-kiosk`
2. Faça upload destes arquivos para a raiz do repositório:
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

## Configuração recomendada no Cisco Desk Mini

Depois de publicar, configure a URL do kiosk no equipamento:

```bash
xConfiguration WebEngine Mode: On
xConfiguration WebEngine Features SipUrlHandler: On
xConfiguration UserInterface Kiosk URL: "https://SEU-USUARIO.github.io/desk-mini-kiosk/"
xConfiguration UserInterface Kiosk Mode: On
```

## Recomendações adicionais para produção

```bash
xConfiguration UserInterface SettingsMenu Mode: Locked
xConfiguration Audio Ultrasound MaxVolume: 0
xConfiguration UserInterface Assistant Mode: Off
```

## Ajustes aplicados no index.html para compatibilidade

- página leve, sem bibliotecas externas
- botões com navegação validada apenas para `https://` e `sip:`
- feedback visual ao abrir reunião
- prevenção contra múltiplos toques seguidos
- retorno ao menu e retry em caso de falha de abertura
- reset automático por inatividade
- fluxo USA otimizado para SIP nativo do Cisco Desk Mini

## Checklist rápida antes de produção

- validar abertura do Microsoft Teams no botão Brasil
- validar abertura SIP/Webex no botão USA
- validar abertura do Google Meet no botão EUR
- confirmar que `SipUrlHandler` está habilitado
- confirmar funcionamento após encerrar cada reunião
- confirmar acesso à página do GitHub Pages a partir da rede corporativa

## Observação

O projeto foi ajustado para máxima compatibilidade prática com o Cisco Desk Mini, mas a experiência final também depende de rede, políticas corporativas, permissões de plataforma e versão do RoomOS. Antes da entrada em produção, faça um teste completo no equipamento real com os três fluxos de reunião.
