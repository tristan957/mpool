mpool_sources = files(
	'dev_cntlr.c',
	'device_table.c',
	'discover.c',
	'logging.c',
	'mdc.c',
	'mlog.c',
	'mp.c',
	'mpctl.c',
	'mpool_err.c',
	'mpool_params.c',
	'omf.c',
	'pd.c',
	'sb.c',
)

mpool_includes = include_directories(
	'include',
)

mpool_dependencies = [
	valgrind_dep,
]

mpool = library(
	'mpool',
	mpool_sources + util_sources,
	version: meson.project_version(),
	include_directories: [
		public_includes,
		mpool_includes,
		util_includes,
	],
	install: true,
)

mpool_dep = declare_dependency(
	link_with: mpool,
	version: meson.project_version(),
	include_directories: public_includes,
)

pkg.generate(
	mpool,
	description: 'Mpool is a Linux loadable kernel module that implements an object storage device interface for SSDs and other solid-state storage.',
	filebase: 'mpool-@0@.@1@'.format(mpool_major_version, mpool_minor_version),
	name: 'mpool',
	version: meson.project_version(),
	url: 'https://github.com/hse-project/mpool',
)
