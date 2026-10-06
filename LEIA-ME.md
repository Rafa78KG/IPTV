# M3U IPTV para TV LG (webOS)

Player que entra com **host, usuário e senha** do painel (Xtream Codes) e monta a playlist. Não traz canais nem credenciais.

A URL gerada é:

`http://HOST/get.php?username=USUARIO&password=SENHA&type=m3u_plus&output=m3u8`

Host pode ser `servidor.com:8080` ou `http://servidor.com:8080`. A conta fica salva só no navegador da TV.

## Uso

1. Hospede a pasta em HTTPS e abra no navegador da LG, ou instale via Developer Mode (`ares-package`).
2. Preencha host, usuário e senha. HLS é o formato recomendado na TV.
3. Setas, OK, Voltar, vermelho = favorito, verde = busca, números = zap.

Arquivo único também funciona se você abrir `index.html` num servidor local. Abrir o arquivo direto (`file://`) costuma bloquear o download da lista.

## Instalar como app (Developer Mode)

1. Na TV: configurações → geral → habilitar **Developer Mode** e anotar a senha (app LG Developer Mode no celular).
2. No PC, instale o [webOS TV CLI](https://webostv.developer.lge.com/develop/tools/cli-installation).
3. Gere ícones PNG 80×80 (`icon.png`) e 130×130 (`largeIcon.png`) na pasta.
4. Empacote e instale:

```bash
ares-package ./lg-m3u-iptv
ares-install --device tv com.iptv.m3u.lg_1.0.0_all.ipk
ares-launch --device tv com.iptv.m3u.lg
```

Publicar na LG Content Store exige conta de desenvolvedor LG e revisão. Sideload via Developer Mode é o caminho para uso próprio.

## Limitações

- Muitos provedores bloqueiam CORS ou só entregam stream em app próprio. Se der erro, o link precisa permitir o navegador da TV, ou um proxy na sua rede.
- Formatos que não são HLS nem MPEG-TS (alguns RTMP/UDP) não tocam no navegador da webOS.
- Use somente conteúdo que você tem direito de assistir.
