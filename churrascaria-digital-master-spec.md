# MASTER SPEC — CHURRASCARIA DIGITAL

**Versão:** 3.0  
**Responsável pelo produto:** Joel Oliveira — Desenvolvimento de Sites  
**Modelo comercial:** Híbrido — sites personalizados com plataforma reutilizável  
**Idioma:** Português brasileiro  
**Status:** Especificação para implementação

## 1. PAPEL DO AGENTE

Atue como uma equipe sênior de engenharia de software composta por:

- Arquiteto de software.
- Desenvolvedor full-stack.
- Engenheiro de banco de dados.
- Especialista em segurança.
- Product designer UX/UI.
- Engenheiro de qualidade.
- Especialista em aplicações SaaS.

Sua missão é implementar uma plataforma completa para churrascarias brasileiras, com qualidade profissional, arquitetura sustentável e interfaces visualmente diferenciadas.

Não entregue apenas um protótipo visual. Implemente funcionalidades reais, testáveis e persistentes.

Não declare uma funcionalidade concluída sem testes e evidências.

## 2. OBJETIVO DO PRODUTO

Criar uma plataforma de gestão e vendas para churrascarias com quatro modalidades:

1. Delivery.
2. Retirada no estabelecimento.
3. Atendimento presencial no salão.
4. Rodízio.

Cada restaurante poderá ativar somente as modalidades que utiliza.

A plataforma também deverá oferecer:

- Site institucional.
- Cardápio digital.
- Pedidos online.
- Integração com WhatsApp.
- Reservas.
- Gestão de mesas e comandas.
- Gestão de rodízio.
- Cozinha.
- Caixa.
- Estoque.
- CRM.
- Relatórios.
- Marketing.
- Gerador de panfletos.
- Notificações.
- Administração e permissões.

## 3. MODELO COMERCIAL HÍBRIDO

Construir um núcleo compartilhado com suporte a múltiplos restaurantes.

Cada restaurante deverá ter:

- Identificador próprio.
- Nome e identidade visual.
- Catálogo independente.
- Equipe e permissões próprias.
- Clientes, pedidos e reservas isolados.
- Configurações próprias.
- Domínio ou subdomínio configurável.
- Módulos habilitados individualmente.

Usar uma arquitetura multi-tenant segura.

Não permitir acesso cruzado entre estabelecimentos.

A primeira versão deve ser preparada para personalização visual e comercial, sem exigir uma infraestrutura separada por restaurante.

Não implementar cobrança de assinaturas da plataforma nesta primeira etapa. Preparar somente a arquitetura para futura monetização recorrente.

## 4. STACK TECNOLÓGICA

Utilizar:

- Next.js com App Router.
- React.
- TypeScript em modo estrito.
- Tailwind CSS.
- Lucide Icons.
- Supabase PostgreSQL.
- Supabase Auth.
- Supabase Realtime.
- Supabase Storage.
- Zod para validação.
- Vitest para testes unitários e integração.
- Playwright para testes de interface e fluxos completos.

Utilizar arquitetura de monólito modular.

Priorizar simplicidade, manutenção e baixo custo operacional.

Não introduzir microsserviços, filas externas ou serviços pagos sem necessidade demonstrada.

## 5. IDENTIDADE VISUAL

Criar uma marca fictícia demonstrativa para uma churrascaria.

Não usar marcas de restaurantes reais.

Paleta inicial:

- Carvão: `#211B17`
- Creme: `#F6F0E7`
- Vermelho-terra: `#9F4334`
- Dourado: `#C69C59`
- Branco: `#FFFFFF`

O site público deverá apresentar:

- Fotografia gastronômica de qualidade.
- Tipografia editorial.
- Hierarquia visual clara.
- Navegação simples.
- Destaque para produtos.
- Layout mobile-first.
- Chamadas para ação evidentes.
- Animações discretas.

Evitar aparência de template SaaS genérico.

O painel administrativo deverá ser mais funcional, mas preservar a identidade gastronômica.

Criar um sistema de temas com tokens visuais e variações de layout para personalização por restaurante.

Utilizar somente imagens com licença adequada ou arquivos autorizados.

## 6. SITE PÚBLICO

### Página inicial
- Hero gastronômico.
- Apresentação da churrascaria.
- Especialidades.
- Produtos em destaque.
- Promoções.
- Horários.
- Localização.
- Redes sociais.
- Botões para pedir e reservar.

