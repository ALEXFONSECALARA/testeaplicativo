# v120 — Evolução de simplicidade e responsividade

- Badge Global removido da interface de edição.
- Selos locais pré-prontos no produto: Mais vendido, Novidade, Premium, Recomendado e Sem selo.
- Badge local passa a aparecer sobre a foto no cardápio do cliente, com acabamento vermelho Shogatsu.
- Central de Impressão compactada e responsiva.
- Impressão automática preservada; a configuração continua usando `cfg.print`.
- Aviso Sonoro do Cliente unificado visualmente com Alertas de pedidos, preservando IDs e funções existentes.
- Funcionamento por dia convertido para grade compacta e responsiva.
- Não foram alteradas APIs, banco ou páginas do cliente além do estilo/posição do badge no cardápio.


## v123 — limpeza e identidade visual
- Removido `public/admin-cardapio.html`, que era apenas um atalho duplicado; a URL antiga agora redireciona no servidor para `/painel.html#cardapio`.
- Aplicado o logo PNG fornecido pelo restaurante aos favicons e ícones PWA existentes.
- Adicionado `public/favicon.png` como favicon PNG canônico.
- Cache do Service Worker atualizado para v8 para entregar a nova identidade visual.
- Nenhuma página pública ativa foi removida: todas continuam preservadas porque são referenciadas por links, manifests ou fluxos do sistema.
