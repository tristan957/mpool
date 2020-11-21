cli_sources = files(
	'common.c',
	'ls.c',
	'mpool_ui.c',
	'mpool.c',
	'ui_common.c',
	'yaml.c',
)

cli_dependencies = [
	mpool_dep,
]

executable(
    'mpool',
    cli_sources,
    dependencies: cli_dependencies,
    install: true,
)
