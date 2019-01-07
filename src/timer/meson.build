all_sources += files(
  'SDL_timer.c',
)

if host_machine.system() == 'windows'
  subdir('windows')
elif host_machine.system() == 'haiku'
  subdir('haiku')
else
  subdir('unix')
endif
#subdir('dummy')
#subdir('psp')

