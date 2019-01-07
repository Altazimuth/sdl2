all_sources += files(
  'SDL_haptic.c',
)

if cdata.get('SDL_HAPTIC_LINUX', 0) == 1
  subdir('linux')
elif cdata.get('SDL_HAPTIC_DINPUT', 0) == 1
  subdir('windows')
elif cdata.get('SDL_HAPTIC_IOKIT', 0) == 1 # FIXME: dummy should be used for iOS
  subdir('darwin')
else
  subdir('dummy')
endif
