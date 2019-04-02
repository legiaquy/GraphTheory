# Graph Theory Assignment
## Group Members
- Do Thu Anh (USTHBI7-006)
- Ha Minh Huong (USTHBI7-079)
- Tran Thi Thuy Kieu (USTHBI7-088)
- Nguyen Dinh Mau (USTHBI7-106)
- Le Gia Anh Quy (USTHBI7-133)
- Source Code: https://github.com/legiaquy/GraphTheory

## Introduction
In this assignment, we do some exercises in Python that are relevant to Graph Theory, based on distance-vn.txt file that contains distances between some cities in Vietnam.

## Objectives
- Build an adjacency matrix and a graph with vertices being the cities and edges being connections of  the 2 cities if their distances are stored in the file.
- Additional functions:
    - Degree function to return the degree of a particular city - a particular node
    - Prim and Kruskal Algorithms to find the Minimal spanning tree
    - Draw graph using networkx
- Programming Language: Python

## Method & Results
### Preprocess input file
After receiving the file, we checked it and realized that it had a problem. This is, 1 city has 2 different names: Quy Nhon & Qui Nhon, Kontum & Kon Tum, Ha Long City & Ha Long, Bien Hoa & Bien Hoi. We changed to: Quy Nhon, Kon Tum, Ha Long and Bien Hoa.
### Adjacency matrix
We create a function named graph_matrix(file_path). The input is the path to the .txt file, and the output includes an adjacency matrix and a list of all cities in ‘start’ and ‘end’   destination, with its IDs. From that ‘cities’ list (which contains a lot of duplicates), we create the ‘city’ list with distinct cities.
For the matrix, firstly, each city has its own id, we create the id for all distinct cities in the input file. We have 68 distinct cities at all and the id is the integer numbers from 0 to 67, so the matrix has size 68x68. The indexes of columns and rows are correctly id’s of the cities. If 2 cities has id i and j are connected, the elements at position [i,j] and [j,i] are equals to its distance, if not, this position is 0.
### Graph
Based on the adjacency matrix, we build the graph and store it in the dictionary of Python. Here is our code:

![build_graph](https://i.imgur.com/l4gQ0Gn.png)

and the output:
![build_graph_o](https://i.imgur.com/emUwWJB.png)

However, this way does not contain the distance between the cities. Thus, we have a function name generate_edges(graph) to generate all the edges with its weights (the distance). And we get the result with 160 directed edges (from 80 undirected edges in the input file):
![build_edge](https://i.imgur.com/ommMHrf.png)

Here is the image of the graph
![graph_img](https://i.imgur.com/2Qdw1e7.png)

### Degree function
We have the degree_of(cityname) function to get the degree of a city. The input is the name of the city. For example, degree_of("Ha Noi"), the output is 7.
To get the degree, first, we identify the id of the city with that name. That id corresponds to the position of the row with that city’s id in the adjacency matrix. This row contains distances from that city to other cities. If the distance equals 0, it means the two cities are not connected. Therefore, we count the number of distances different to 0 in that row to get the degree of the city.

### Minimal Spanning Tree
#### Prim Algorithm
In this problem, we are using Graph and Vertex module from https://github.com/bnmnetp/pythonds. Then, we implement Prim algorithm:

![prim](https://i.imgur.com/vydGUfK.png)

Here are the first 10 of 68 edges in the minimum spanning tree with total weight is 26038.6:

![prim_path](https://i.imgur.com/ZUyfaiu.png)

And here is the Minimum Spanning Tree image using Prim:

![prim_img](https://i.imgur.com/v1pEaZ5.png)

#### Kruskal Algorithm
![kruskal](https://i.imgur.com/yswXm6m.png)

And here is the output:

![kruskal_path](https://i.imgur.com/EPL9xn5.png)

#### Dijikstra Algorithm
![dijkstra](https://i.imgur.com/gXCwnlj.png)

And the output includes distance and paths

![dijkstra_distance](https://i.imgur.com/Ln2mMii.png)

![dijkstra_path](https://i.imgur.com/WSMsbhz.png)


## Conclusion
- Done
    - Complete all the objectives
- Difficulties:
    - Hard to implement algorithm in paralelly
    - Input and Output: not consistent
    - Spend a lot of time to re-modify
- Future works:
    - Unify the code


