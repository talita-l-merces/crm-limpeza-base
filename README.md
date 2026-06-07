# Limpeza e Estruturação de Base CRM

Pipeline de limpeza, padronização e deduplicação de base de contatos para uso em CRM — transformando dados brutos de hospedagem em uma base confiável e acionável para estratégias de relacionamento.

---

## Objetivo

Estruturar uma base de leads/contatos para CRM garantindo qualidade e consistência dos dados: sem duplicatas, com canais de contato validados, campos padronizados e scoring de completude por registro.

---

## Estrutura do Projeto

```
crm_limpeza/
├── data/
│   ├── raw/
│   │   └── BASE_COMPLETA_anonimizada.csv   # Base original anonimizada (LGPD)
│   └── processed/
│       └── rd_base_limpa_dedupe.csv         # Base limpa e deduplicada para CRM
├── notebooks/
│   └── 01_exploracao_crm_final.ipynb        # Pipeline completo de limpeza
├── outputs/
│   └── grafico_completude_contatos.png
└── README.md
```

---

## O que foi feito

**Padronização estrutural**
- Normalização de nomes de colunas para `snake_case` (remoção de acentos, camelCase, separadores)
- Limpeza de texto interno: espaços invisíveis, múltiplos espaços, bordas

**Limpeza de dados de contato**
- Normalização de emails: lowercase, strip, conversão de vazios para NA
- Padronização de telefones com DDI internacional (+55)
- Validação de formato e descarte de entradas inválidas

**Deduplicação inteligente**
- Chave de contato: email preferencial, telefone como fallback
- Score de completude por registro (campos preenchidos)
- Priorização do registro mais completo em duplicatas

**Segmentação**
- Classificação de contatos por faixa de recorrência (buckets)
- Diagnóstico de completude por canal de contato

---

## Resultados

| Indicador | Valor |
|---|---|
| Registros na base original | 47.416 |
| Registros após deduplicação | 15.538 |
| Duplicatas removidas | 31.878 |
| Redução da base | 67,2% |
| Registros com email + telefone | 47.416 (100%) |
| Registros sem chave de contato | 0 |

---

## Ferramentas

- Python 3.12
- Pandas
- NumPy
- Regex (`re`, `unicodedata`)
- Matplotlib

---

## Privacidade dos Dados

Os dados originais contêm informações pessoais reais e não foram publicados neste repositório. A base disponível (`BASE_COMPLETA_anonimizada.csv`) foi gerada com nomes, emails e telefones fictícios, mantendo a estrutura e distribuições originais para fins de análise.

---

## 👩‍💻 Autora

**Talita Lima das Mercês**  
[LinkedIn](https://www.linkedin.com/in/talita-merces-a75b9b103)
