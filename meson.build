project('sndio', 'c', version: '1.9.0', default_options: ['c_std=c99'])

cc = meson.get_compiler('c')

libsndio_defs = []
sndiod_user='_sndio'
if host_machine.system() == 'linux'
    libsndio_defs += ['-D_GNU_SOURCE', '-DHAVE_SOCK_CLOEXEC', '-DHAVE_CLOCK_GETTIME']
    sndiod_user='sndiod'
elif host_machine.system() == 'openbsd'
    libsndio_defs += ['-DHAVE_ARC4RANDOM', '-DHAVE_GETPEEREID', '-DHAVE_ISSETUGID', '-DHAVE_STRLCAT', '-DHAVE_STRLCPY', '-DHAVE_STRTONUM', '-DHAVE_SOCK_CLOEXEC', '-DHAVE_CLOCK_GETTIME']
    sndiod_user='_sndiop'
elif host_machine.system() == 'darwin'
    libsndio_defs += ['-DHAVE_ARC4RANDOM', '-DHAVE_GETPEEREID', '-DHAVE_ISSETUGID', '-DHAVE_STRLCAT', '-DHAVE_STRLCPY']
endif

# Always added in the original project. If not defined sndiod will not compile
# because of missing file_log function.
libsndio_defs += '-DDEBUG'

sndio_inc_dirs = include_directories('libsndio', 'bsd-compat')

# ALSA specific configuration
alsa_deps = []
if get_option('alsa')
    libsndio_defs += ['-DUSE_ALSA']
    libasound = cc.find_library('asound', required: true)
    alsa_deps += [ libasound ]
endif

if host_machine.system() == 'linux'
    alsa_deps += cc.find_library('rt', required: true)
endif

# rmidi and umidi specific configurations
if get_option('rmidi')
    libsndio_defs += ['-DUSE_RMIDI']
endif

if get_option('umidi')
    libsndio_defs += ['-DUSE_UMIDI']
endif

subdir('bsd-compat')
subdir('libsndio')
if get_option('sndiod')
    subdir('sndiod')
endif

pkg_gen = import('pkgconfig')

pkg_gen.generate(
    name : 'sndio',
    description : 'libsndio',
    version : '1.9.0',
    libraries : libsndio
)

