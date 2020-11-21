mpool_version_data = configuration_data({
    'build_version': meson.project_version(),
	'build_tag': build_tag,
	'build_sha': build_sha,
})

mpool_version = configure_file(
	input: 'mpool_version.h.in',
	output: 'mpool_version.h',
	configuration: mpool_version_data
)

install_headers(mpool_version)

subdir('mpool')
