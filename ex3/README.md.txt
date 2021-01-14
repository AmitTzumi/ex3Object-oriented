In this task we will improve task 2 (part 1), by converting the directed graph code to python and extend it, and by adding new functionality to the graph_algo class.
after the convertion between java and python, we will implement the additional methods of calculating SCC and plotting the graph using matplotlib. 
We will also implement UnitTest files for each logical class we convert, in order to make sure our code runs without errors.
in addition to all of the implementation in python, we will also write 2 additional functions in Java in order to test the 2 implementations.
we've also created a python file for the plotting of networkx graph named 'nx_plot.py'.

The main classes we have built in this project are:
Helper classes: NodeData and EdgeData
Interface implementations: DiGraph (implements GraphInterface) and GraphAlgo (implements GraphAlgoInterface).

NodeData:
* __init__ - constructor class for object
* getNi_out() - returns a collection with all the out edges of this node_data 
* getNi_in() - returns a HashSet with all the in edges of this node_data
* getNiEdge(dest) - returns a specific edge of this NodeData
* addNi_out(dest, w) - This method adds the out_edge to this NodeData
* addNi_in(src) - This method adds the in_edge to this NodeData
* hasNi_out(dest) - return true iff this<==>key are adjacent, as an edge between them
* removeEdge_out(key) - Removes the out-edge with the key - 'key'
* removeEdge_in(key) - Removes the in-edge with the key - 'key'
* getKey() - Returns the key (id) associated with this node
* getLocation() - Returns the location of this node, if none return null
* setLocation() - Allows changing this node's location
* getWeight() - Returns the weight associated with this node
* setWeight(w) - Allows changing this node's weight
* getInfo() - Returns the remark (meta data) associated with this node
* setInfo(s) - Allows changing the remark (meta data) associated with this node
* getTag() - Temporal data (aka color: e,g, white, gray, black) which can be used be algorithms
* setTag(t) - Allows setting the "tag" value for temporal marking an node - common practice for marking by algorithms
* __eq__(other) - equals function - return true if the two object are equals, else returns false


EdgeData:
* __init__ - constructor class for object
* getSrc() - return the id of the source node of this edge
* getDest() - return the id of the destination node of this edge
* getWeight() - return the weight of this edge (positive value).
* getInfo() - return the remark (meta data) associated with this edge
* getTag() - which can be used in algorithms temporal data (aka color: white, gray, black)
* setInfo(info) - Allows changing the remark (meta data) associated with this edge.
* setTag(tag) - this method allows setting the tag value for temporal marking an edge - common practice for marking by algorithms

GraphAlgo:
* __init__ - constructor class for object
* init(g) - init function for class GraphAlgo with graph g
* get_graph() - returns the directed graph on which the algorithm works on
* parse_path(file_name) - a helper function to parse the file absolute path
* load_from_json(file_name) - loads a graph from a json file
* save_to_json(file_name) - saves the graph in json format to a file
* connected_components() - Finds all the Strongly Connected Component(SCC) in the graph.
* connected_component(id1) - Finds the Strongly Connected Component(SCC) that node id1 is a part of.
* Dijkstra(s) - implementation of the dijkstra algorithm
* shortest_path_dist(id1, id2) - helper function to get the distance of the shortest path between id1 and id2
* shortest_path(id1, id2) - a function to return a list of the shortest path between id1 and id2
* get_graph_lims() -  a helper function for the plot graph func. will calculate the borders of the graph to be plotted
* plot_graph() - plots the graph using matplotlib
	Inner class Node: this class is used for Dijkstra algorithm. used to save the key and cur distance for node, and also for comparing function (__cmp__)

DiGraph:
* __init__ - constructor class for object
* getNode(key) - returns the node_data by the key.
* getEdge(src, dest) - returns the data of the edge (src,dest), null if none.
* addNode(n) - adds a new node to the graph with the given node_data.
* add_node(node_id) - adds a node to the graph with id 'node_id'
* hasEdge(src, dest) - return true iff (if and only if) there is an edge between src and dest
* add_edge(id1, id2, weight) - Connects an edge with weight 'weight' between node id1 to node id2.
* getV() - This method returns a pointer (shallow copy) for the collection representing all the nodes in the graph.
* get_all_v() - return a dictionary of all the nodes in the Graph, each node is represented using a pair (node_id, node_data)
* get_all_e() - return a dictionary of all the edges in the Graph, each edge is of type EdgeData
* all_in_edges_of_node(id1) - return a dictionary of all the nodes connected to (into) node_id ,each node is represented using a pair (other_node_id, weight)
* all_out_edges_of_node(id1) - return a dictionary of all the nodes connected from node_id , each node is represented using a pair
* getE(node_id) - This method returns a pointer (shallow copy) for the collection representing all the edges getting out of the given node (all the edges starting (source) at the given node)
* remove_node(key) - Deletes the node (with the given ID) from the graph - and removes all edges which starts or ends at this node. This method should run in O(k), V.degree=k, as all the edges should be removed
* remove_edge(node_id1, node_id2) - Deletes the edge from the graph.
* v_size() - Returns the number of vertices (nodes) in the graph.
* e_size() - Returns the number of edges (assume directional graph).
* get_mc() - Returns the Mode Count - for tests changes in the graph.
* __eq__ - equals function - return true if the two object are equals. else, return false
* __repr__() - Returns a string representing the directed graph

In addition, we implemented 2 java methods with the same signature:
* connectedComponents() - Finds all the Strongly Connected Component(SCC) in the graph.
* connectedComponent(int id1) - Finds the Strongly Connected Component(SCC) that node id1 is a part of.
