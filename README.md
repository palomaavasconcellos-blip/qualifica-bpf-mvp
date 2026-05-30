# MVP Qualifica BPF | Classificação de Risco Operacional

**Discente:** Paloma  
**Instituição:** Universidade de Brasília — UnB  
**Disciplina:** Sistemas de Suporte a Decisão / Ciência de Dados  
**Professor:** Dr. Andre Luiz Marques Serrano  
**Ano:** 2026  

---

## Descrição do Problema

A Qualifica Alimentos é uma empresa de consultoria especializada em Boas Práticas de Fabricação (BPF) para o setor de alimentos. No contexto operacional atual, as consultoras realizam visitas periódicas a restaurantes e estabelecimentos alimentícios, aplicando checklists de conformidade e registrando não conformidades com seus respectivos pesos e criticidades.

O desafio central está na priorização: com dezenas de clientes ativos, diferentes frequências de visita, variações na complexidade de cada estabelecimento e histórico de não conformidades recorrentes, a liderança da Qualifica precisa identificar rapidamente quais clientes demandam atenção imediata — seja por risco sanitário elevado, seja pela necessidade de uma reunião de impacto para realinhamento do plano de ação.

Hoje esse processo é feito de forma manual, disperso em planilhas, relatórios em PDF e ferramentas como Checklist Fácil e Trello. O objetivo deste projeto é desenvolver um modelo de classificação capaz de **predizer o nível de risco operacional de cada cliente** com base em dados estruturados das visitas realizadas.

---

## Hipótese

Variáveis como nota do checklist BPF, quantidade e criticidade das não conformidades, taxa de cumprimento das visitas previstas, recorrência de problemas e desvios no tempo de permanência contêm informação suficiente para classificar automaticamente o risco operacional de um cliente em três categorias: **Baixo**, **Atenção** ou **Crítico**.

---

## Variável Alvo

`risco_operacional` — variável categórica com três classes:
- `baixo` — cliente em conformidade, visitas cumpridas, sem NC crítica recorrente
- `atencao` — cliente com sinais de degradação ou cumprimento irregular
- `critico` — cliente com risco sanitário elevado, necessidade de reunião de impacto

---

## Dataset

O dataset utilizado é **sintético**, gerado com base nas regras operacionais reais da Qualifica Alimentos, com dados fictícios que preservam a lógica de negócio sem expor informações confidenciais de clientes reais.

- **Arquivo:** `data/processed/dataset_bpf_sintetico.csv`
- **URL para carga no Colab:** disponível após upload no GitHub (ver notebook)
- **Registros:** 500 observações
- **Atributos:** 16 variáveis preditoras + 1 variável alvo

---

## Como Executar

### Google Colab (recomendado)
1. Acesse o notebook público: [link do Colab aqui após upload]
2. Clique em `Ambiente de execução > Executar tudo`
3. Nenhuma configuração adicional é necessária — os dados são carregados por URL

### Localmente
```bash
git clone https://github.com/SEU-USUARIO/qualifica-bpf-mvp.git
cd qualifica-bpf-mvp
pip install -r requirements.txt
jupyter notebook notebooks/MVP_Qualifica_BPF_Classificacao_Risco.ipynb
```

---

## Estrutura do Repositório

```
qualifica-bpf-mvp/
│
├── data/
│   └── processed/
│       └── dataset_bpf_sintetico.csv       # Dataset sintético principal
│
├── docs/
│   ├── dicionario_dados.md                  # Descrição de cada variável
│   ├── regras_negocio.md                    # Regras para geração da variável alvo
│   ├── escopo_mvp.md                        # O que entra e o que fica fora
│   └── briefing_professor.md               # Checklist dos requisitos do professor
│
├── notebooks/
│   └── MVP_Qualifica_BPF_Classificacao_Risco.ipynb   # Entrega principal
│
├── src/
│   └── gerar_dataset.py                     # Script para gerar o dataset sintético
│
├── app/                                     # Protótipo complementar (visão futura)
│   └── briefing_lovable.md
│
├── evidence/
│   └── resumo_reuniao_checklist_facil.md
│
├── outputs/
│   └── metricas_modelos.csv                 # Resultados comparativos
│
├── CLAUDE.md                                # Instruções do agente
├── README.md                                # Este arquivo
└── requirements.txt                         # Dependências Python
```

---

## Separação das Camadas do Projeto

| Camada | O que é | Status |
|---|---|---|
| **Entrega acadêmica** | Notebook Colab + dataset + README + GitHub | ✅ Prioridade máxima |
| **Protótipo complementar** | Interface web com checklist e dashboard | 🔄 Em concepção |
| **Visão futura** | Plataforma integrada com login, Supabase, relatórios e dossiê do cliente | 📋 Documentado |

---

## Modelos Treinados

| Modelo | Justificativa |
|---|---|
| Árvore de Decisão (baseline) | Interpretável, bom ponto de partida para dados estruturados |
| Random Forest | Robusto, lida bem com features correlacionadas |
| Gradient Boosting (XGBoost) | Alto desempenho em classificação tabular |

---

## Tecnologias Utilizadas

- Python 3.10+
- pandas, numpy
- scikit-learn
- matplotlib, seaborn
- Google Colab
- GitHub

---

## Contexto Operacional (Visão Futura)

A visão de longo prazo é substituir ou complementar o Checklist Fácil com uma plataforma integrada da Qualifica Alimentos, contendo:
- Checklist BPF digital por estabelecimento
- Registro de não conformidades com ação corretiva, responsável e prazo
- Dossiê histórico do cliente
- Dashboard interno para a equipe Qualifica
- Dashboard externo para o cliente (com login por perfil)
- Alertas automáticos baseados no modelo de classificação de risco

> Este projeto prova a viabilidade da camada de inteligência do sistema. A plataforma completa é documentada em `app/briefing_lovable.md`.
