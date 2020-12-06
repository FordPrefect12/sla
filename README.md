# Projeto-NetworkX
É um pacote do python para criação, manipulação e estudo da estrutura, dinâmica e funções complexas de rede. Em python, por definição, grafos são uma coleção de nodes e edges (par de nodes relacionados entre si). Neste pacote os nodes podem ser qualquer hashable object, como uma string, uma imagem, um node customizado ou até outro grafo.

## Grafos:
De certo modo grafos são uma estrutura que equivale a um conjunto de objetos nos quais alguns pares de objetos estão, em certo sentido, "relacionados". Em python usamos o conceito de centralidade, sendo a medida de importância de um vértice em um grafo. Existem diferentes tipos de medidas de centralidade de um vértice num grafo que determinam a importância relativa, que permitem, por exemplo, estimar o quanto uma pessoa é influente dentro de uma rede social, o quão é importante uma sala dentro de um edifício e como é bem utilizada uma estrada dentro de uma rede urbana. O conceito de grafos foi construído pelo matemático Euler, quando ele tentava solucionar  o problema das sete pontes de Königsberg.

Agora vamos para o collab apresentar alguns comandos para facilitar o entendimento e depois mostrar e construir alguns grafos para melhor visualização.

# Exemplo 1:
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
