project('libpng', 'c', version: '1.6.40')

compiler = meson.get_compiler('c')
link_deps = [
    dependency('zlib'),
]

sources = [
    'arm/arm_init.c',
    'arm/filter_neon_intrinsics.c',
    'arm/palette_neon_intrinsics.c',
    'intel/filter_sse2_intrinsics.c',
    'intel/intel_init.c',
    'png.c',
    'pngerror.c',
    'pngget.c',
    'pngmem.c',
    'pngpread.c',
    'pngread.c',
    'pngrio.c',
    'pngrtran.c',
    'pngrutil.c',
    'pngset.c',
    'pngtrans.c',
    'pngwio.c',
    'pngwrite.c',
    'pngwtran.c',
    'pngwutil.c',
]

incdirs = ['.']

c_flags = []

if target_machine.cpu_family() == 'x86' or target_machine.cpu_family() == 'x86_64'
    c_flags += ['-DPNG_INTEL_SSE_OPT=1']
endif

incdirs = include_directories(incdirs)

libpng = static_library(
    'png',
    sources,
    c_args: c_flags,
    include_directories: incdirs,
    dependencies: link_deps,
)
libpng_dep = declare_dependency(
    include_directories: incdirs,
    dependencies: link_deps,
    link_with: libpng,
    version: meson.project_version()
)

meson.override_dependency('libpng', libpng_dep)

# vim: set ts=4 sts=4 sw=4 et:
