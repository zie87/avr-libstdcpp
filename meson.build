project('avr-libstdcpp', ['c', 'cpp'], version: '0.0.1', license: 'MPL-2.0', default_options: ['cpp_std=c++17'])

avr_libstdcpp_private_cpp_args = []
avr_libstdcpp_interface_cpp_args = []

avr_libstdcpp_lib = library(
  'avr-libstdcpp',
  'src/functexcept.cc',
  'src/hash_bytes.cc',
  'src/hashtable_c++0x.cc',
  'src/limits.cc',
  'src/list.cc',
  'src/math.cc',
  'src/new_handler.cc',
  'src/tree.cc',
  cpp_args: avr_libstdcpp_private_cpp_args,
  include_directories: 'include',
  install: true,
)

install_subdir('include',
  strip_directory: true,
  install_dir: get_option('includedir'),
)

avr_libstdcpp_dep = declare_dependency(
  include_directories: 'include',
  compile_args: avr_libstdcpp_interface_cpp_args,
  link_with: avr_libstdcpp_lib,
)

if meson.version().version_compare('>=0.54.0')
  meson.override_dependency('avr_libstdcpp', avr_libstdcpp_dep)
endif

avr_libstdcpp_header_only_dep = declare_dependency(
  include_directories: 'include',
)

pkg_mod = import('pkgconfig')
pkg_mod.generate(avr_libstdcpp_lib,
  name: 'avr_libstdcpp',
  filebase: 'avr_libstdcpp',
)
