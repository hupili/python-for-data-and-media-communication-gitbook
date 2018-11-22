# Week 12: Network data

<div id="toc">
<!-- TOC -->

- [Week 12: Network data](#week-12-network-data)
    - [Graph introduction](#graph-introduction)
    - [Network example](#network-example)
    - [Get data by json](#get-data-by-json)
    - [Visualization Spring layout](#visualization-spring-layout)
    - [Color specific nodes](#color-specific-nodes)
    - [Shortest path](#shortest-path)
    - [Centrality Measures](#centrality-measures)
    - [Structure degree](#structure-degree)
    - [Clustering coefficient](#clustering-coefficient)
    - [Cliques part of the graph](#cliques-part-of-the-graph)
    - [Connected components](#connected-components)
    - [Community detection](#community-detection)
    - [Color the nodes](#color-the-nodes)

<!-- /TOC -->
</div>

## Graph introduction

>Graph theory is the study of graphs, which are mathematical structures used to model `pairwise relations` between objects. A graph in this context is made up of `nodes`, which are connected by `edges`, arcs, or lines. A graph may be `undirected`, meaning that there is no distinction between the two vertices associated with each edge. (from [wiki](https://en.wikipedia.org/wiki/Graph_theory))

There are different kind of graphs.
![Graph types 1](assets/type-of-graphs1.png)

The criteria to judge whether one graph is the same as others is not the appearance, but the relationship between different nodes.

![Graph types 2](assets/type-of-graphs2.png)

* Nodes: the fundamental unit of which graphs are formed,also called endpoint. They are connected by the edge like `A` and `B` in above picture.
* Edge：the line that connect two nodes. Each edge has two nodes to which it is attached. Edges may be directed or undirected

Try to count the edge between those circles.

   ![](assets/to-do-uncategorized-screenshots/no125.png)  
   This undirected table is symmetric. It shows that 1 and 2 has one edge. 2 and 3 is the same.   
   ![](assets/to-do-uncategorized-screenshots/no126.png)  
   The above one is directed.

* There are different ways to show the relationships.
   ![](assets/to-do-uncategorized-screenshots/no127.png)  
   ![](assets/to-do-uncategorized-screenshots/no129.png)  
   ![](assets/to-do-uncategorized-screenshots/no130.png)  
   Then we can infer the list.

## Network example

  ```
  import networkx as nx
  g=nx.Graph()
  ```

  ![](assets/to-do-uncategorized-screenshots/no131.png)

  ```
  g.add_node('A')
  g.add_node('B')
  g.add_node('C')
  ```

  It adds the nodes. Then`g.nodes` to check.  
  ![](assets/to-do-uncategorized-screenshots/no132.png)

  ```
  g.add_edge('A','B')
  ```

  It adds egdes between A and B. Then`g.nodes` and`g.edges` to check.  
  ![](assets/to-do-uncategorized-screenshots/no133.png)

  ```
  nx.draw(g)
  ```

  ![](assets/to-do-uncategorized-screenshots/no134.png)

  ```
  g.add_edge('C','B')
  nx.draw(g)
  ```

  ![](assets/to-do-uncategorized-screenshots/no135.png)

## Get data by json

  ```
  import json
  content=open('miserables.json').read()
  data=json.loads(content)
  ```

 ![](assets/to-do-uncategorized-screenshots/no136.png)  
 The content is an object.

 ![](assets/to-do-uncategorized-screenshots/no137.png)  
 `json.loads` is to load a string which is given by content. Then data becomes the python structure.

  ```
  type(data)
  data.keys()
  data['nodes']
  data['links']
  ```

   ![](assets/to-do-uncategorized-screenshots/no138.png)  
   ![](assets/to-do-uncategorized-screenshots/no139.png)  
   Check the data. There are many nodes called 'group' and 'ID' and links called 'source' and 'target'.
  ```
  for n in data['nodes']:
  g.add_node(n['id'],group=n['group'])
  ```

  `n['id']` means extracting the id from every item in data\[nodes\], and add them into g.  
  `g.number_of_nodes` and `g.number_of_edges` to check the node.

  ```
  for l in data['links']:
  g.add_edge(l['source'],l['target'], **l)
  ```

  `**l` is an attribute. It means to take every item in 'key-value' pairs. So it equals to

  ```
  l['source'],l['target'], source=0,target=0,value=0
  ```

## Visualization Spring layout

* 'spring layout' is another name for 'force directed layout'.

  ```
  import matplotlib 
  %matplotlib inline
  nx.draw(g)
  ```

  ![](assets/to-do-uncategorized-screenshots/no140.png)

  ```
  from matplotlib import pyplot as plt
  plt.figure(figsize=(20,20))
  pos=nx.spring_layout(g)
  nx.draw_networkx_nodes(g,pos,node_color='#ccccff',alpha=0.5)
  nx.draw_networkx_edges(g,pos,width=1,alpha=0.3)
  labels=dict([(n,n)for n in g.nodes])
  _=nx.draw_networkx_labels(g,pos,labels=labels,font_color='#666666')
  ```

  ![](assets/to-do-uncategorized-screenshots/no141.png)

* The above one is the basic graph.

 ![](assets/to-do-uncategorized-screenshots/no142.png)  
 `plt.figure(figsize=(20,20))` to change the size.  
 `nx.draw_networkx_nodes` and `nx.draw_networkx_edges` to draw the nodes and edges.  
 `labels=dict([(n,n)for n in g.nodes])` and `_=nx.draw_networkx_labels` to draw the labels. Create a dict\[\(n,n\)\], whose n is from g.nodes

## Color specific nodes

  ```
  g.nodes['Anzelma']
  ```

  ![](assets/to-do-uncategorized-screenshots/no143.png)  
  We know the content of g.nodes

  ```
  import matplotlib
  color=matplotlib.cm.Accent
  color(10)
  ```

  ![](assets/to-do-uncategorized-screenshots/no144.png)  
  `matplotlib.cm` is a useful tool. You can try by yourself.It shows the R\(red\), G\(green\), B\(blue\) and alpha.

  ```
  for group in range(1,20):
  nodelist=[n for n in g.nodes if g.nodes[n]['group']== group]
  nx.draw_networkx_nodes(g,pos,nodelist=nodelist,node_color=color(group),alpha=0.8)
  ```

![](assets/to-do-uncategorized-screenshots/no145.png)

 ![](assets/to-do-uncategorized-screenshots/no146.png)
 If g.nodes's group = 1, add those nodes into the nodelist. They will be the same color 1 . If g.nodes's group = 2, they will be added to another nodelist ,and be colored 2.

## Shortest path

  ```
  sp=nx.shortest_path(g,'XXX','XXX')
  ```

  ![](assets/to-do-uncategorized-screenshots/no147.png)  
  It shows the shortest way between the two nodes.

  ```
  #base on the above graph
  nx.draw_networkx_edges(g,
  pos,
  edgelist=list(zip(sp[:-1],sp[1:])),
  width=5,
  edge_color='r'
  )
  ```

   ![](assets/to-do-uncategorized-screenshots/no148.png)  
   ![](assets/to-do-uncategorized-screenshots/no149.png)

## Centrality Measures

* **Degree centrality**: degree is the numbers of edges associated with the nodes.
* But not everyone is of the same importance. So **Closeness**  means the shorter the path, relationship is closer. 
* How many times the person be the bridge in the shortest path? This is **Betweenness**. Key messages are in those person.

  ```
  df_top_nodes=df.sort_values('closeness', ascending=False)[:5]
  #basic grah
  nx.draw_networkx_nodes(g,pos,nodelist=list(df_top_nodes.index),
  node_color='#ff7700',
  alpha=0.5)
  ```

   ![](assets/to-do-uncategorized-screenshots/no150.png)  
   ![](assets/to-do-uncategorized-screenshots/no151.png)  
   Sort by closeness.

## Structure degree

  ```
  g.degree
  ```

  ![](assets/to-do-uncategorized-screenshots/no152.png)

  ```
  pd.Series(dict(g.degree())).hist(bins=20)
  ```

  ![](assets/to-do-uncategorized-screenshots/no153.png)  
  `dict(g.degree())` and then `Series`. Then Draw a picture.

* Heave tail distribution, which is famous for rich will be richer and poor will be poorer.

## Clustering coefficient

  ```
  nx.algorithms.clustering(g,['XXX','XXX','XXX'])
  nx.average_clustering(g)
  ```

  The numbers of triangles over the number of potential triangles .
  ![](assets/to-do-uncategorized-screenshots/no154.png)
  ```
  nx.average_clustering(nx.complete_graph(5))
  ```

  ![](assets/to-do-uncategorized-screenshots/no155.png)

## Cliques part of the graph

  ```
  Cliques=list(nx.find_cliques(g))
  ```

  ![](assets/to-do-uncategorized-screenshots/no156.png)

  ```
  from matplotlib import pyplot as plt
  plt.figure(figsize=(20,20))
  pos=nx.spring_layout(g)
  nx.draw_networkx_nodes(g,
                     pos,
                     node_color='#ccccff',
                     alpha=0.5
                     )
  nx.draw_networkx_edges(g,
                     pos,
                     width=1,
                     alpha=0.3
                     )
  labels=dict([(n,n)for n in g.nodes])
  _=nx.draw_networkx_labels(g,
                   pos,
                   labels=labels,
                   font_color='#666666'
                   )
  ```

  The above is the basic graph. Then

  ```
  nx.draw_networkx_nodes(g,
                       pos,
                       nodelist=cliques[1],
                       node_color='#ff7700',
                       alpha=0.5
                       )
  ```

  ![](assets/to-do-uncategorized-screenshots/no157.png)

## Connected components

  ```
  components =list(nx.connected_components(g))
  ```

  to find those who are not connected by others.

## Community detection

  ```
  from networkx.algorithms import community
  communities = list(community.girvan_newman(g))
  ```

  ![](assets/to-do-uncategorized-screenshots/no158.png)  
  Those in the community is much denser,and those between the community is sparser.

  ```
  communities = list(community.label_propagation_communities(g))
  ```

  The function is similar.

## Color the nodes

```
plt.figure(figsize=(20,20))
pos=nx.spring_layout(g)
nx.draw_networkx_edges(g,pos,width=1,alpha=0.3)

for i in range(0, len(communities)):
  nodelist=communities[i]
  print(nodelist)
  nx.draw_networkx_nodes(g,pos,nodelist=nodelist,node_color=color(i), alpha=0.8)
  labels=dict([(n, '%s:%s' % (n, g.nodes[n]['group'])) for n in nodelist])
  nx.draw_networkx_labels(g,pos,labels=labels,fint_color='#666666')
```

![](assets/to-do-uncategorized-screenshots/no159.png)  
![](assets/to-do-uncategorized-screenshots/no160.png)
