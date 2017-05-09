#Dijkstra's algorithm

###Some Wiki for ya
Made by Edsger W. Dijkrsta in 1956. It is used to find the shortest path from a single node to another one (or all of the other nodes, with some slight modification). Note that it doesn't work properly if there are negative weight edges in the graph.

###What does it need
The information it generally requires is of course which node is the source and which one is the target and a graph containing the following:
- the nodes
- the "edges" between the nodes (you can think of them as available paths to go from one node to another)
- the "weight" of the edges (basically the cost to go from one node to another using a particular edge)

###How it works

#####Initialising
At the beginning you don't know the distance from the source node to any other node, so you set the source node's distance to 0 (since the distance from A to A will always be 0) and you set the distance of all the other nodes to infinity.

#####Hey neighbor!
This is the core of the algorithm; checking a node's neighbor. A neighbor of node A is a node that is connected by an edge to node A.

The first part of this is finding a neighbor. A general way of doing this is by checking all of the edges to see which connect the node you're checking with another one. Note that if this is a large graph it will take quite a bit of computing time to check all of the edges.

You found your first neighbor? Great! Now you need to mark how far he is from the source node. To do that, you take the distance of the node you're checking and add the weight of the edge to it. But, before you go ahead and mark that as the distance, make sure the neighbor hasn't been marked with any smaller distance. If you do mark the distance, also mark the neighbor's "previous node" as the node you're checking.

#####Who's next
So you found all of the neighbors of your node and now you have to move on to the next one. To figure out which node is next, you see which node has the least distance from the source. Make sure not to check nodes you have already gone through.

#####When to stop
You stop when you're checking the target node. By that, I mean checking its neighbors, not finding it out as a neighbor.

#####But I wanted a path, not the distance
Remember when we told you to mark each neighbor's previous node? Good. To get the path, just backtrack from your target by going to its previous node and then the previous node of that node and so on until you reach the source.