### Cardápio
- Categorias.
- Busca.
- Filtros.
- Produtos.
- Fotos.
- Descrições.
- Preços.
- Variações.
- Adicionais.
- Observações.
- Disponibilidade.

### Carrinho
- Inclusão e remoção de itens.
- Alteração de quantidades.
- Adicionais.
- Observações.
- Subtotal.
- Descontos.
- Taxas.
- Total.
- Persistência temporária do carrinho.

### Checkout
- Delivery ou retirada.
- Nome e contato.
- CEP.
- Rua, número e complemento.
- Referência.
- Validação de zona de entrega.
- Taxa de entrega.
- Cupom.
- Forma de pagamento.
- Revisão do pedido.
- Confirmação.

### Acompanhamento
- Número do pedido.
- Status.
- Resumo.
- Atualizações.
- Proteção contra acesso não autorizado.

Não expor dados pessoais apenas por identificadores sequenciais.

## 7. PEDIDOS

Implementar criação de pedidos no servidor com validação completa.

O servidor deverá recalcular todos os valores com base no catálogo vigente.

Registrar snapshots de:

- Nome do produto.
- Preço aplicado.
- Adicionais.
- Quantidade.
- Descontos.
- Taxas.
- Total.

Implementar chave de idempotência para evitar duplicidade.

Estados:

- Recebido.
- Aceito.
- Em preparação.
- Pronto.
- Em entrega.
- Concluído.
- Cancelado.

Validar transições de status.

Registrar quem alterou cada estado e quando.

Não permitir que um cliente modifique diretamente o estado operacional de um pedido.

## 8. WHATSAPP

Criar integração inicial por link oficial `wa.me`.

Após registrar o pedido:

- Gerar resumo formatado.
- Incluir itens e quantidades.
- Incluir endereço quando necessário.
- Incluir total.
- Incluir identificador do pedido.
- Abrir conversa com o número configurado pelo restaurante.

Não considerar o pedido enviado apenas porque o WhatsApp foi aberto.

Preparar uma interface de integração para futura utilização da WhatsApp Business Platform.

Não implementar envio automático sem credenciais e configuração oficial.

## 9. DELIVERY E RETIRADA

### Delivery
- Configuração de zonas atendidas.
- Taxas por região.
- Pedido mínimo opcional.
- Horários de funcionamento.
- Prazo estimado.
- Disponibilidade por modalidade.

O ViaCEP servirá para preenchimento de endereço, não como única validação da área de entrega.

### Retirada
- Sem taxa de entrega.
- Horário desejado.
- Estimativa de preparo.
- Identificação do pedido.
- Confirmação de retirada.

## 10. SALÃO E COMANDAS

Criar:

- Cadastro de mesas.
- Capacidade.
- Mapa visual do salão.
- Status das mesas.
- Abertura de comanda.
- Inclusão de itens.
- Transferência de mesa autorizada.
- Fechamento.
- Histórico.

Uma mesa não poderá possuir duas sessões ativas incompatíveis.

Implementar controle transacional de abertura e fechamento.

O QR Code de mesa deverá ser validado pelo servidor.

Não permitir alteração arbitrária de mesa apenas manipulando parâmetros na URL.

## 11. RODÍZIO

Criar:

- Planos de rodízio.
- Preços por faixa etária.
- Horários de validade.
- Participantes.
- Sessões.
- Extras.
- Bebidas.
- Sobremesas.
- Descontos autorizados.

O preço contratado deverá ser preservado na comanda.

Permitir configuração de regras especiais, sem assumir automaticamente gratuidade ou desconto por idade.

## 12. RESERVAS

Criar:

- Calendário.
- Horários.
- Número de pessoas.
- Capacidade por intervalo.
- Solicitações.
- Confirmações.
- Cancelamentos.
- Não comparecimento.
- Histórico.

Impedir reservas acima da capacidade configurada.

Usar operações transacionais para evitar conflitos simultâneos.

Permitir política de aprovação manual ou automática.

## 13. COZINHA

Criar uma tela operacional para a equipe.

Funcionalidades:

- Pedidos pendentes.
- Itens por estação.
- Horário de entrada.
- Tempo em preparação.
- Prioridades.
- Marcação de pronto.
- Atualização em tempo real.

Preparar suporte futuro para impressão de comandas.

## 14. CAIXA E PAGAMENTOS

Implementar:

