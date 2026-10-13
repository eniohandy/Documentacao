# Researcher: Levantamento de Custos de LLMs (Google, Anthropic, OpenAI, DeepSeek, Z.ai e OpenRouter)

We found **8 sources** on LLM pricing and cost estimation, organized by type below.

---

## 🔧 Technical (6)

| # | Title | Source | Date |
|---|-------|--------|------|
| 1 | [Claude Models Overview & Pricing](https://platform.claude.com/docs/en/models/overview) | Anthropic Platform Docs | 2026 |
| 2 | [Gemini Developer API Pricing](https://ai.google.dev/gemini-api/docs/pricing) | Google AI for Developers | 2026 |
| 3 | [DeepSeek API Models & Pricing](https://api-docs.deepseek.com/quick_start/pricing) | DeepSeek API Docs | 2026 |
| 4 | [Z.AI API Pricing Overview](https://docs.z.ai/guides/overview/pricing) | Z.AI Developer Document | 2026 |
| 5 | [OpenRouter Models & Pricing Directory](https://openrouter.ai/models) | OpenRouter | 2026 |
| 6 | [OpenRouter Platform Plans & Fees](https://openrouter.ai/pricing) | OpenRouter | 2026 |

**(1)** Documentação oficial da Anthropic detalhando os preços de entrada e saída por 1M de tokens para Claude Sonnet, Opus e Haiku, além de descontos de prompt caching e Batch API.

**(2)** Tabela oficial de preços da API do Google Gemini, especificando taxas padrão, lotes (Batch com 50% de desconto) e context caching para as linhas Gemini 2.5 Flash, 3.8 Flash, Gemini Pro e Gemini 4 Argon.

**(3)** Documentação oficial de preços da DeepSeek, cobrindo modelos como DeepSeek-V4.1-Flash e DeepSeek-V4-Pro com tarifas diferenciadas para horários de pico e fora de pico (off-peak com 50% de desconto), bem como taxas reduzidas para cache hits.

**(4)** Guia oficial de precificação da Z.ai para a família GLM (GLM-5.3-Flash, GLM-5.3-FlashX e GLM-5.3), demonstrando tarifas por milhão de tokens e opções com camada gratuita.

**(5)** Catálogo comparativo com mais de 500 modelos no OpenRouter, permitindo roteamento dinâmico e visualização de preços unificados entre diferentes provedores em uma só interface.

**(6)** Estrutura de planos do OpenRouter (Free, Standard e Business), detalhando taxas de plataforma (5.5% no Standard pay-as-you-go) e benefícios de gerenciamento de chaves e controle de custos.

---

## 📊 Reports (2)

| # | Title | Source | Date |
|---|-------|--------|------|
| 7 | [OpenAI API Pricing: All Models Breakdown](https://apicostcompare.com/providers/openai-api-pricing) | API Cost Compare | 2026 |
| 8 | [OpenAI Model & Token Costs Comparison](https://benchlm.ai/openai/api-pricing) | BenchLM.ai | 2026 |

**(7)** Levantamento analítico detalhado das taxas de tokens de entrada, saída, caching e processamento em lote para toda a linha OpenAI, cobrindo GPT-4o, GPT-4o-mini e a série o3/o1.

**(8)** Análise comparativa do custo operacional por milhão de tokens da OpenAI, destacando a disparidade de custos entre modelos ultra-leves e modelos frontier de raciocínio avançado.

---

## Key Themes Across Sources

- **Separação Drástica entre Tiers (Flash vs. Flagship)**: Modelos leves (GPT-4o-mini, Gemini 2.5/3.5 Flash-Lite, DeepSeek-Flash, GLM-5.3-Flash) custam na faixa de $0.10 a $0.30 por 1M de tokens de entrada, enquanto modelos de fronteira (Claude Opus, GPT-4o, Gemini Pro/Argon) variam de $2.00 a $10.00 por 1M de tokens de entrada — uma diferença de 10x a 50x.
- **Assimetria Input vs. Output**: Em todos os provedores, tokens de saída custam entre 3x e 5x mais do que tokens de entrada devido à maior exigência computacional de geração autoregressiva.
- **Alavancas de Otimização (Caching & Batch)**: Todos os principais players agora oferecem Prompt Caching (descontos de 50% a 95% para prompts de contexto reutilizados) e Batch APIs (desconto fixo de 50% para tarefas não urgentes processadas em até 24h).
- **Competitividade dos Modelos Open-Weight / Provedores Chineses**: DeepSeek e Z.ai oferecem valores extremamente agressivos, com DeepSeek custando a partir de $0.15/$0.60 por 1M de tokens em horários fora de pico e Z.ai oferecendo GLM-5.3-Flash a $0.15/$0.50.
- **Conveniência vs. Taxa do OpenRouter**: O OpenRouter centraliza mais de 500 modelos sob uma única chave e API compatível com OpenAI, cobrando uma taxa de serviço moderada (5.5% no pay-as-you-go), viabilizando testes rápidos e failover automático sem gerenciar múltiplos contratos.

---

*Research conducted on October 13, 2026.*
