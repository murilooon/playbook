# Python Data Science Tools

Nesse artigo irei descrever algumas ferramentas importantes e rotinaieras na vida de um cientista de dados. Será abordado a funcionalidade e aplicações práticas de cada uma delas. Além disso, trechos de sintaxe das ferramentas será descrito para recorrer ao artigo quando necessária a consulta.

## Sumário

* [Numpy](#numpy)
* [Pandas](#pandas)
* [Matplotlib](#matplotlib)
* [Seaborn](#seaborn)
* [Requests](#requests)
* [BeautifulSoup](#beautifulsoup)
* [SQLAlchemy](#sqlalchemy)
* [Keras](#keras)
* [OpenRefine](#openrefine)
* [Curiosidades](#curiosidades)

## Numpy

Numpy é o principal pacote para desenvolvimento de projetos utilizando ciência dos dados, em Python.

* Traz a facilidade de criação de arrays N-dimensionais, com o intuito de otimizar cálculos;
* Pode utilizar a maioria dos operadores lógicos e matemáticos presentes no Python;
* (continuar)
* (continuar)

Algumas funcionalidades importantes:

### Importar a biblioteca
	import numpy as np

### Criar um array
	np_array= np.array([1, 2, 3],
			   [4, 5, 6])

### Operações básicas
	# Soma de todos os elementos
	np_array.sum()

	# Encontra o menor valor no array
	np_array.min()

	# Encontra o maior valor no array
	np_array.max()

	# Cria um array 3x4 com 12 elementos
	np_array = np.arange(12).reshape(3, 4)
	# Os valores acima de 4 recebem True
	b_bool = np_array > 4
	# Imprime apenas os valores True
	print(np_array[b_bool])
	output: array([5, 6, 7, 8, 9, 10, 11])
	# Melhor utilizar Pandas para essa aplicação

### Importar documentos

	data = np.genfromtxt('file.csv', delimiter=',', names=True, dtype=None)

O primeiro argumento é o nome do arquivo, o segundo especifica da delimitação, o terceiro diz que tem um Header e o quarto diz que o tipo é None (qualquer um).

### Recomendações

* Utilizar arrays de apenas um tipo (int, float, string), e de preferência valores numéricos, não mesclando-os.

## Pandas

Pandas incorpora na linguagem Python um ambiente completo para análise de dados, sem a necessidade de utilizar outra liguagem específica, como R.

Algumas funcionalidades importantes:

### Importar a biblioteca
	import pandas as pd

### Importar documentos (csv, spreadsheet, json, html)..
	# Ler documentos
	file = pd.read_csv('file.csv', nrows=5) # Número de linhas q irá salvar
	file = pd.read_json('file.json', header=None) # Sem Header
	file = pd.read_excel('file.xml', sep='\t') # Separado por Tab
	file = pd.read_html('file.html', na_values='Nothing') # NA/NaN valores viram Nothing

	# Escrever em documentos
	file = pd.to_csv('file.csv')
	file = pd.to_json('file.json')
	file = pd.to_excel('file.xml')
	file = pd.to_html('file.html')

## Matplotlib

### Importar a biblioteca
	import matplotlib.pyplot as plt

### Plotar um histograma DataFrame
	pd.DataFrame.hist(data) # data.hist() -> outra formar
	# Nome do eixo X
	plt.xlabel('Age (years)')
	# Nome do eixo Y
	plt.ylabel('count')
	plt.show()

## Seaborn

## Requests

Disponibiliza uma interface para busca de dados na internet

	import requests
	url = "https://github.com/"
	# Manda uma requisição para a url e pega a resposta
	r = requests.get(url)
	# Retorna para 'text' o html da página
	text = r.text

## BeautifulSoup

Analiza e extrai estruturas de dados do HTML

	# Importar bibliotecas
	import requests
	from bs4 import BeautifulSoup

	# Manda uma requisição para a url e pega a resposta
	r = requests.get('https://www.python.org/~guido/')

	# Extrai o HTML
	html_doc = r.text

	# Cria um objeto BeautifulSoup do HTML
	soup = BeautifulSoup(html_doc)

	# Imprime o título da página
	print(soup.title)

	# Encontra todas as tags 'a'
	a_tags = soup.find_all('a')

	# Imprime as URLs das tags 'a'
	for link in a_tags:
	    print(link.get('href'))

## SQLAlchemy

É uma ferramenta SQL open source para Python que disponibiliza o diálogo entre a linguagem e o banco de dados SQL. Funciona com diversos sistemas relacionais, como SQLite, PostgreSQL e MySQL.

	# Importar a biblioteca
	from sqlalchemy import create_engine 
	import pandas as pd

	# Criar uma conexão com o banco SQLite
	engine = create_engine('sqlite:///Northwind.sqlite')

	# 'With as' é útil para não necessitar fechar a conexão após o uso do banco
	with engine.connect() as con:
			# Atribuir a execução do comando para 'rs'
			rs = con.execute('SELECT OrderID, OrderDate, ShipName FROM Orders')
			# Criar tabela com todos os dados até a linha 5
			df = pd.DataFrame(rs.fetchmany(size=5))
			# Atribuir nome as colunas da tabela
			df.columns = rs.keys()
			
	# OU
		
	# Com uma linha você pode fazer a mesma coisa
	df = pd.read_sql_query('SELECT OrderID, OrderDate, ShipName FROM Orders', engine)

## Keras

[Keras](https://keras.io/) é uma biblioteca open source de redes neurais escrita em Python.

## OpenRefine

* [OpenRefine](http://openrefine.org/) é uma ferramenta desktop open-source criada pela Google para limpeza e análise de dados. Com ela, pode-se corrigir erros de tabelas, arquivos .csv e visualizar padrões em gráficos. Uma alternativa válida para pequenos projetos e ou pessoais.

## One Hot Encode

* Machine learning não trabalha com dados categóricos diretamente, eles precisam ser convertidos para números. Isso se aplica quando se está trabalhando com um problema de classificação e planeja usar estratégias de Deep Leaning como Long Short-Term Memory. Para conversão desses dados existe uma técnica chamada [One Hot Encoding](https://machinelearningmastery.com/how-to-one-hot-encode-sequence-data-in-python/), que é a representação do dado como um vetor binario de 0's e apenas um 1.

* Com a biblioteca Scikit-Learn e Numpy da pra transformar o texto em One Hot Encoding facilmente.

Exemplo:

	from numpy import array
	from numpy import argmax
	from sklearn.preprocessing import LabelEncoder
	from sklearn.preprocessing import OneHotEncoder

	# define example
	data = ['cold', 'cold', 'warm', 'cold', 'hot', 'hot', 'warm', 'cold', 'warm', 'hot']
	values = array(data)
	print(values)

	# integer encode
	label_encoder = LabelEncoder()
	integer_encoded = label_encoder.fit_transform(values)
	print(integer_encoded)

	# binary encode
	onehot_encoder = OneHotEncoder(sparse=False)
	integer_encoded = integer_encoded.reshape(len(integer_encoded), 1)
	onehot_encoded = onehot_encoder.fit_transform(integer_encoded)
	print(onehot_encoded)

	# invert first example
	inverted = label_encoder.inverse_transform([argmax(onehot_encoded[0, :])])
	print(inverted)

[OneHotEncoder scikit-learn API documentation](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html)

[LabelEncoder scikit-learn API documentation](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html)

* Como alternativa, a lib Keras tem disponível uma função chamada [to_categorical()](https://keras.io/utils/#to_categorical) que faz One Hot Encode em inteiros.

Exemplo:

	from numpy import array
	from numpy import argmax
	from keras.utils import to_categorical

	# define example
	data = [1, 3, 2, 0, 3, 2, 2, 1, 0, 1]
	data = array(data)
	print(data)

	# one hot encode
	encoded = to_categorical(data)
	print(encoded)

	# invert encoding
	inverted = argmax(encoded[0])
	print(inverted)

## Links Úteis

* [What is one-hot encoding and when is it used in data science?](https://www.quora.com/What-is-one-hot-encoding-and-when-is-it-used-in-data-science)
* [Data Preparation for Gradient Boosting with XGBoost in Python](https://machinelearningmastery.com/data-preparation-gradient-boosting-xgboost-python/)
* [Multi-Class Classification Tutorial with the Keras Deep Learning Library](https://machinelearningmastery.com/multi-class-classification-tutorial-keras-deep-learning-library/)