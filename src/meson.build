phosh_tour_enum_sources = gnome.mkenums_simple('ms-enum-types',
     sources : files('phosh-config-enums.h'))

phosh_tour_sources = [
  'main.c',
  'phosh-tour-window.h',
  'phosh-tour-window.c',
  'phosh-tour-application.h',
  'phosh-tour-application.c',
  'pt-page.h',
  'pt-page.c',
  'pt-util.h',
  'pt-util.c',
  phosh_tour_enum_sources,
]

phosh_tour_deps = [
  gio_dep,
  glib_dep,
  gtk_dep,
  adwaita_dep,
]

gnome = import('gnome')

phosh_tour_sources += gnome.compile_resources('phosh-tour-resources',
  'phosh-tour.gresource.xml',
  c_name: 'phosh_tour'
)

executable('phosh-tour', phosh_tour_sources,
  dependencies: phosh_tour_deps,
  install: true,
)
