# NetworkX
É um pacote do python para criação, manipulação e estudo da estrutura, dinâmica e funções complexas de rede. Em python, por definição, grafos são uma coleção de nodes e edges (par de nodes relacionados entre si). Neste pacote os nodes podem ser qualquer hashable object, como uma string, uma imagem, um node customizado ou até outro grafo.

## Grafos:
De certo modo grafos são uma estrutura que equivale a um conjunto de objetos nos quais alguns pares de objetos estão, em certo sentido, "relacionados". Em python usamos o conceito de centralidade, sendo a medida de importância de um vértice em um grafo. Existem diferentes tipos de medidas de centralidade de um vértice num grafo que determinam a importância relativa, que permitem, por exemplo, estimar o quanto uma pessoa é influente dentro de uma rede social, o quão é importante uma sala dentro de um edifício e como é bem utilizada uma estrada dentro de uma rede urbana. O conceito de grafos foi construído pelo matemático Euler, quando ele tentava solucionar  o problema das sete pontes de Königsberg.

Agora vamos para o collab apresentar alguns comandos para facilitar o entendimento e depois mostrar e construir alguns grafos para melhor visualização.



## Exemplo 1:
- Os vértices de um grafo são os nodes
- A relação entre os nodes são os edges

```python
import networkx as nx
G = nx.Graph()
G.add_node('N1')
G.add_node('N2')
G.add_node('N3')
G.add_edge('N1', 'N2') # Adicionar uma relação entre o node 'N1' e 'N2'
G.add_edge('N3', 'N4') # Adicionar uma relação entre o node 'N3' e um node que até agora ainda não existia
nx.draw(G, with_labels=1)
```

