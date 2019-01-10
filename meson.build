project('sdl2', 'c',
  version : '2.0.9',
  license : 'zlib',
  default_options: ['c_std=gnu99']
)

varr = meson.project_version().split('.')
version_major = varr[0]
version_minor = varr[1]
version_micro = varr[2]

cc = meson.get_compiler('c')

core_deps = [
  cc.find_library('m',       required : false),
  cc.find_library('dl',      required : false),
  cc.find_library('pthread', required : false),
]

if host_machine.system() == 'darwin'
  add_languages('objc')
endif

cc = meson.get_compiler('c')
cdata = configuration_data()
check_headers = [
  ['HAVE_IMMINTRIN_H',      'immintrin'       ],
  ['HAVE_SYS_TYPES_H',      'sys/types.h'     ],
  ['HAVE_STDIO_H',          'stdio.h'         ],
  ['HAVE_STDLIB_H',         'stdlib.h'        ],
  ['HAVE_STDDEF_H',         'stddef.h'        ],
  ['HAVE_STDARG_H',         'stdarg.h'        ],
  ['HAVE_MALLOC_H',         'malloc.h'        ],
  ['HAVE_MEMORY_H',         'memory.h'        ],
  ['HAVE_STRING_H',         'string.h'        ],
  ['HAVE_LIMITS_H',         'limits.h'        ],
  ['HAVE_STRINGS_H',        'strings.h'       ],
  ['HAVE_WCHAR_H',          'wchar.h'         ],
  ['HAVE_INTTYPES_H',       'inttypes.h'      ],
  ['HAVE_STDINT_H',         'stdint.h'        ],
  ['HAVE_CTYPE_H',          'ctype.h'         ],
  ['HAVE_MATH_H',           'math.h'          ],
  ['HAVE_ICONV_H',          'iconv.h'         ],
  ['HAVE_SIGNAL_H',         'signal.h'        ],
  ['HAVE_LIBUNWIND_H',      'libunwind.h'     ],
  ['HAVE_ALLOCA_H',         'alloca.h'        ],
  ['HAVE_LIBUDEV_H',        'libudev.h'       ],
  ['HAVE_FCITX_FRONTEND_H', 'fcitx/frontend.h'],
  ['HAVE_LINUX_VERSION_H',  'linux/version.h' ],
  ['HAVE_XINPUT_H',         'xinput.h'        ],
  ['HAVE_D3D_H',            'd3d9.h'          ],
  ['HAVE_D3D11_H',          'd3d11_1.h'       ],
  ['HAVE_DDRAW_H',          'ddraw.h'         ],
  ['HAVE_DSOUND_H',         'dsound.h'        ],
  ['HAVE_DINPUT_H',         'dinput.h'        ],
  ['HAVE_DXGI_H',           'dxgi.h'          ],
  ['HAVE_MMDEVICEAPI_H',    'mmdeviceapi.h'   ],
  ['HAVE_AUDIOCLIENT_H',    'audioclient.h'   ],
  ['HAVE_ENDPOINTVOLUME_H', 'endpointvolume.h'],
]

foreach h : check_headers
  if cc.has_header(h.get(1))
    cdata.set(h.get(0), 1)
  endif
endforeach

