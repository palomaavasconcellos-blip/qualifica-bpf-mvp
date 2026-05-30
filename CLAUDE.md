# CLAUDE.md — Instruções do Agente

## Contexto do Projeto

Este projeto é um MVP acadêmico da UnB com aplicação real na Qualifica Alimentos.
A visão final é uma plataforma integrada de BPF para substituir ou complementar o Checklist Fácil,
com checklist digital, relatórios de visita, dossiê do cliente, dashboard interno,
dashboard do cliente e alertas operacionais baseados em IA.

## Objetivo Acadêmico (PRIORIDADE MÁXIMA)

Construir um notebook público no Google Colab, usando Python, para resolver um problema de
classificação de risco operacional. O notebook deve:
- Carregar dataset por URL do GitHub
- Preparar os dados (encoding, normalização, feature selection)
- Separar treino e teste
- Treinar pelo menos dois modelos (baseline + principal)
- Comparar resultados com métricas adequadas
- Gerar gráficos (matriz de confusão, feature importance)
- Documentar cada etapa em células de texto com linguagem acadêmica
- Rodar do início ao fim sem erro

## Objetivo do Protótipo (COMPLEMENTAR)

Demonstrar como o sistema poderia funcionar com:
- Login por perfis (admin, líder, consultora, cliente)
- Checklist BPF digital
- Relatório de visita e registro de não conformidade
- Dashboard interno e dashboard do cliente

## Restrições Absolutas

- Não usar dados reais sensíveis (nomes de clientes, CNPJ, e-mails)
- Não incluir nomes de consultoras reais
- Usar apenas dataset sintético ou anonimizado
- Não subir planilhas operacionais reais no GitHub
- Priorizar clareza, simplicidade e execução sem erros

## Variável Alvo

`risco_operacional` com três classes: baixo, atencao, critico

## Regras para a Variável Alvo

**Crítico** se qualquer condição:
- nota_checklist < 60
- qtd_nc_peso_3 >= 2
- qtd_nc_recorrentes >= 3
- taxa_cumprimento_visitas < 0.60

**Atenção** se qualquer condição (e não for Crítico):
- nota_checklist entre 60 e 84
- qtd_nc_peso_2 >= 3
- taxa_cumprimento_visitas entre 0.60 e 0.85
- desvio_tempo < -30

**Baixo** — demais casos

## Comandos Úteis

```bash
# Gerar dataset
python src/gerar_dataset.py

# Instalar dependências
pip install -r requirements.txt

# Rodar notebook localmente
jupyter notebook notebooks/MVP_Qualifica_BPF_Classificacao_Risco.ipynb
```

## Tarefas Prioritárias (em ordem)

1. [x] Criar estrutura do repositório
2. [x] Criar README.md
3. [x] Criar dataset sintético CSV
4. [ ] Criar notebook completo no padrão do professor
5. [ ] Subir tudo no GitHub
6. [ ] Compartilhar notebook no Colab como público
7. [ ] Criar protótipo visual (Lovable/Supabase) — opcional para disciplina
