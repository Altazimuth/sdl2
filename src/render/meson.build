all_sources += files(
  'SDL_d3dmath.c',
  'SDL_render.c',
  'SDL_yuv_sw.c',
)

if host_machine.system() == 'windows'
  subdir('direct3d')
  subdir('direct3d11')
elif host_machine.system() == 'darwin'
subdir('metal')
endif

subdir('opengl')
subdir('opengles')
subdir('opengles2')
subdir('psp')
subdir('software')