check_functions = [
  ['HAVE_MALLOC',       'malloc',      '#include<stdlib.h>' ],
  ['HAVE_CALLOC',       'calloc',      '#include<stdlib.h>' ],
  ['HAVE_REALLOC',      'realloc',     '#include<stdlib.h>' ],
  ['HAVE_FREE',         'free',        '#include<stdlib.h>' ],
  ['HAVE_ALLOCA',       'alloca',      '#include<alloca.h>' ],
  ['HAVE_GETENV',       'getenv',      '#include<stdlib.h>' ],
  ['HAVE_SETENV',       'setenv',      '#include<stdlib.h>' ],
  ['HAVE_PUTENV',       'putenv',      '#include<stdlib.h>' ],
  ['HAVE_UNSETENV',     'unsetenv',    '#include<stdlib.h>' ],
  ['HAVE_QSORT',        'qsort',       '#include<stdlib.h>' ],
  ['HAVE_ABS',          'abs',         '#include<stdlib.h>' ],
  ['HAVE_BCOPY',        'bcopy',       '#include<strings.h>'],
  ['HAVE_MEMSET',       'memset',      '#include<string.h>' ],
  ['HAVE_MEMCPY',       'memcpy',      '#include<string.h>' ],
  ['HAVE_MEMMOVE',      'memmove',     '#include<string.h>' ],
  ['HAVE_MEMCMP',       'memcmp',      '#include<string.h>' ],
  ['HAVE_WCSLEN',       'wcslen',      '#include<wchar.h>'  ],
  ['HAVE_WCSLCPY',      'wcslcpy',     '#include<wchar.h>'  ],
  ['HAVE_WCSLCAT',      'wcslcat',     '#include<wchar.h>'  ],
  ['HAVE_WCSCMP',       'wcscmp',      '#include<wchar.h>'  ],
  ['HAVE_STRLEN',       'strlen',      '#include<string.h>' ],
  ['HAVE_STRLCPY',      'strlcpy',     '#include<string.h>' ],
  ['HAVE_STRLCAT',      'strlcat',     '#include<string.h>' ],
  ['HAVE__STRREV',      '_strrev',     '#include<string.h>' ],
  ['HAVE__STRUPR',      '_strupr',     '#include<string.h>' ],
  ['HAVE__STRLWR',      '_strlwr',     '#include<string.h>' ],
  ['HAVE_INDEX',        'index',       '#include<strings.h>'],
  ['HAVE_RINDEX',       'rindex',      '#include<strings.h>'],
  ['HAVE_STRCHR',       'strchr',      '#include<string.h>' ],
  ['HAVE_STRRCHR',      'strrchr',     '#include<string.h>' ],
  ['HAVE_STRSTR',       'strstr',      '#include<string.h>' ],
  ['HAVE_ITOA',         'itoa',        '#include<stdlib.h>' ],
  ['HAVE__LTOA',        '_ltoa',       '#include<stlib.h>'  ],
  ['HAVE__UITOA',       '_uitoa',      '#include<stdlib.h>' ],
  ['HAVE__ULTOA',       '_ultoa',      '#include<stdlib.h>' ],
  ['HAVE_STRTOL',       'strtol',      '#include<stdlib.h>' ],
  ['HAVE_STRTOUL',      'strtoul',     '#include<stdlib.h>' ],
  ['HAVE__I64TOA',      '_i64toa',     '#include<stdlib.h>' ],
  ['HAVE__UI64TOA',     '_uit64toa',   '#include<stdlib.h>' ],
  ['HAVE_STRTOLL',      'strtoll',     '#include<stdlib.h>' ],
  ['HAVE_STRTOULL',     'strtoull',    '#include<stdlib.h>' ],
  ['HAVE_STRTOD',       'strtod',      '#include<stdlib.h>' ],
  ['HAVE_ATOI',         'atoi',        '#include<stdlib.h>' ],
  ['HAVE_ATOF',         'atof',        '#include<stdlib.h>' ],
  ['HAVE_STRCMP',       'strcmp',      '#include<string.h>' ],
  ['HAVE_STRNCMP',      'strncmp',     '#include<string.h>' ],
  ['HAVE__STRICMP',     '_stricmp',    '#include<string.h>' ],
  ['HAVE_STRCASECMP',   'strcasecmp',  '#include<strings.h>'],
  ['HAVE__STRNICMP',    '_strnicmp',   '#include<string.h>' ],
  ['HAVE_STRNCASECMP',  'strncasecmp', '#include<strings.h>'],
  ['HAVE_VSSCANF',      'vsscanf',     '#include<stdio.h>'  ],
  ['HAVE_VSNPRINTF',    'vsnprintf',   '#include<stdio.h>'  ],
  ['HAVE_ACOS',         'acos',        '#include<math.h>'   ],
  ['HAVE_ACOSF',        'acosf',       '#include<math.h>'   ],
  ['HAVE_ASIN',         'asin',        '#include<math.h>'   ],
  ['HAVE_ASINF',        'asinf',       '#include<math.h>'   ],
  ['HAVE_ATAN',         'atan',        '#include<math.h>'   ],
  ['HAVE_ATANF',        'atanf',       '#include<math.h>'   ],
  ['HAVE_ATAN2',        'atan2',       '#include<math.h>'   ],
  ['HAVE_ATAN2F',       'atan2f',      '#include<math.h>'   ],
  ['HAVE_CEIL',         'ceil',        '#include<math.h>'   ],
  ['HAVE_CEILF',        'ceilf',       '#include<math.h>'   ],
  ['HAVE_COPYSIGN',     'copysign',    '#include<math.h>'   ],
  ['HAVE_COPYSIGNF',    'copysignf',   '#include<math.h>'   ],
  ['HAVE_COS',          'cos',         '#include<math.h>'   ],
  ['HAVE_COSF',         'cosf',        '#include<math.h>'   ],
  ['HAVE_EXP',          'exp',         '#include<math.h>'   ],
  ['HAVE_EXPF',         'expf',        '#include<math.h>'   ],
  ['HAVE_FABS',         'fabs',        '#include<math.h>'   ],
  ['HAVE_FABSF',        'fabsf',       '#include<math.h>'   ],
  ['HAVE_FLOOR',        'floor',       '#include<math.h>'   ],
  ['HAVE_FLOORF',       'floorf',      '#include<math.h>'   ],
  ['HAVE_FMOD',         'fmod',        '#include<math.h>'   ],
  ['HAVE_FMODF',        'fmodf',       '#include<math.h>'   ],
  ['HAVE_LOG',          'log',         '#include<math.h>'   ],
  ['HAVE_LOGF',         'logf',        '#include<math.h>'   ],
  ['HAVE_LOG10',        'log10',       '#include<math.h>'   ],
  ['HAVE_LOG10F',       'log10f',      '#include<math.h>'   ],
  ['HAVE_POW',          'pow',         '#include<math.h>'   ],
  ['HAVE_POWF',         'powf',        '#include<math.h>'   ],
  ['HAVE_SCALBN',       'scalbn',      '#include<math.h>'   ],
  ['HAVE_SCALBNF',      'scalbnf',     '#include<math.h>'   ],
  ['HAVE_SIN',          'sin',         '#include<math.h>'   ],
  ['HAVE_SINF',         'sinf',        '#include<math.h>'   ],
  ['HAVE_SQRT',         'sqrt',        '#include<math.h>'   ],
  ['HAVE_SQRTF',        'sqrtf',       '#include<math.h>'   ],
  ['HAVE_TAN',          'tan',         '#include<math.h>'   ],
  ['HAVE_TANF',         'tanf',        '#include<math.h>'   ],
  ['HAVE_FOPEN64',      'fopen64',     '#include<stdio.h>'  ],
  ['HAVE_FSEEKO',       'fseeko',      '#include<stdio.h>'  ],
  ['HAVE_FSEEKO64',     'fseeko64',    '#include<stdio.h>'  ],
  ['HAVE_SIGACTION',    'sigaction',   '#include<signal.h>' ],
# check token HAVE_SA_SIGACTION
  ['HAVE_SETJMP',        'setjmp',        '#include<setjmp.h>'    ],
  ['HAVE_NANOSLEEP',     'nanosleep',     '#include<time.h>'      ],
  ['HAVE_SYSCONF',       'sysconf',       '#include<unistd.h>'    ],
  ['HAVE_SYSCTLBYNAME',  'sysctlbyname',  '#include<sys/sysctl.h>'],
  ['HAVE_CLOCK_GETTIME', 'clock_gettime', '#include<time.h>'      ],
  ['HAVE_GETPAGESIZE',   'getpagesize',   '#include<unistd.h>'    ],
  ['HAVE_MPROTECT',      'mprotect',      '#include<sys/mman.h>'  ],
# check token HAVE_ICONV
  ['HAVE_PTHREAD_SETNAME_NP',  'pthread_setname_np',  '#include<pthread.h>'],
  ['HAVE_PTHREAD_SET_NAME_NP', 'pthread_set_name_np', '#include<pthread.h>'],
# check token HAVE_SEM_TIMEDWAIT
  ['HAVE_GETAUXVAL', 'getauxval', '#include<sys/auxv.h>'],
  ['HAVE_POLL',      'poll',      '#include<poll.h>'    ],
]

