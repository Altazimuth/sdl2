all_sources += files(
  'SDL_power.c',
)

if host_machine.system() == 'linux'
  subdir('linux')
elif host_machine.system() == 'windows'
  subdir('windows')
elif host_machine.system() == 'darwin'
  subdir('macosx')
elif host_machine.system() == 'haiku'
  subdir('haiku')
else
  error('Unsupported platform.')
endif
