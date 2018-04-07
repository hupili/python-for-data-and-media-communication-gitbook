# Week 9
### 1. Common license

* GPL=use freely. But your work based on GPL is required to open source.
* GNU=general public license 
* MIT=do whatever you want. You are obligated to provide attribution with your code or binary (e.g. say "this project uses code that is MIT licensed" -- with a copy of the license and copyright of the author of the open source code).
* There are 2 pictures for reference.  
![](/assets/Screen Shot 2018-04-07 at 2.07.51 pm.png)

### 2. Basic preparations
 
##### Pip install by one step

* First of all, download the requirements.txt from  https://github.com/hupili/python-for-data-and-media-communication to your desktop.

* This file is a list of many modules. So you only need to do this for once to have all the packages.

* Check on your virtual environment to make sure you have this file.
![](/assets/Screen Shot 2018-04-07 at 2.21.32 pm.png)

* Then do as follows.
![](/assets/Screen Shot 2018-04-07 at 2.20.38 pm.png)

##### jupyter display a picture
* Create a picture "picture.png" on your repository.
For example, on venv.
![](/assets/Screen Shot 2018-04-07 at 2.34.30 pm.png)

* 
```
jupyter notebook
```
Then in the venv folder create a new python.

* 
```
from IPython.display import Image
Image("picture.png")
```
![](/assets/Screen Shot 2018-04-07 at 2.39.35 pm.png)

##### Markdown to show a picture

* Change to the markdown environment.
![](/assets/Screen Shot 2018-04-07 at 2.41.17 pm.png)

* 
```
![](picture.png)
```
![](/assets/Screen Shot 2018-04-07 at 2.44.51 pm.png)

##### HTML link

* 
```
from IPython.core.display import HTML
HTML('<a href="http://example.com">link</a>')
```
![](/assets/Screen Shot 2018-04-07 at 2.49.07 pm.png)
You can change to website.

* 
Block quote, or ''' ''', is to quote code. 
![](/assets/Screen Shot 2018-04-07 at 2.52.25 pm.png)


### 3. Graph

### Count the edge

* Represents of the graph.
>![](/assets/Screen Shot 2018-04-07 at 2.56.16 pm.png)
![](/assets/Screen Shot 2018-04-07 at 2.57.29 pm.png)

* Try to count the edge between those circles.
>![](/assets/Screen Shot 2018-04-07 at 3.02.40 pm.png)
This undirected table is symmetric. It shows that 1 and 2 has one edge. 2 and 3 is the same. 
![](/assets/Screen Shot 2018-04-07 at 3.01.17 pm.png)
The above one is directed.
* There are different ways to show the relationships.
>![](/assets/Screen Shot 2018-04-07 at 3.08.36 pm.png)
![](/assets/Screen Shot 2018-04-07 at 3.10.08 pm.png)
![](/assets/Screen Shot 2018-04-07 at 3.11.27 pm.png)
Then we can infer the list.

### Network example

* 
```
import networkx as nx
g=nx.Graph()
``` 
![](/assets/Screen Shot 2018-04-07 at 3.16.35 pm.png)

* 
```
g.add_node('A')
g.add_node('B')
g.add_node('C')
```
It adds the nodes. Then`g.nodes` to check.
![](/assets/Screen Shot 2018-04-07 at 3.17.55 pm.png)

*  
```
g.add_edge('A','B')
```
It adds egdes between A and B. Then`g.nodes` and`g.edges` to check.
![](/assets/Screen Shot 2018-04-07 at 3.20.57 pm.png)

*  
```
nx.draw(g)
```
![](/assets/Screen Shot 2018-04-07 at 3.25.48 pm.png)

* 
```
g.add_edge('C','B')
nx.draw(g)
```
![](/assets/Screen Shot 2018-04-07 at 3.27.31 pm.png)


### Get data by json
*  
```
import json
content=open('miserables.json').read()
data=json.loads(content)
```

>![](/assets/Screen Shot 2018-04-07 at 3.35.36 pm.png)
The content is an object.

>![](/assets/Screen Shot 2018-04-07 at 3.32.59 pm.png)
`json.loads` is to load a string which is given by content. Then data becomes the python structure.

*  
```
type(data)
data.keys()
data['nodes']
data['links']
```
>![](/assets/Screen Shot 2018-04-07 at 3.37.51 pm.png)
![](/assets/Screen Shot 2018-04-07 at 3.41.47 pm.png)
Check the data. There are many nodes called 'group' and 'ID' and links called 'source' and 'target'.

*  
```
for n in data['nodes']:
  g.add_node(n['id'],group=n['group'])
```
`n['id']` means extracting the id from every item in data[nodes], and add them into g.
`g.number_of_nodes` and `g.number_of_edges` to check the node.

* ```
for l in data['links']:
  g.add_edge(l['source'],l['target'], **l)
```
`**l` is an attribute. It means to take every item in 'key-value' pairs. So it equals to
```
l['source'],l['target'], source=0,target=0,value=0
```

### Visualization - Spring layout

*  'spring layout' is another name for 'force directed layout'.

*  
```
import matplotlib 
%matplotlib inline
nx.draw(g)
```
![](/assets/Screen Shot 2018-04-07 at 5.03.46 pm.png)

