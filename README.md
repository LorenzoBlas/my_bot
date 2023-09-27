# Scripts de inicio:
## Robot autonomo en lenguaje Pyhton con uso de ubuntu

### Iniciar antes de todo
* entrar en el entorno de trabajo project_ws/
* source install/setup.bash


### Pasos de inicio:
* Activar registro de mapa
* Cargar launch del mundo
* Iniciar rviz2 con el mundo
* Cargar mapeado prehecho (en este caso de deshabilitara el primer script del registro del mapa) 
* Cargar odometría de posicion amcl
* Usar bringup's amcl y map_server
* Activar control del teclado

```
ros2 launch slam_toolbox online_async_launch.py param_file:=.src/my_bot/config/mapper_params_online_async.yaml use_sim-time:=true 

ros2 launch my_bot launch_sim.launch.py world:=src/my_bot/worlds/pws.world

rviz2 -d pws.rviz

ros2 run nav2_map_server map_server --ros-args -p yaml_filename:=P_mapsave.yaml -p use_sim_time:=true

ros2 run nav2_amcl amcl --ros-args -p use_sim_time:=true

ros2 run nav2_util lifecycle_bringup amcl

ros2 run nav2_util lifecycle_bringup map_server

ros2 run teleop_twist_keyboard teleop_twist_keyboard

ros2 launch nav2-bringup navigation_launch.py use_sim_time:=true
```
 
### Constructor de nuevos archivos
```
 colcon build --symlink-install
```
### subida de archivos a git (dentro de src y my_bot en el entorno de trabajo)
* desde project_ws/src/my_bot
```
git status
git add .
git status
git push -m "#comentario de subida"
git push
```


