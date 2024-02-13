# Multi-Layer Motion Planning For Autonomous Vehicles

## About the project

The self-driving car requires a robust motion planner for navigating itself in structured environments such as roads or highways and unstructured environments such as parking lots. In structured environments, some constraints exists such as the maintenance of high speeds, the presence of curvature roads, and specific driving rules. On the other hand, in unstructured environments, there is no lane information to guide or constrain the actions of the vehicle. To navigate an autonomous vehicle in both of these environments, a multi-layer motion planner with active obstacle avoidance is needed.

The main focus of this project is to design a multi-layer motion planner with global route planning and local route planning using state-of-the-art motion planning algorithms that can be incorporated to navigate autonomous vehicles in both structured and unstructured environments.

## Mulit-layer Motion Planner

Please refer to the [report](https://github.com/DhirajRouniyar/Assets/blob/main/Report/Report_MP_Dynamic%20Obstacles.pdf) for an in-depth explanation of algorithms, experiments performed, and achieved results.

The motion planning layer provides a plan to achieve a particular desired goal considering the current and predicted vehicle states. The desired goal could be anything like traversing a particular lane, avoiding a particular obstacle, or following another vehicle. The motion planner executes these planning considering the behavioral constraints in the environment, and provides an optimal solution to achieve the desired goal. The motion planner executes these goals by generating a set of trajectories using trajectory generating algorithms.

- Global Planner 
  -  The global planner calculates the shortest route from the initial position to the goal position using the given or generated map of the surrounding environment. In order to do this, we sample the environment with random points (nodes of the graph), and then we draw edges between these nodes and choose the edges that are collision-free. Last, using the Dijkstra discrete search algorithm, we find the shortest path using these sample nodes while considering the collision checker algorithm on each step. 
&nbsp;

- Local Planner
  - Once the waypoints are decided by the global planner, the next layer of the motion planner is the local planner. The local planner predicts the future states based upon the control inputs to an ego vehicle to perform the global map, and simultaneously takes care of close-in obstacle avoidance, even if it was not provided by the global plan. In order to achieve this task, we develop a state lattice planner using the hybrid A* discrete search algorithm. This planner functions in accordance with an obstacle map of all the surrounding obstacles created by the collision checker algorithm. If the obstacle is in close proximity to an ego vehicle or if the predicted future trajectory of an ego vehicle lies in close proximity to the obstacle, then that trajectory is encoded as a hard constraint and fed to the local planner to strictly avoid. In such a case, the local planner finds an optimal path to reach the next possible waypoints on the global map.
&nbsp; 

- Active collision-checker algorithm
  - In order to avoid static and/or dynamic obstacles during both global and local trajectory exploration, we developed a collision checker algorithm based on convex hull. To make the collision-free waypoint search more efficient in terms of obstacle avoidance, we pad all the obstacles with our ego vehicle’s dimensions using the Minkowski sum method.
  

## Results
- Structured Environment
  - Since for a structured environment, autonomous vehicles are being made to follow lane-divided roads featuring unidirectional flows, some of the tasks that are to be done in this regard are as follows:
    1) Car following
    2) Lane keeping
    3) Lane changing
    4) Passing
    5) Overtaking
    6) Obstacle avoidance
    
  
<img width="471" alt="Screenshot 2023-05-27 at 7 43 18 PM" src="https://github.com/DhirajRouniyar/Assets/blob/main/Images/static%20and%20dynamic%20obstacle%20avoidance.png">

&nbsp;


<img width="471" alt="Screenshot 2023-05-27 at 7 46 37 PM" src="https://github.com/DhirajRouniyar/Assets/blob/main/Images/static%20and%20dynamic%20obstacle%20avoidance_2.png">

&nbsp;
&nbsp;

- Unstructured Environment
  - For an unstructured environment, lane structure is not available. Hence, the most important task that is to be done in this regard is the navigation through the static and/or dynamic obstacle where the ego must reach a given goal while avoiding obstacles like curbs, parked cars and so on.
   
<img width="471" alt="Screenshot 2023-05-27 at 7 48 30 PM" src="https://github.com/DhirajRouniyar/Assets/blob/main/Images/static%20and%20dynamic%20obstacle%20avoidance_3.png">

&nbsp;

<img width="472" alt="Screenshot 2023-05-27 at 7 41 29 PM" src="https://github.com/DhirajRouniyar/Assets/blob/main/Images/static%20and%20dynamic%20obstacle%20avoidance_4.png">

## Demo



https://github.com/DhirajRouniyar/Assets/blob/main/Videos/241452845-024b7adb-94ea-41f1-98f7-2bc1064e002f.mp4

&nbsp;
&nbsp;


https://github.com/DhirajRouniyar/Assets/blob/main/Videos/241452342-cfb89a4c-4be7-4a2b-a13f-8ba052888b16.mp4

&nbsp;
&nbsp;

https://github.com/DhirajRouniyar/Assets/blob/main/Videos/241452368-b6822cb2-d98e-42ae-82ad-49cd47a9ffb3.mp4

&nbsp;
&nbsp;


https://github.com/DhirajRouniyar/Assets/blob/main/Videos/241452471-cf27c6b9-0c1a-434e-8561-290e545eca1a.mp4

&nbsp;
&nbsp;


https://github.com/DhirajRouniyar/Assets/blob/main/Videos/241453118-1c37f418-2aa6-477f-91a4-8cc6e0dfc1ac.mp4

&nbsp;
&nbsp;


## References

* [Steven M. LaValle. Planning Algorithms. Cambridge University Press, May 2006.
9780521862059.](http://lavalle.pl/planning/)

 


    