- Abertura de caixa.
- Registro de pagamentos.
- Dinheiro.
- Pix manual.
- Cartão presencial.
- Pagamento parcial.
- Divisão de conta.
- Descontos autorizados.
- Sangrias.
- Suprimentos.
- Fechamento.
- Divergências.

Separar estados de pedido e pagamento.

Não marcar Pix manual como pago automaticamente.

Registrar estornos e cancelamentos de maneira auditável.

Não armazenar dados completos de cartões.

## 15. ESTOQUE

Implementar:

- Cadastro de insumos.
- Unidade de medida.
- Saldo.
- Entradas.
- Saídas.
- Ajustes.
- Estoque mínimo.
- Alertas.

Preparar estrutura para fichas técnicas e baixa automática de ingredientes.

Não apresentar custo ou lucro como exato quando os dados de insumos forem incompletos.

## 16. CRM

Implementar:

- Cadastro de clientes.
- Histórico de pedidos.
- Preferências informadas.
- Frequência de compra.
- Consentimentos.
- Segmentação simples.

Respeitar princípios da LGPD.

Não realizar campanhas de mensagens sem base legal e mecanismos adequados de consentimento.

## 17. MARKETING E PANFLETOS

Criar:

- Promoções.
- Cupons.
- Banners.
- Campanhas.
- Períodos de validade.
- Limites de utilização.
- Editor de panfletos.

O editor deverá permitir:

- Escolher modelos.
- Selecionar produtos.
- Inserir imagens.
- Editar textos.
- Ajustar cores.
- Exibir preços.
- Gerar prévia.
- Exportar PNG.

Formatos:

- Instagram 1080 × 1080.
- Stories 1080 × 1920.
- A4 para impressão.

Os materiais deverão ser gerados com dados do estabelecimento.

Não inventar avaliações ou depoimentos.

## 18. RELATÓRIOS

Criar indicadores:

- Vendas por período.
- Pedidos por modalidade.
- Ticket médio.
- Produtos mais vendidos.
- Cancelamentos.
- Formas de pagamento.
- Reservas.
- Ocupação de mesas.
- Desempenho de promoções.
- Movimentações de caixa.

Usar somente dados reais registrados no sistema ou dados demonstrativos explicitamente identificados.

## 19. NOTIFICAÇÕES

Implementar:

- Atualizações via Supabase Realtime.
- Alertas visuais.
- Alertas sonoros opcionais.
- Novos pedidos.
- Novas reservas.
- Alterações de status.
- Reconexão e sincronização.

Preparar notificações Web Push.

O sistema deverá continuar funcionando quando o Realtime estiver temporariamente indisponível, utilizando consultas de reconciliação.

## 20. ADMINISTRAÇÃO

Perfis:

- Proprietário.
- Gerente.
- Caixa.
- Atendente.
- Garçom.
- Cozinha.
- Marketing.

Implementar permissões por ação e recurso.

Verificar autorização no servidor.

Criar histórico de operações críticas.

## 21. BANCO DE DADOS

Modelar pelo menos:

- `restaurants`
- `restaurant_domains`
- `restaurant_settings`
- `restaurant_users`
- `categories`
- `products`
- `product_options`
- `customers`
- `orders`
- `order_items`
- `payments`
- `delivery_zones`
- `tables`
- `table_sessions`
- `rodizio_plans`
- `rodizio_participants`
- `reservations`
- `inventory_items`
- `inventory_movements`
- `cash_sessions`
- `cash_movements`
- `promotions`
- `coupons`
- `marketing_assets`
- `notifications`
- `audit_logs`

Criar chaves estrangeiras, índices, restrições e migrações.

Usar políticas RLS apropriadas.

Garantir isolamento por restaurante, inclusive em consultas, armazenamento e eventos em tempo real.

Não confiar em `restaurant_id` enviado pelo navegador sem validação do contexto autenticado.

## 22. SEGURANÇA

Implementar:

- Autenticação segura.
- Controle de sessão.
- Autorização por perfil.
- RLS.
- Validação Zod.
- Rate limiting em endpoints sensíveis.
- Proteção contra acesso indevido.
- Proteção contra pedidos duplicados.
- Logs de auditoria.
- Segredos em variáveis de ambiente.
- Restrições de upload.
- Políticas de privacidade.
- Procedimentos de backup e recuperação.

Não expor `service_role` keys ao cliente.

## 23. DEMONSTRAÇÃO COMERCIAL

Criar uma churrascaria fictícia com:

