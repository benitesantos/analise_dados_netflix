
 
<img src = 'https://assets.turbologo.com/blog/pt/2019/08/19133745/netflix-new-logo.png' width = '210' height= '140' >

# Análise de dados exploratória Netflix
 Breve analise exploratória dos dados Top 10
 vistos na Netflix.

  ## Requisitos:
 - Ter o jupyter notebook instalado.
 - Ter o arquivo netflix daily  top 10.csv nas mesma pasta do arquivo analise_exploratoria_netflix.ipynb

## Pacotes instalados:
- Pandas
```bash
pip install pandas
```

## Processo das ferramentas que foram usadas:

Código que importa a tabela em csv e trás  para o python.

``` python
base = pd.read_csv('netflix daily top 10.csv')
```
Visualiza as primeiras 5 linhas da tabela.

```python
base.head()
```
Visualiza as ultimas 5 linhas da tabela.

```pyhton
base.tail()
```
Mostra a quantidade de linhas e colunas da tabela.

``` python
base.shape
```

Visualiza o inicio do periodo.

``` python
inicio = pd.to_datetime(base['As of']).dt.date.min()
print(inicio)
```

Visualiza o fim do periodo.

```python

fim = pd.to_datetime(base['As of']).dt.date.max()
print(fim)
```

Visualiza o tipo dos dados na tabela e valores nulos.

``` python
base.info()
```

Visualiza os tipos de dados na tabela.

``` python
base.dtypes
```
Visualiza se tem algum valor nulo na tabela.

``` python
base.isnull().sum()
```

Código que conta as linhas de uma coluna na tabela.

``` python
base['Netflix Exclusive'].value_counts()
```
Mostra um resumo estatístico da tabela.

``` python
base.describe()
```
Visualiza os dados em forma de gráfico. para ter outra compreensão do todo nos dados.

``` python
base.plot(kind='box',figsize=(10,6),subplots=True)
```
Vizualiza os dados filtrando por dias que foram maiores ou iguais a 100.

``` python
base[base['Days In Top 10']>= 100]
```

Importa os dados filtrados em uma planilha excel.
``` python
base_excel = base[base['Days In Top 10']>= 100]
base_excel.to_excel('Verificar.xlsx')
```

Mostra as series mais vistas na netflix

``` python
base.Title.value_counts()
```

Mostra em forma de um gráfico de barras  o tipo de series na netflix.

``` python
base.Type.value_counts().plot(kind='bar')
```
Mostra um histograma do número de vezes que foram assistidas as series.

``` python
base['Viewership Score'].hist()
```

Mostra a série que foi mais assitida. 

``` python
base[base['Viewership Score']== base['Viewership Score'].max()]
```
## Aprendizagem

- Conhecer mais os metodos que tem a ferramenta pandas, para a visualização dos dados. 