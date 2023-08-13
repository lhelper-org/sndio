sndiod_srcs = [
    'abuf.c', 'dev.c', 'dev_sioctl.c', 'dsp.c', 'file.c', 'listen.c',
    'midi.c', 'miofile.c', 'opt.c', 'siofile.c', 'sndiod.c', 'sock.c', 'utils.c'
]

sndiod_defs = ['-DSNDIO_USER="' + sndiod_user + '"', '-DDEFAULT_BITS=' + get_option('precision')]

executable('sndiod', sndiod_srcs,
    dependencies: alsa_deps,
    include_directories: sndio_inc_dirs,
    c_args: libsndio_defs + sndiod_defs,
    link_with: libsndio,
    install: true,
)

