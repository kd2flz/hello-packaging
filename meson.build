# project name and programming language
project ('com.github.kd2flz.hello-packaging', 'vala', 'c')
# Include the translations module
i18n = import('i18n')

# Set our translation domain
add_global_arguments('-DGETTEXT_PACKAGE="@0@"'.format (meson.project_name()), language:'c')

#Create a new executable, list the files we want to compile, list the dependencies we need.
executable(
    meson.project_name(),
    'src'/ 'Application.vala',
    dependencies: [
        dependency('gtk+-3.0')
    ],
    install: true
)

#Translate and install our .desktop file
i18n.merge_file(
    input: 'data' / 'hello-packaging.desktop.in',
    output: meson.project_name() + '.desktop',
    po_dir: meson.source_root() / 'po',
    type: 'desktop',
    install: true,
    install_dir: get_option('datadir') / 'applications'
)

#Translate and install our .appdata file
i18n.merge_file(
    input: 'data' / 'hello-packaging.appdata.xml.in',
    output: meson.project_name() + '.appdata.xml',
    po_dir: meson.source_root() / 'po',
    install: true,
    install_dir: get_option('datadir') / 'metainfo'
)

subdir('po')

#Install our icons in all the required size
icon_sizes = ['16', '24', '32', '48', '64', '128']

foreach i : icon_sizes
    install_data(
        'data' / i + '.svg',
        install_dir: get_option('datadir') / 'icons' / 'hicolor' / i + 'x' + i / 'apps',
        rename: meson.project_name() + '.svg'
    )
    install_data(
        'data' / i + '.svg',
        install_dir: get_option('datadir')/ 'icons'/ 'hicolor' / i + 'x' + '@2' / 'apps',
        rename: meson.project_name() + '.svg'
    )
endforeach