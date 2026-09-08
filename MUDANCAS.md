# v126 — Reserva, impressão sem ambiguidade, e limpeza visual

- **📅 Nova Reserva no painel**: botão na aba Reservas abre um modal pra registrar uma reserva recebida por telefone/balcão/WhatsApp direto do painel, com data e horário pré-programados — mesma lógica de horários por dia da semana que o cliente já usa no cardápio (só mostra horários dentro do funcionamento daquele dia, avisa "fechado" nos dias sem expediente). Usa o mesmo endpoint do cliente, então segue as mesmas regras (pendente/confirmada conforme o Aceite Automático de Reserva).
- **Bug corrigido — reserva imprimia fora de hora**: a elegibilidade de impressão automática de reserva usava só o interruptor geral (Configurações → Impressão Automática), sem checar se a loja estava aberta nem se o Aceite Automático de Reserva estava ligado — diferente de pedido, que já seguia essa regra desde a v92. Agora reserva só imprime sozinha quando a loja está **aberta** e o **Aceite Automático de Reserva** está ligado; continua podendo ser *criada* com a loja fechada (é assim que dá pra reservar um dia futuro com antecedência), só não sai na impressora sozinha nesse caso.
- **Bug corrigido (auditoria) — trava de impressão presa no Modo Teste**: no Agente Local, imprimir uma reserva com Modo Teste ligado reclamava a trava anti-duplicidade e nunca a liberava, deixando a reserva "presa" por até 90 segundos como se já tivesse sido impressa de verdade (sem nunca ter saído papel nenhum). Corrigido — a trava agora é liberada na hora quando é só simulação.
- **Central de Impressão → Impressoras por Estação simplificado**: cada via agora aparece recolhida por padrão (ícone, nome, método, Ativa, Testar) em vez de mostrar todos os campos e parágrafos de explicação sempre abertos. Um botão "⚙️ Configurar" expande IP/porta, caminho USB, tempo de preparo e a explicação do método só quando precisar. Nenhuma função foi removida — só reorganizada pra ocupar menos espaço na tela.
- Auditoria geral de impressão/duplicidade: revisadas as travas de idempotência de pedido (geocodificação antes da gravação, chave de idempotência), o claim por pedido+via do Agente Local, e o ciclo de vida completo da trava de reserva — nenhum outro ponto de duplicidade encontrado além do já corrigido acima.

# v120 — Evolução de simplicidade e responsividade

- Badge Global removido da interface de edição.
- Selos locais pré-prontos no produto: Mais vendido, Novidade, Premium, Recomendado e Sem selo.
- Badge local passa a aparecer sobre a foto no cardápio do cliente, com acabamento vermelho Shogatsu.
- Central de Impressão compactada e responsiva.
- Impressão automática preservada; a configuração continua usando `cfg.print`.
- Aviso Sonoro do Cliente unificado visualmente com Alertas de pedidos, preservando IDs e funções existentes.
- Funcionamento por dia convertido para grade compacta e responsiva.
- Não foram alteradas APIs, banco ou páginas do cliente além do estilo/posição do badge no cardápio.


## v127 — evolução solicitada
- Corrigido o modal de **Nova Reserva**: o overlay é movido para `body` ao abrir e não fica preso a uma página oculta.
- Central de Impressão: padrão de fonte reduzido para **14 px**, com largura padrão segura de **48 colunas** para térmicas de 80 mm/Bematech quando não houver largura configurada.
- Impressão térmica: adicionado **bip duplo** ESC/POS ao final da impressão.
- Cards de Configurações: controles antigos em menu `⋮` substituídos por ações diretas e compactas: **Expandir/Fechar, Ocultar/Mostrar, Fixar, 1º campo, Favoritar e Fechar**.
- `Fixar` passou a usar posicionamento sticky no topo do grupo; `Ocultar` não desativa mais os próprios controles.
