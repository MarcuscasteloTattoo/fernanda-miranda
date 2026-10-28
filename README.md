# Nanda Tattoo | Fernanda Miranda

Site estático: `index.html`, `favicon.png`, `apple-touch-icon.png` e a pasta `assets/`. Não precisa de build. Envie tudo junto, mantendo a estrutura de pastas.

## Publicar na Netlify com domínio do Registro.br

1. Acesse app.netlify.com/drop e arraste a pasta inteira do site. A Netlify gera um endereço `algo.netlify.app`.
2. Crie a conta (grátis) para o site não expirar. Em **Domain management → Add a domain**, digite o domínio (ex.: `nandatattoo.com.br`).
3. No Registro.br: **Meus domínios → domínio → DNS → Editar zona** (se aparecer "Configurar endereçamento", escolha usar os DNS do Registro.br). Crie:
   - Tipo **A**, nome vazio (ou `@`), valor `75.2.60.5`
   - Tipo **CNAME**, nome `www`, valor `seu-site.netlify.app` (o endereço que a Netlify gerou)
   Apague registros A/CNAME antigos que apontem para outra hospedagem.
4. A propagação leva de minutos até 24 h. Depois, a Netlify emite o HTTPS sozinha (Domain management → HTTPS).

## Onde editar

No fim do `index.html`, dentro do `<script>`, o objeto `site`:

- `whatsappBase` e `mensagemWhatsApp`: número e mensagem inicial.
- `webhook`: endereço do webhook do Make que recebe os orçamentos.
- `galeria`: fotos do carrossel "Seu corpo, sua arte, sua identidade", na ordem.
- `avaliacoes`: avaliações do Google (nome e texto).
- `locais`, `tamanhos`, `estilosForm`, `investimentos`: opções do chat de orçamento.

Ficam direto no HTML: frase e fotos do banner, texto do "Sobre a tatuadora", cuidados, endereço e links do rodapé.

## Orçamento (chat)

Ao responder a última pergunta, o site envia ao Make os campos `nome`, `whatsapp`, `whatsapp_numero`, `local_do_corpo`, `tamanho`, `estilo`, `orcamento`, `ideia`, `data_envio` e `pagina`, e em seguida leva a pessoa ao WhatsApp com a mensagem pronta.

No Make, deixe o cenário ligado, clique em "Redetermine data structure" no módulo do webhook e faça um orçamento de teste pelo site publicado. Para acompanhar o envio sem redirecionar, abra o site com `?teste` no fim do endereço.

## Fotos

Cada foto de `assets/portfolio-*` e `assets/estilo-*` tem uma versão menor com `-480` no nome, usada no celular. Ao trocar uma foto, use um nome de arquivo novo (o `_headers` e o `vercel.json` mandam o navegador guardar as fotos em cache por 1 ano).
