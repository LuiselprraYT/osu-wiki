---
stub: true
---

# Slider tick

Le **slider tick** est un petit point (tick) qui apparaît à l'intérieur des [sliders](/wiki/Hit_object/Slider). Le nombre de ticks utilisés dans un slider dépend du [slider velocity](/wiki/Hit_object/Slider_velocity), du [BPM](/wiki/Beatmapping/Beats_per_minute) et du timing.

Au cours d'une partie, les sliders ticks sont collectés en gardant le curseur dans le follow circle du slider, qui, une fois collecté, augmentera le combo d'une unité par slider tick collecté. Si un joueur ne parvient pas à collecter tous les ticks d'un slider, il recevra un `100` et brisera son combo.
