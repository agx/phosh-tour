phosh_tour_enum_sources = gnome.mkenums_simple(
  'ms-enum-types',
  sources: files('phosh-config-enums.h'),
)

phosh_tour_sources = [
  'main.c',
  'pt-application.h',
  'pt-application.c',
  'pt-window.h',
  'pt-window.c',
  'pt-page.h',
  'pt-page.c',
  'pt-hw-page.h',
  'pt-hw-page.c',
]

phosh_tour_deps = [gio_dep, glib_dep, gmobile_dep, gtk_dep, adwaita_dep]

gnome = import('gnome')

phosh_tour_sources += gnome.compile_resources(
  'phosh-tour-resources',
  'phosh-tour.gresource.xml',
  c_name: 'phosh_tour',
)

executable('phosh-tour', phosh_tour_sources, dependencies: phosh_tour_deps, install: true)
