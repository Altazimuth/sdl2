if host_machine.system() == 'linux'
  subdir('linux')
elif host_machine.system() == 'windows'
  subdir('windows')
endif

if host_machine.system() != 'windows'
  subdir('unix')
endif