*  
```
from matplotlib import pyplot as plt
plt.figure(figsize=(20,20))
pos=nx.spring_layout(g)
nx.draw_networkx_nodes(g,pos,node_color='#ccccff',alpha=0.5)
nx.draw_networkx_edges(g,pos,width=1,alpha=0.3)
labels=dict([(n,n)for n in g.nodes])
_=nx.draw_networkx_labels(g,pos,labels=labels,font_color='#666666')
```
![](/assets/Screen Shot 2018-04-07 at 5.20.42 pm.png)
*  The above one is the basic graph.

>![](/assets/Screen Shot 2018-04-07 at 5.24.43 pm.png)
`plt.figure(figsize=(20,20))` to change the size.
`nx.draw_networkx_nodes` and `nx.draw_networkx_edges` to draw the nodes and edges.
`labels=dict([(n,n)for n in g.nodes])` and `_=nx.draw_networkx_labels` to draw the labels. Create a dict[(n,n)], whose n is from g.nodes

### Color specific nodes

*  
```
g.nodes['Anzelma']
```
![](/assets/Screen Shot 2018-04-07 at 5.40.46 pm.png)
We know the content of g.nodes

*  
```
import matplotlib
color=matplotlib.cm.Accent
color(10)
```
![](/assets/Screen Shot 2018-04-07 at 5.28.26 pm.png)
`matplotlib.cm` is a useful tool. You can try by yourself.It shows the R(red), G(green), B(blue) and alpha. 

*  
```
for group in range(1,20):
  nodelist=[n for n in g.nodes if g.nodes[n]['group']== group]
  nx.draw_networkx_nodes(g,pos,nodelist=nodelist,node_color=color(group),alpha=0.8)
```
![](/assets/Screen Shot 2018-04-07 at 5.37.40 pm.png)

>![](/assets/Screen Shot 2018-04-07 at 6.01.02 pm.png)If g.nodes's group = 1, add those nodes into the nodelist. They will be the same color 1 . If g.nodes's group = 2, they will be added to another nodelist ,and be colored 2.

### Shortest path

*  
```
sp=nx.shortest_path(g,'XXX','XXX')
```
![](/assets/Screen Shot 2018-04-07 at 6.02.26 pm.png)
It shows the shortest way between the two nodes.

*  
```
#base on the above graph
nx.draw_networkx_edges(g,
pos,
edgelist=list(zip(sp[:-1],sp[1:])),
width=5,
edge_color='r'
)
```
>![](/assets/Screen Shot 2018-04-07 at 6.05.34 pm.png)
![](/assets/Screen Shot 2018-04-07 at 6.09.18 pm.png)

### Centrality Measures

* **Degree centrality**: degree is the numbers of edges associated with the nodes.
*  But not everyone is of the same importance. So **Closeness**  means the shorter the path, relationship is closer. 
*  How many times the person be the bridge in the shortest path? This is **Betweenness**. Key messages are in those person.

*  
```
df_top_nodes=df.sort_values('closeness', ascending=False)[:5]
#basic grah
nx.draw_networkx_nodes(g,pos,nodelist=list(df_top_nodes.index),
node_color='#ff7700',
alpha=0.5)
```
>![](/assets/Screen Shot 2018-04-07 at 6.23.04 pm.png)
![](/assets/Screen Shot 2018-04-07 at 6.24.26 pm.png)
Sort by closeness.


### Structure - degree

*  
```
g.degree
```
![](/assets/Screen Shot 2018-04-07 at 6.28.36 pm.png)

*  
```
pd.Series(dict(g.degree())).hist(bins=20)
```
![](/assets/Screen Shot 2018-04-07 at 6.28.25 pm.png)
`dict(g.degree())` and then `Series`. Then Draw a picture.
* Heave tail distribution, which is famous for rich will be richer and poor will be poorer.

### Clustering coefficient

*  
```
nx.algorithms.clustering(g,['XXX','XXX','XXX'])
nx.average_clustering(g)
```
The numbers of triangles over the number of potential triangles .
![](/assets/Screen Shot 2018-04-07 at 6.41.00 pm.png)
*  
```
nx.average_clustering(nx.complete_graph(5))
```
![](/assets/Screen Shot 2018-04-07 at 6.41.12 pm.png)

### Cliques (part of the graph)
*  
```
Cliques=list(nx.find_cliques(g))
```
![](/assets/Screen Shot 2018-04-07 at 6.44.29 pm.png)

*  
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

*  
```
nx.draw_networkx_nodes(g,
                        pos,
                        nodelist=cliques[1],
                        node_color='#ff7700',
                        alpha=0.5
                        )
```
![](/assets/Screen Shot 2018-04-07 at 6.48.09 pm.png)

### Connected components

*  
```
components =list(nx.connected_components(g))
```
to find those who are not connected by others.

### Community detection

*  
```
from networkx.algorithms import community
communities = list(community.girvan_newman(g))
```
![](/assets/Screen Shot 2018-04-07 at 6.55.48 pm.png)
Those in the community is much denser,and those between the community is sparser.

*  
```
communities = list(community.label_propagation_communities(g)) 
```
The function is similar.

##### Color the nodes

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
![](/assets/Screen Shot 2018-04-07 at 7.16.10 pm.png)
![](/assets/Screen Shot 2018-04-07 at 7.15.58 pm.png)