foreach f : check_functions
  if cc.has_function(f.get(1), prefix : f.get(2))
    cdata.set(f.get(0), 1)
  endif
endforeach

cdata.set('HAVE_LIBC', 1)
# TODO: Something with _USE_MATH_DEFINES
if cc.compiles('''#include<math.h>
double dummy = M_PI
''', name : 'M_PI')
  cdata.set('HAVE_M_PI', 1)
endif

# FIXME: Supposed to be windows and not MinGW but I dunno how to achieve that in Meson
if host_machine.system() == 'windows' and cc.get_id() == 'msvc'
  cdata.set('STDC_HEADERS', 1)
else
  stdc_headers = [
    'dlfcn.h', 'stdint.h', 'stddef.h', 'inttypes.h',
    'stdlib.h', 'strings.h', 'string.h', 'float.h',
  ]
  cdata.set('STDC_HEADERS', 1)
  foreach h : stdc_headers
    if not cc.has_header(h)
      cdata.set('STDC_HEADERS', 0)
    endif
  endforeach
endif

core_args = ['-DUSING_GENERATED_CONFIG_H']
core_ldflags = []

if host_machine.system() == 'linux'
  cdata.set('HAVE_GCC_ATOMICS',                                 1)
  cdata.set('HAVE_GCC_SYNC_LOCK_TEST_AND_SET',                  1)
  cdata.set('SDL_POWER_LINUX',                                  1)
  cdata.set('SDL_THREAD_PTHREAD',                               1)
  cdata.set('SDL_JOYSTICK_LINUX',                               1)
  cdata.set('SDL_INPUT_LINUXEV',                                1)
  cdata.set('SDL_INPUT_LINUXKD',                                1)
  cdata.set('SDL_HAPTIC_LINUX',                                 1)
  cdata.set('SDL_TIMER_UNIX',                                   1)
  cdata.set('SDL_FILESYSTEM_UNIX',                              1)
  cdata.set('SDL_DYNAMIC_API',                                  1)
  cdata.set('SDL_LOADSO_DLOPEN',                                1)
  cdata.set('SDL_VIDEO_DRIVER_X11',                             1)
  cdata.set('SDL_VIDEO_DRIVER_X11_DYNAMIC_XINPUT2',             1)
  cdata.set('SDL_VIDEO_DRIVER_X11_XINPUT2',                     1)
  cdata.set('SDL_VIDEO_DRIVER_X11_XINPUT2_SUPPORTS_MULTITOUCH', 1)
  cdata.set('SDL_VIDEO_DRIVER_X11_SUPPORTS_GENERIC_EVENTS',     1)
  cdata.set('SDL_SENSOR_DUMMY',                                 1)
  cdata.set('SDL_VIDEO_VULKAN',                                 1)
  # HAVE_VIDEO_VULKAN is set to TRUE in the CMake, but is never used
  core_args += ['-pthread']
