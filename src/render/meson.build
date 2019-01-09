all_sources += files(
  'SDL_d3dmath.c',
  'SDL_render.c',
  'SDL_yuv_sw.c',
)

subdir('direct3d')
subdir('direct3d11')
# MaxW: I can't find anything in CMakeLists.txt that causes this to be included
#if host_machine.system() == 'darwin'
#subdir('metal')
#endif
subdir('opengl')
subdir('opengles')
subdir('opengles2')
subdir('psp')
subdir('software')
