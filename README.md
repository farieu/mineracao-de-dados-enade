# Mapeamento de Desempenho de Concluintes de Computação no Nordeste

> **Educational Data Mining (EDM) • K‑Means Clustering • ENADE & Censo Superior • Nordeste/Brasil**

[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=19867014)

---

## Visão Geral

Este projeto aplica **Mineração de Dados Educacionais (EDM)** para investigar o desempenho de concluintes dos cursos de Computação na região Nordeste do Brasil (ENADE 2014‑2017‑2021). Utilizamos **K‑Means** para identificar perfis latentes a partir de variáveis socioeconômicas, institucionais e acadêmicas, seguindo o processo **KDD**. Os insights gerados podem subsidiar políticas públicas de inclusão e qualidade no ensino superior.

<div align="center">
<img src="docs/banner_edm.png" width="80%" alt="Banner K-Means"/>
</div>

## Objetivos

* 🔍 **Clusterizar** os concluintes em perfis socioeconômicos/acadêmicos.
* 📊 **Comparar** evolução de desempenho entre 2014, 2017 e 2021.
* 🗺️ **Mapear** diferenças por curso e UF no Nordeste.
* 🎯 **Gerar** indicadores que orientem ações de melhorias públicas e apoio estudantil.

## Estrutura do Repositório

```text
├── code/
│   ├── 1. Notebooks EDA/                          # Análise exploratória dos dados brutos
│   │   ├── [EDM] Exploração do ENADE (filtrado).ipynb      # Gráficos e estatísticas por UF, curso, etc.
│   │   ├── [EDM] Extração_Censo_Analise_Exploratoria.ipynb # Tratamento do Censo e estatísticas descritivas
│   │   └── [EDM] Comparação por curso e ano.ipynb          # Análise comparativa entre anos (2014-2021)
│   │
│   ├── 2. Notebooks Metodologia/                 # Etapas de pré-processamento e definição de K
│   │   ├── [ELBOW] Codificação e WCSS.ipynb             # One-hot, normalização e método do cotovelo
│   │   ├── [EDM] Merge ENADE Censo Final.ipynb          # Junta datasets e seleciona variáveis
│   │   └── [EDM] Verificação Pós-Processamento.ipynb    # Checagem de dados normalizados
│   │
│   └── 5. K-Means/
│       ├── [EDM] K-Means.ipynb                          # Clusterização final com visualizações e geração de gráficos detalhados por cluster

├── data/
│   ├── 1. Listagem de Cursos/
│   │   ├── censo_cursos_2014.csv
│   │   ├── censo_cursos_2017.csv
│   │   └── censo_cursos_2021.csv
│   │
│   ├── 2. ENADE/
│   │   ├── enade_2014_filtrado.csv
│   │   ├── enade_2017_filtrado.csv
│   │   └── enade_2021_filtrado.csv
│   │
│   ├── 3. Normalizados/
│   │   ├── enade_2014_normalizado.csv
│   │   ├── enade_2017_normalizado.csv
│   │   └── enade_2021_normalizado.csv
│   │
│   └── 4. Versão Final para o K-MEANS/
│       ├── enade_normalizado.csv                   # Dataset final com todos os anos consolidados

├── docs/
│   ├── pandas profiling/
│   ├── microdados2014_profiling.html              # Profiling para entender melhor os dados
│   ├── ...
│   │
│   ├── CENSO - Atributos.pdf
│   ├── ENADE - Atributos.pdf
│   ├── Observações do Conjunto de Dados.pdf
│   ├── banner_edm.pdf
│   └── [EDM 2025.1] Paper.pdf                      # Artigo do projeto em formato PDF

└── README.md                                       # Documentação geral do projeto
```

## Fontes de Dados

| Base                       | Ano(s)             | Link                                                                                     |
| -------------------------- | ------------------ | ---------------------------------------------------------------------------------------- |
| ENADE Microdados           | 2014 • 2017 • 2021 | [INEP](https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/microdados/enade) |

> **Nota:** as bases foram processadas para atender LGPD; detalhes completos no [paper](docs/EDM_Paper.pdf).

## Metodologia

1. **Seleção & Limpeza**

   * Filtragem por códigos de curso de TI (Tabela 2 do paper).
   * Remoção de registros inconsistentes ou incompletos.
2. **Transformação**

   * Mapeamento textual → One‑Hot Encoding (\~110 atributos).
   * Normalização *Z‑score* de idade & nota geral.
3. **Definição de *k***

   * **Método do Cotovelo** (SSE) apontou *k = 3*.
4. **K‑Means**

   * Implementação via `scikit‑learn` (k‑means++).
   * 300 máx. iterações, 20 inicializações, `random_state=42`.
5. **Avaliação & Visualização**

   * Gráficos por curso, UF, renda, ano.
   * Interpretação dos clusters segundo variáveis chave.

## Como Reproduzir os Resultados

1. **Download dos Dados**
   Coloque os microdados originais em `data/` ou rode `code/1. Notebooks EDA/[EDM] Extração do ENADE.ipynb` para baixá‑los automaticamente.
2. **Pré‑processamento**
   Execute sequencialmente os notebooks em `code/2. Notebooks Metodologia`.
3. **Clustering**
   Rode `code/5. K-Means/[EDM] K-Means.ipynb` para gerar os clusters.
4. **Visualização**
   Os gráficos finais são salvos em `docs/figures/`.

> Você pode **abrir diretamente no GitHub Codespaces** através do botão no topo do README.

## Contribuidores

| Aluno                                   |  Contato                                                      |
| --------------------------------------- | ------------------------------------------------------------- |
| **Caio César Farias da Silva**          | [caio.fsilva@ufrpe.br](mailto:caio.fsilva@ufrpe.br)           |
| **Tarcísio Barbosa da Costa**           | [tarcisio.bcosta@ufrpe.br](mailto:tarcisio.bcosta@ufrpe.br)   |
| **Victor Henrique dos Santos Oliveira** | [victor.henriqued@ufrpe.br](mailto:victor.henriqued@ufrpe.br) |

> Sinta‑se à vontade para abrir *issues* ou *pull requests* 💙

## Referências

* Murphy, K. *Machine Learning: A Probabilistic Perspective*. MIT Press, 2012.
* Bailey, K. D. *Cluster Analysis*. Sociological Methodology, 1975.
* Aldefender, M. S.; Blashfield, R. K. *Cluster Analysis*. Sage, 1984.
* (Demais referências no [paper](docs/EDM_Paper.pdf))

---

<p align="center"><em>
Universidade Federal Rural de Pernambuco — Departamento de Estatística & Informática
</em></p>