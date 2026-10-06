# eda_projeto_ia — Análise Exploratória de Dados: Video Game Sales

Projeto #1 (1ª etapa) de **Análise Exploratória de Dados (EDA)** sobre a base [Video Game Sales](https://www.kaggle.com/datasets/gregorut/videogamesales), do Kaggle.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SEU_USUARIO/eda_projeto_ia/blob/main/eda_projeto_ia.ipynb)

## Objetivo

Explorar, limpar e entender uma base real de dados: como ela está organizada, quais inconsistências possui e como suas variáveis se relacionam. A pergunta que guia o projeto é: **o que faz um jogo vender bem — o gênero, a plataforma, a época ou a região?**

## Sobre a base

| Item | Detalhe |
|---|---|
| Fonte | Kaggle — `gregorut/videogamesales` (arquivo `vgsales.csv`) |
| Registros | 16.598 originais (16.323 após a limpeza); cada linha é um jogo em uma plataforma |
| Variáveis | 11 originais (`Rank`, `Name`, `Platform`, `Year`, `Genre`, `Publisher`, `NA_Sales`, `EU_Sales`, `JP_Sales`, `Other_Sales`, `Global_Sales`) |
| Contínuas | Vendas por região e global (em milhões de unidades) |
| Discretas | `Name`, `Platform`, `Genre`, `Publisher`, `Year` (`Rank` é só identificador) |
| Período | 1980 a 2016 |

## Estrutura do repositório

```
eda_projeto_ia/
├── eda_projeto_ia.ipynb   # notebook com todas as análises, já executado
├── vgsales.csv            # base de dados
└── README.md
```

## Estrutura do notebook

O notebook segue o template da disciplina:

1. **Base escolhida e interesse**
2. **Descrição do conjunto de dados** e classificação das variáveis (contínua ou discreta)
3. **Avaliação descritiva e pré-processamento**
4. **Análises**
   - 4.1 Distribuição dos valores de cada variável
   - 4.2 Dependência entre variáveis (grupos de vendas: Nicho, Médio e Hit)
   - 4.3 Correlação entre variáveis (3 análises)
5. **Conclusões**

## Pré-processamento realizado

- `Year`: `"N/A"` convertido em nulo, 271 registros sem ano eliminados (1,6%), conversão para inteiro e filtro de 1980–2016 (4 registros fora da faixa removidos).
- `Publisher`: `"N/A"` substituído por `"Unknown"`.
- `Name`: remoção de espaços extras.
- `Platform` e `Genre`: conversão para tipo categórico.
- Vendas: checagem de valores não negativos e de coerência entre a soma das regiões e `Global_Sales`.
- Verificação de duplicados (nenhum encontrado).
- Testes com `assert` ao longo do notebook para validar a base antes e depois da limpeza.

## Principais resultados

- **Cauda longa:** cerca de 76% dos jogos vendem menos de 0,5M de unidades e apenas 12,6% chegam a 1M. O top 10% dos jogos concentra cerca de 59% das vendas totais.
- **América do Norte lidera:** responde por cerca de 49% das vendas, com correlação forte com as vendas globais (Pearson ≈ 0,94). O Japão tem comportamento próprio: 63% dos jogos têm venda zero lá.
- **Frequência não é sucesso:** `Action` é o gênero mais frequente (cerca de 20%), mas `Platform` (0,95M) e `Shooter` (0,80M) têm as maiores vendas médias por título.
- **Tempo:** os lançamentos crescem até o pico de 2009 e depois caem. A correlação entre ano e vendas é muito fraca e levemente negativa.
- **Limitações:** a base cobre apenas vendas físicas até 2016, sem downloads digitais, mobile ou jogos como serviço.

## Como executar

### Google Colab
1. Clique no botão **Open in Colab** no topo deste README.
2. Envie o `vgsales.csv` no painel de arquivos do Colab, se ele não estiver na pasta.
3. Use **Ambiente de execução → Executar tudo**.

### Localmente
```bash
git clone https://github.com/SEU_USUARIO/eda_projeto_ia.git
cd eda_projeto_ia
pip install pandas numpy matplotlib seaborn plotly jupyterlab
jupyter lab eda_projeto_ia.ipynb
```

Se o `vgsales.csv` não for encontrado na pasta, o notebook tenta baixá-lo automaticamente via `kagglehub` (`pip install kagglehub`).

## Tecnologias

Python 3, Pandas, NumPy, Matplotlib, Seaborn, Plotly e Jupyter.

## Integrantes

| Nome | Matrícula |
|---|---|
| Rebeka Natália Cavalcante dos Santos | 17242219 |
| Nayara Gabrielle Freire | 17242166 |
| André Soares Gomes dos Santos Junior | 17251365 |
| João Pedro Prysthon Paiva da Fonseca Oliveira | 17242226 |
| Natália Almeida Silva dos Santos | 17242210 |
