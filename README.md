# Projet RI partie 1
Ce repo contient les packages de la première partie du projet.

### part_one_urdf
Ce package l'urdf d'une jambe du robot ainsi qu'un launch file pour visualizer la jambe.

### udm_project_moveitconfig
Ce package a été généré avec moveit

### udm_project_control
Ce package contient les noeuds, les services et les launch file nécéssaire pour controler la jambe à travers la cinématique directe ou inverse

## Installation
Pour installer ce noeud il faut le cloner dans le dossier src de votre catkin workspace (catkin_ws).

```
cd catkin_ws/src
git clone https://github.com/IF488/MIAR_ROS_1.git
catkin build
cd ..
source devel/setup.bash
```
## Execution 
### Visualiser la jambe
Pour visualiser, il faut executer le code suivant dans le terminal de votre workspace:

```
source devel/setup.bash
roslaunch part_one_urdf simulate.launch
```
### Controler la jambe à l'aide de la cinématique directe

Dans le premier terminal de votre catkin workspace:
```
source devel/setup.bash
roslaunch udm_project_moveitconfig demo.launch
```

Dans le deuxième terminal de votre catkin workspace:
```
source devel/setup.bash
roslaunch udm_project_control direct.launch
```

Dans le troisième terminal de votre catkin workspace:
```
source devel/setup.bash
rosservice call /direct_kin_service_legmr "joint1:
 data: -0.4
joint2:
 data: -0.4
joint3:
 data: 0.2
joint4:
 data: -0.3"
```
NB: Vous pouvez choisir d'autre valeur. 

### Controler la jambe à l'aide de la cinématique inverse

Dans le premier terminal de votre catkin workspace:
```
source devel/setup.bash
roslaunch udm_project_moveitconfig demo.launch
```

Dans le deuxième terminal de votre catkin workspace:
```
source devel/setup.bash
roslaunch udm_project_control indirect.launch
```

Dans le troisième terminal de votre catkin workspace:
```
source devel/setup.bash
rosservice call /indirect_kin_service_legmr "pose:
 orientation:
  w: 1
 position:
  x: 0.4
 position:
  y: 0.4
 position:
  z: -0.2"
```
NB: Vous pouvez choisir d'autre valeur. 