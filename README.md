# AI_Maze_generator_and_solver
  This is the repo of our AI final project
# Introduction
  Our problem is to construct an auto maze generator, the maze we generate will have only one path that leads to the goal , all roads in the maze are one block wide,     and there are no loops in the maze.

  The topic we chose can be applied on game design, like generating dungeon maps as well as NPC pathing.

  We have also constructed different types of maze solvers, to help us realize the differences between the algorithms and also to find the path of maze fast, and make    the maze design conveniently. 
# Related work
  Most of the maze generators on the web uses algorithms like Kruskal’s, Recursive Backtracker, Wilson’s etc, while our generator uses random DFS. To keep the road one   block wide, the explorer explores two blocks per iteration, however doing so confines the maze dimensions to an odd number.

  For the maze solver, since DFS, BFS and A* are covered in previous assignments, we added an additional IDA* maze solver, but we still kept the other algorithms for     comparison.
# Dataset/Platform
  The dataset is generated by our maze generator.

  We’ve coded the AI algorithms using generic python libraries(without AI libraries like tensorflow).The result is displayed with pygame .
# Baseline
  We use random DFS to build our maze generator. 

  We test for all possible steps which are valid, and randomly pick which action to do. We record the nodes that were chosen, and trace back to earlier nodes if the    algorithm explores to a dead end. 

  We use BFS, DFS, A* and IDA* to solve the maze, all possible paths in the maze form an unweighted & undirected graph.
# Main Approach
  Base on DFS

  First, we set the dimensions of the maze, then set the start and goal nodes. We simulate 2 steps in all 4 directions, and check the validity of the actions(if its    within the set dimensions and if it doesn’t bump into a dead end). If one of the arguments is false, trace the history to find a node that has a valid move and     explore from said node. The maze is fully explored when the algorithm has traced back to the starting node.

  For the solvers, we run each algorithm on the generated maze in an iterative fashion(except for IDA*) so we can easily show the progress of the search, and since   IDA* isn’t written iteratively, only the result is shown.

  If the pathfinder finds the goal, we reconstruct the path by tracing the parent of each node.
# Results & Analysis
  Types of experiment : we can change the maze dimensions, the start and goal nodes, and maze solving algorithm. We have also tried to modify the shape of the          maze(circles, triangles etc.), but due to the limits of our generation algorithm, this was not implemented.

  Discussion and analysis : since each step we explore two blocks, the nodes whose x and y coordinates are both odd numbers is guaranteed to be reached. The reason   why our IDA* implementation is slower might be due to the high depth of the maze and not having an efficient pruning method.
  
  Limitation of our work : as mentioned previously, every row and column length is limited to odd numbers. For the IDA* algorithm, since our implementation uses        recursion, it is restricted by the python recursion depth limit, resulting it not being able to run larger mazes.

  Method application : Dungeon generation and NPC pathing in video games .

  Other : The visualization of the searching process is slow since the program re-graphs the entire graph each step.
# Requirement & Usage
  pip install -r requirements.txt    ( NumPy and Pygame )
  
  Run maze generator : 
    (display : 1 default true, 0 false) (num_maze : default 1)
    python maze_generator.py --display=1 --num_mazes=1
    
  Run solver : 
    (algorithm + _pathfinder) (maze name + .csv)
    python dfs_pathfinder.py --maze_file=maze_0.csv --display=1
    
  Run visualizer : 
    (algorithm : dfs, bfs, Astar, IDAstar
    python visualize.py --maze_file=maze_0.csv --algorithm=dfs
    
# Other detail please read the slide 
