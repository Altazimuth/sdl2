all_sources += files(
  'SDL_d3dmath.c',
  'SDL_render.c',
  'SDL_yuv_sw.c',
)

subdir('direct3d')
subdir('direct3d11')
if cdata.get('SDL_VIDEO_RENDER_METAL', 0) == 1
  subdir('metal')
endif
subdir('opengl')
subdir('opengles')
subdir('opengles2')
subdir('psp')
subdir('software')
