# Ciência de Dados: faltas em consultas médicas (No-Show)

Projeto completo de ciência de dados, da disciplina de Ciência de Dados da UFAL (2026.1), sobre a base pública [Medical Appointment No Shows](https://www.kaggle.com/datasets/joniarroba/noshowappointments). A base tem cerca de **110 mil agendamentos** do sistema público de saúde de Vitória (ES).

**Pergunta central:** quais fatores levam um paciente a faltar à consulta, e é possível prever esse risco para agir antes (por exemplo, com um lembrete ativo)?

## 📓 Notebooks

| Notebook | Conteúdo | Abrir |
|---|---|---|
| `Lista_1_Antonio_Guilherme.ipynb` | Diagnóstico automatizado, auditoria de qualidade, limpeza reprodutível, EDA orientada ao problema, medição de associação, engenharia de atributos, pipeline com `ColumnTransformer` e k-NN em vários cenários comparado à Random Forest | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/guilhermek32/ListaDataScience-2026.1/blob/main/Lista_1_Antonio_Guilherme.ipynb) |
| `Lista_2_Antonio_Guilherme.ipynb` | Naive Bayes (Multinomial e Bernoulli), regressão com análise de resíduos, árvore de decisão interpretável, comparação formal entre modelos, séries temporais, análise de redes, meta-aprendizagem e visualização para tomada de decisão | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/guilhermek32/ListaDataScience-2026.1/blob/main/Lista_2_Antonio_Guilherme.ipynb) |

## 🔍 Principais achados

- **O tempo de espera é o principal fator.** As variáveis mais importantes na árvore de decisão foram `wait_days` (dias entre agendamento e consulta), idade, horário agendado e recebimento de SMS.
- **A árvore de decisão foi o modelo mais defensável.** Teve o melhor F1 entre Naive Bayes, regressão logística e árvore, e gera regras que um atendente consegue aplicar (por exemplo: espera longa e paciente jovem significa risco alto, então vale um lembrete ativo).
- **Naive Bayes não serve para esta base.** A independência condicional é violada (Idade × Hipertensão tem correlação de cerca de 0,50, e o V de Cramér mostra associação entre as categorias).
- **A regressão linear tem limites aqui.** O teste de Breusch-Pagan rejeitou a homocedasticidade e os resíduos têm formato de funil.
- **Avaliação crítica:** a modelagem como rede (bairro × dia da semana) foi testada e descartada como metodologicamente fraca para este problema.

## 🧰 Técnicas e ferramentas

`pandas` · `scikit-learn` (Pipeline, ColumnTransformer, StratifiedKFold, TimeSeriesSplit) · `category_encoders` (Target Encoding) · `statsmodels` · `scipy` · `NetworkX` · `seaborn` · `matplotlib`

## ▶️ Como executar

1. Abra um dos notebooks no Colab pelos botões acima, ou clone o repositório e use Jupyter.
2. A base `Medical Appointment No Shows.csv` já está no repositório.
3. Algumas etapas (k-NN com busca de hiperparâmetros) podem levar mais de 5 minutos. As saídas já estão salvas nos notebooks.

---
Autor: **Antonio Guilherme da Silva**, Ciência da Computação, UFAL