elif host_machine.system() == 'windows'
  cdata.set('SDL_THREAD_WINDOWS',       1)
  cdata.set('SDL_JOYSTICK_DINPUT',      1)
  cdata.set('SDL_HAPTIC_DINPUT',        1)
  cdata.set('SDL_TIMER_WINDOWS',        1)
  cdata.set('SDL_FILESYSTEM_WINDOWS',   1)
  cdata.set('SDL_DYNAMIC_API',          1)
  cdata.set('SDL_HAPTIC_DINPUT',        1)
  cdata.set('SDL_POWER_WINDOWS',        1)
  cdata.set('SDL_LOADSO_WINDOWS',       1)
  cdata.set('SDL_VIDEO_DRIVER_WINDOWS', 1)
  cdata.set('SDL_VIDEO_RENDER_D3D',     1)
  cdata.set('SDL_AUDIO_DRIVER_WINMM',   1)
  cdata.set('SDL_SENSOR_DUMMY',         1)
  cdata.set('SDL_VIDEO_VULKAN',         1)
  core_deps += [
    cc.find_library('winmm'),
    cc.find_library('version'),
    cc.find_library('imm32'),
  ]
elif host_machine.system() == 'darwin'
  cdata.set('HAVE_GCC_ATOMICS',                1)
  cdata.set('HAVE_GCC_SYNC_LOCK_TEST_AND_SET', 1)
  cdata.set('SDL_POWER_MACOSX',                1)
  cdata.set('SDL_THREAD_PTHREAD',              1)
  cdata.set('SDL_JOYSTICK_IOKIT',              1)
  cdata.set('SDL_HAPTIC_IOKIT',                1)
  cdata.set('SDL_TIMER_UNIX',                  1)
  cdata.set('SDL_FILESYSTEM_UNIX',             1)
  cdata.set('SDL_DYNAMIC_API',                 1)
  cdata.set('SDL_LOADSO_DLOPEN',               1)
  cdata.set('SDL_VIDEO_DRIVER_COCOA',          1)
  cdata.set('SDL_AUDIO_DRIVER_COREAUDIO',      1)
  cdata.set('SDL_VIDEO_OPENGL_CGL',            1)
  cdata.set('SDL_SENSOR_DUMMY',                1)
  cdata.set('SDL_VIDEO_VULKAN',                0) # TODO: Implement Metal support (this relies on it)
  core_args += ['-pthread']
  core_deps += [dependency('appleframeworks',
    modules : ['CoreFoundation', 'Foundation',
     'QuartzCore', 'CoreAudio',
    'AudioUnit', 'AudioToolbox', 'ForceFeedback',
    'IOKit', 'Cocoa', 'Carbon', 'CoreGraphics'])]
