desktop_conf = configuration_data()
desktop_conf.set('BRAND', get_option('brand'))

desktop_file = i18n.merge_file(
  input: configure_file(
    input: files('mobi.phosh.PhoshTour.desktop.in.in'),
    output: 'mobi.phosh.Phosh.desktop.in',
    configuration: desktop_conf,
  ),
  output: 'mobi.phosh.PhoshTour.desktop',
  type: 'desktop',
  po_dir: '../po',
  install: true,
  install_dir: join_paths(get_option('datadir'), 'applications'),
)

desktop_file = i18n.merge_file(
  input: configure_file(
    input: files('mobi.phosh.PhoshTour-first-login.desktop.in.in'),
    output: 'mobi.phosh.PhoshTour-first-login.desktop.in',
    configuration: desktop_conf,
  ),
  output: 'mobi.phosh.PhoshTour-first-login.desktop',
  type: 'desktop',
  po_dir: '../po',
  install: true,
  install_dir: get_option('sysconfdir') / 'xdg' / 'autostart',
)

appstream_file = i18n.merge_file(
  input: configure_file(
    input: files('mobi.phosh.PhoshTour.metainfo.xml.in.in'),
    output: 'mobi.phosh.PhoshTour.metainfo.xml.in',
    configuration: desktop_conf,
  ),
  output: 'mobi.phosh.PhoshTour.metainfo.xml',
  po_dir: '../po',
  install: true,
  install_dir: join_paths(get_option('datadir'), 'metainfo'),
)

appstream_util = find_program('appstreamcli', required: false)
if appstream_util.found()
  test('Validate appstream file', appstream_util, args: ['validate', '--no-net', appstream_file])
endif

install_data(
  'mobi.phosh.PhoshTour.gschema.xml',
  install_dir: join_paths(get_option('datadir'), 'glib-2.0/schemas'),
)

compile_schemas = find_program('glib-compile-schemas', required: false)
if compile_schemas.found()
  test(
    'Validate schema file',
    compile_schemas,
    args: ['--strict', '--dry-run', meson.current_source_dir()],
  )
endif

systemd_unit_conf = configuration_data()
systemd_unit_conf.set('BRAND', get_option('brand'))

systemd_unit = configure_file(
  input: 'mobi.phosh.PhoshTour-first-login.service.in',
  output: 'mobi.phosh.PhoshTour-first-login.service',
  configuration: systemd_unit_conf,
  install: true,
  install_dir: get_option('prefix') / 'lib' / 'systemd' / 'user',
)

subdir('icons')
