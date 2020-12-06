# Projeto-NetworkX
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
![Exemplo 1](https://github.com/FordPrefect12/Projeto---NetworkX.github.io/blob/main/Exemplo%201.png)

