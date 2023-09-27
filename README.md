Instruccines de inicialización:

ros2 launch slam_toolbox online_async_launch.py param_file:=.src/my_bot/config/mapper_params_online_async.yaml use_sim-time:=true #map rviz

ros2 launch my_bot launch_sim.launch.py world:=src/my_bot/worlds/pws.world #Launch del mundo

rviz2 -d pws.rviz #Config de rviz

ros2 run nav2_map_server map_server --ros-args -p yaml_filename:=P_mapsave.yaml -p use_sim_time:=true #Cargar mapeado sin escaner

ros2 run nav2_amcl amcl --ros-args -p use_sim_time:=true #navegación y estimacion de posicion amcl

ros2 run nav2_util lifecycle_bringup amcl #activador amcl
ros2 run nav2_util lifecycle_bringup map_server #activador map_server

ros2 run teleop_twist_keyboard teleop_twist_keyboard #control manual del robot (teclado)

Scripts adicionales antes:
source install/setup.bash #variables de entorno
colcon build --symlink-install #cargador de archivos

subida de datos a git (dentro de src y my_bot)
git status
git add .
git status
git push -m "#comentario de subida"
git push