![image](https://github.com/FordPrefect12/NetworkX.github.io/blob/main/Exemplo%201.png)


```python
print(nx.info(G)) # Alternativa para não precisar usar um comando para cada informação presente em um grafo
```
    Name: 
    Type: Graph
    Number of nodes: 4
    Number of edges: 2
    Average degree:   1.0000

## Exemplo 2:
- Criar um grafo com um número de nodes pré-determinado e conectados entre si, em ordem crescente
```python
H = nx.path_graph(10)
nx.draw(H, with_labels=1)
```
![exemplo 2](https://github.com/FordPrefect12/Projeto---NetworkX.github.io/blob/main/Exemplo%202.png)

## Exemplo 3:
- Criando um grafo com um número de nodes pré-determinado e conectados entre si
```python
Z = nx.complete_graph(10)
nx.draw(Z, with_labels=1)
```
![Exemplo 3](https://github.com/FordPrefect12/Projeto---NetworkX.github.io/blob/main/Exemplo%203.png)

```python
print(nx.info(Z))
```
    Name: 
    Type: Graph
    Number of nodes: 10
    Number of edges: 45
    Average degree:   9.0000
    
## Exemplo 4:
- Gerando um grafo com um número de nodes pré-determinado com uma probabilidade de relação de 50%
```python
Y = nx.gnp_random_graph(10, 0.5)
nx.draw(Y, with_labels=True)
```
![Exemplo 4](https://github.com/FordPrefect12/Projeto---NetworkX.github.io/blob/main/Exemplo%204.png)

```python
print(nx.info(Y))
```
    Name: 
    Type: Graph
    Number of nodes: 10
    Number of edges: 22
    Average degree:   4.4000

```python
10*9
```
    90
    
```python
90/2 # número de edges de um grafo completo com 10 nodes
```
    45.0

```python
45/2 # número de edges de um grafo com probabilidade 0.5 com 10 nodes
```
    22.5
    
```python
45/2 # número de edges de um grafo com probabilidade 0.5 com 10 nodes
```

```python
total_of_edges=[]
for i in range(100000): #Criando x grafos aleatórios para provar que o número de edges tende a 22.5
  Y = nx.gnp_random_graph(10, 0.5)
  m=Y.size()
  total_of_edges.append(m)
print(total_of_edges)
```
    [22, 25, 20, 18, 20, 19, 21, 28, 28, 18, 23, 25, 17, 27, 23, 24, 26, (...), 21, 20]

```python
import numpy as np
print(np.average(total_of_edges))
```
    22.4839
    
## Exemplos aplicados:
### Tentativa 1 (Excel):
```python
import networkx as nx
import pandas as pd
dfs = pd.read_excel("Twitter.xlsx", sheet_name = ["Elementos", "Perfil", "Conexoes", "Conexoes2"])
node_data = dfs["Elementos"]
edge_data = dfs["Perfil"]
edge_data1 = dfs["Conexoes"]
edge_data2 = dfs["Conexoes2"]

A = nx.from_pandas_edgelist(edge_data, source = 'Perfil1', target = 'Seguindo1')
B = nx.from_pandas_edgelist(edge_data1, source = 'Seguindo', target = 'Recomendado')
C = nx.from_pandas_edgelist(edge_data2, source = 'Recomendado1', target = 'Recomendado2')
U = nx.compose(A, B)
Z = nx.compose(U,C)
```

```python
nx.draw_shell(Z, with_labels=True)
```
![Tentativa 1](https://github.com/FordPrefect12/Projeto---NetworkX.github.io/blob/main/Tentativa%201.png)

```python
print(nx.info(Z))
```
    Name: 
    Type: Graph
    Number of nodes: 12
    Number of edges: 17
    Average degree:   2.8333

```python
Z.add_node('Renan', weight= 0.4)
Z.add_node('Leonardo', weight= 0.6)
Z.add_node('Felipe', weight= 0.2)
Z.add_node('Bruna', weight= 0.1)
Z.add_node('Fabiano', weight= 0.4)
Z.add_node('Roberto', weight= 0.1)
Z.add_node('Rodrigo', weight= 0)
Z.add_node('Ana', weight= 0)
Z.add_node('Alice', weight= 0)
Z.add_node('Arthur', weight= 0)
Z.add_node('Pedro', weight= 0)
print(Z.nodes.data())
```
    [('Eduardo', {}), ('Arthur', {'weight': 0}), ('Rodrigo', {'weight': 0}), ('Ana', {'weight': 0}), ('Alice', {'weight': 0}), ('Pedro', {'weight': 0}), ('Leonardo', {'weight': 0.6}), ('Renan', {'weight': 0.4}), ('Fabiano', {'weight': 0.4}), ('Felipe', {'weight': 0.2}), ('Roberto', {'weight': 0.1}), ('Bruna', {'weight': 0.1})]

### Tentativa 2:

```python
H = nx.Graph()
H.add_nodes_from(['Eduardo', 'Arthur','Rodrigo', 'Ana', 'Alice', 'Pedro', 'Renan', 'Leonardo', 'Felipe', 'Bruna', 'Fabiano'])
H.add_edge('Eduardo', 'Arthur')
H.add_edge('Eduardo','Rodrigo')
H.add_edge('Eduardo','Ana')
H.add_edge('Eduardo','Alice')
H.add_edge('Eduardo','Pedro')
H.add_edge('Arthur','Leonardo')
H.add_edge('Arthur','Pedro')
H.add_edge('Arthur','Rodrigo')
H.add_edge('Arthur','Renan')
H.add_edge('Rodrigo','Leonardo')
H.add_edge('Ana','Leonardo')
H.add_edge('Ana','Fabiano')
H.add_edge('Ana','Felipe')
H.add_edge('Alice','Fabiano')
H.add_edge('Pedro','Renan')
H.add_edge('Felipe','Roberto')
H.add_edge('Felipe','Bruna')

H.add_node('Renan', weight= 0.4)
H.add_node('Leonardo', weight= 0.6)
H.add_node('Felipe', weight= 0.2)
H.add_node('Bruna', weight= 0.1)
H.add_node('Fabiano', weight= 0.4)
H.add_node('Roberto', weight= 0.1)
H.add_node('Rodrigo', weight= 0)
H.add_node('Ana', weight= 0)
H.add_node('Alice', weight= 0)
H.add_node('Arthur', weight= 0)
H.add_node('Pedro', weight= 0)
```

```python
nx.draw(H, with_labels=True)
```
![Tentativa 2](https://github.com/FordPrefect12/Projeto---NetworkX.github.io/blob/main/Tentativa%202.png)

```python
print(nx.info(H))
```
    Name: 
    Type: Graph
    Number of nodes: 12
    Number of edges: 17
    Average degree:   2.8333

```python
print(H.nodes.data())
```
    [('Eduardo', {}), ('Arthur', {'weight': 0}), ('Rodrigo', {'weight': 0}), ('Ana', {'weight': 0}), ('Alice', {'weight': 0}), ('Pedro', {'weight': 0}), ('Renan', {'weight': 0.4}), ('Leonardo', {'weight': 0.6}), ('Felipe', {'weight': 0.2}), ('Bruna', {'weight': 0.1}), ('Fabiano', {'weight': 0.4}), ('Roberto', {'weight': 0.1})]

## Exemplo Aplicado:
Vamos importar nosso dataset para manipulação dos dados
```python
link = ("https://github.com/dnllvrvz/Social-Network-Dataset/blob/master/Social%20Network%20Dataset.xlsx?raw=true")
```

importando o pandas
```python
import pandas as pd
```

```python
pd.read_excel(link)
```
    	Label	Type	School (ID)	Answered the form
        0	S-c1b610	Student	27	Yes
        1	S-4985b3	Student	25	Yes
        2	S-376418	Student	67	Yes
        3	S-d00f38	Student	24	Yes
        4	S-e538e3	Student	30	Yes
        ...	...	...	...	...
        1188	S-64b594	Student	25	No
        1189	S-42ff75	Student	49	No
        1190	S-87c031	Student	4	No
        1191	S-cd9523	Student	12	No
        1192	S-1a36bb	Student	58	No
        1193 rows × 4 columns

DICA MESTRE: O python mostra um cardapio de acordo com a função pedida
```python
?pd.read_excel
```
    Signature:
    pd.read_excel(
    io,
    sheet_name=0,
    header=0,
    names=None,
    index_col=None,
    usecols=None,
    squeeze=False,
    dtype=None,
    engine=None,
    converters=None,
    true_values=None,
    false_values=None,
    skiprows=None,
    nrows=None,
    na_values=None,
    keep_default_na=True,
    na_filter=True,
    verbose=False,
    parse_dates=False,
    date_parser=None,
    thousands=None,
    comment=None,
    skipfooter=0,
    convert_float=True,
    mangle_dupe_cols=True,
    )
    (...)
    >>> pd.read_excel('tmp.xlsx', index_col=0, comment='#')  # doctest: +SKIP
      Name  Value
    0  string1    1.0
    1  string2    2.0
    2     None    NaN
    File:      c:\users\rodri\appdata\local\programs\python\python38-32\lib\site-packages\pandas\io\excel\_base.py
    Type:      function

```python
data = pd.read_excel(link, sheet_name=['Elements','Connections'])
```

```python
node_data = data['Elements']
edge_data = data['Connections']
```

```python
edge_data.head(3)
```
    	From	To	Type	Weight	When
        0	S-c1b610	S-7d9053	Other	1.0	2012.0
        1	S-4985b3	S-e7dad4	School	1.0	2015.0
        2	S-376418	S-ab3070	School	1.0	2012.0

```python
import networkx as nx
```

```python
graph = nx.from_pandas_edgeliste(dge_data, source='From', target='To', edge_attr=['Weight','When'])
```

```python
import matplotlib as plt
```

```python
nx.draw(graph, node_size=10, node_color='C1')
```
![Exemplo Rodrigo](https://github.com/FordPrefect12/Projeto---NetworkX.github.io/blob/main/Exemplo%20Rodrigo.png)

```python
?nx.draw
```
    Signature: nx.draw(G, pos=None, ax=None, **kwds)
    Docstring:
    Draw the graph G with Matplotlib.

    Draw the graph as a simple representation with no node
    labels or edge labels and using the full Matplotlib figure area
    and no axis labels by default.  See draw_networkx() for more
    full-featured drawing that allows title, axis labels etc.

    Parameters
    ----------
    G : graph
       A networkx graph

    pos : dictionary, optional
       A dictionary with nodes as keys and positions as values.
       If not specified a spring layout positioning will be computed.
       See :py:mod:`networkx.drawing.layout` for functions that
       compute node positions.

    ax : Matplotlib Axes object, optional
       Draw the graph in specified Matplotlib axes.

    kwds : optional keywords
       See networkx.draw_networkx() for a description of optional keywords.

    Examples
    --------
    >>> G = nx.dodecahedral_graph()
    >>> nx.draw(G)
    >>> nx.draw(G, pos=nx.spring_layout(G))  # use spring layout

    See Also
    --------
    draw_networkx()
    draw_networkx_nodes()
    draw_networkx_edges()
    draw_networkx_labels()
    draw_networkx_edge_labels()

    Notes
    -----
    This function has the same name as pylab.draw and pyplot.draw
    so beware when using `from networkx import *`

    since you might overwrite the pylab.draw function.

    With pyplot use

    >>> import matplotlib.pyplot as plt
    >>> G = nx.dodecahedral_graph()
    >>> nx.draw(G)  # networkx draw()
    >>> plt.draw()  # pyplot draw()

    Also see the NetworkX drawing examples at
    https://networkx.github.io/documentation/latest/auto_examples/index.html
    File:      c:\users\rodri\appdata\local\programs\python\python38-32\lib\site-packages\networkx\drawing\nx_pylab.py
    Type:      function