else
  error('Unsupported platform.')
endif

core_inc = include_directories('.', 'include')
all_sources  = []
main_sources = []

alsa_dep     = dependency('alsa',     required : false)
x11_dep      = dependency('x11',      required : false)
xi_dep       = dependency('xi',       required : false)
xext_dep     = dependency('xext',     required : false)
gl_dep       = dependency('gl',       required : false)
vulkan_dep   = dependency('vulkan',   required : false)
xrandr_dep   = dependency('xrandr',   required : false)
xinerama_dep = dependency('xinerama', required : false)

if gl_dep.found()
  cdata.set('SDL_VIDEO_RENDER_OGL', 1)
endif

if x11_dep.found()
  if gl_dep.found()
    cdata.set('SDL_VIDEO_OPENGL_GLX', 1)
  endif
  if xrandr_dep.found()
    cdata.set('SDL_VIDEO_DRIVER_X11_DYNAMIC_XRANDR', 1)
#    cdata.set('SDL_VIDEO_DRIVER_X11_XRANDR', 1)
  endif
  if xinerama_dep.found()
    cdata.set('SDL_VIDEO_DRIVER_X11_XINERAMA', 1)
#    cdata.set('SDL_VIDEO_DRIVER_X11_DYNAMIC_XINERAMA', 1)
  endif
endif

if alsa_dep.found()
  cdata.set('SDL_AUDIO_DRIVER_ALSA', 1)
#  cdata.set('SDL_AUDIO_DRIVER_ALSA_DYNAMIC', 1)
endif

# The config file is at root because we want to
# ensure that it comes before the include subdir
# in search order and include also has a SDL_config.h.
configure_file(
  input : 'SDL_config.h.meson',
  output : 'SDL_config.h',
  configuration : cdata
)


subdir('src')
core_deps += [
  x11_dep, xi_dep, xrandr_dep, xext_dep,
  gl_dep, vulkan_dep, xinerama_dep, alsa_dep,
]

sdl2 = library('sdl2',
  all_sources,
  include_directories : core_inc,
  c_args              : core_args,
  link_args           : core_ldflags,
  dependencies        : core_deps,
)

sdl2main = static_library('sdl2main',
  main_sources,
  include_directories : core_inc,
  c_args : core_args,
)

sdl2_dep = declare_dependency(
  link_with : sdl2,
  include_directories : core_inc
)
sdl2main_dep = declare_dependency(
  link_with : sdl2main,
  include_directories : core_inc
)

# disabled for now
# subdir('test')