- Produtos demonstrativos.
- Categorias.
- Imagens autorizadas.
- Mesas.
- Reservas fictícias.
- Pedidos fictícios.
- Relatórios demonstrativos.

Identificar claramente o ambiente como demonstração.

Separar dados de demonstração de dados reais.

Oferecer mecanismo de restauração do ambiente demo.

Não criar credenciais administrativas públicas com acesso à infraestrutura de produção.

## 24. ETAPAS DE IMPLEMENTAÇÃO

Executar em seis fases.

### Fase 1 — Fundação
- Inicializar projeto.
- Definir arquitetura.
- Criar design system.
- Criar banco e migrações.
- Implementar autenticação e permissões.
- Configurar ambiente.

### Fase 2 — Vendas online
- Site institucional.
- Cardápio.
- Produtos.
- Carrinho.
- Checkout.
- Delivery.
- Retirada.
- WhatsApp.

### Fase 3 — Operação
- Gestão de pedidos.
- Cozinha.
- Painel administrativo.
- Notificações.
- Tempo real.

### Fase 4 — Atendimento presencial
- Mesas.
- Comandas.
- Rodízio.
- Reservas.
- Caixa.

### Fase 5 — Gestão e marketing
- Estoque.
- CRM.
- Relatórios.
- Promoções.
- Cupons.
- Panfletos.

### Fase 6 — Preparação comercial
- Testes automatizados.
- Testes de segurança.
- Auditoria de permissões.
- Otimização.
- Documentação.
- Ambiente demonstrativo.
- Preparação para publicação.

Ao final de cada fase:

1. Executar lint e verificação de tipos.
2. Executar os testes pertinentes.
3. Verificar os fluxos implementados.
4. Corrigir falhas.
5. Atualizar documentação.
6. Registrar pendências.
7. Apresentar critérios de aceite.
8. Solicitar aprovação antes de avançar para a fase seguinte.

## 25. CRITÉRIOS DE ACEITE

O produto será considerado pronto para demonstração comercial completa quando:

- O site público estiver responsivo e funcional.
- Produtos puderem ser administrados e persistidos.
- Pedidos forem registrados com preços validados no servidor.
- O painel receber pedidos reais do banco.
- Os estados dos pedidos funcionarem.
- O WhatsApp abrir com resumo correto.
- O delivery validar regiões e taxas.
- Reservas respeitarem capacidade.
- Mesas e comandas funcionarem.
- Rodízio calcular corretamente os valores.
- Pagamentos e caixa forem consistentes.
- Promoções aplicarem regras válidas.
- Panfletos puderem ser exportados.
- Permissões impedirem acessos indevidos.
- Restaurantes não conseguirem acessar dados uns dos outros.
- Os principais fluxos possuírem testes automatizados.
- A documentação de implantação estiver completa.

## 26. DOCUMENTAÇÃO OBRIGATÓRIA

Manter:

- `README.md`
- `docs/architecture.md`
- `docs/database.md`
- `docs/design-system.md`
- `docs/business-rules.md`
- `docs/security.md`
- `docs/deployment.md`
- `docs/testing.md`
- `docs/roadmap.md`
- `.env.example`

## 27. REGRAS DE EXECUÇÃO DO CODEX

Antes de programar:

1. Inspecione o repositório existente.
2. Identifique tecnologias e arquivos.
3. Não apague código existente sem justificativa e aprovação.
4. Apresente o plano de implementação.
5. Identifique dependências externas.
6. Confirme quais serviços estão configurados.

Durante a implementação:

- Trabalhe por fases.
- Faça alterações pequenas e verificáveis.
- Priorize código reutilizável.
- Não use dados simulados silenciosamente.
- Não crie botões sem funcionalidade.
- Não invente integrações.
- Não declare testes aprovados sem executá-los.
- Não publique em produção sem autorização.

Se faltar uma credencial ou serviço externo, implemente a interface e os contratos necessários, documente a pendência e não simule uma integração real.

## 28. PRIMEIRA AÇÃO

Comece pela Fase 1.

Apresente:

- Estrutura de diretórios.
- Arquitetura de módulos.
- Modelo inicial do banco.
- Estratégia multi-tenant.
- Sistema de temas.
- Plano de testes.
- Dependências.
- Critérios de aceite da fase.

Depois implemente a fundação, execute as verificações disponíveis e apresente o resultado.

Não tente concluir as seis fases em uma única resposta ou alteração.
