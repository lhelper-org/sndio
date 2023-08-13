libsndio_srcs = [
    'debug.c', 'aucat.c', 'mio.c', 'mio_rmidi.c', 'mio_alsa.c', 'mio_aucat.c',
    'sio.c', 'sio_alsa.c', 'sio_aucat.c', 'sio_oss.c', 'sio_sun.c', 'sioctl.c',
    'sioctl_aucat.c', 'sioctl_sun.c'
]

libsndio = library('sndio', libsndio_srcs + bsd_compat_sources,
    dependencies: alsa_deps,
    c_args: libsndio_defs,
    include_directories: sndio_inc_dirs,
    install: true,
)

