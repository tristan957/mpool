project(
	'mpool',
	'c',
	version: '1.8.0',
	license: [
		'Apache-2.0',
	],
	default_options: [
		'c_std=gnu99',
		'buildtype=debugoptimized',
		'warning_level=2',
	],
)

cc = meson.get_compiler('c')

version_components = meson.project_version().split('.')

mpool_major_version = version_components[0]
mpool_minor_version = version_components[1]
mpool_patch_version = version_components[2]

git_tag_command = run_command('git', 'describe', '--always', '--long', '--tags', '--dirty', '--abbrev=10', '2>/dev/null')
if git_tag_command.returncode() != 0
	build_tag = 'no-tag-found'
else
	build_tag = git_tag_command.stdout().strip()
endif

git_sha_command = run_command('git', 'rev-parse', 'HEAD', '2>/dev/null')
if git_sha_command.returncode() != 0
	build_sha = 'no-sha-found'
else
	build_sha = git_sha_command.stdout().strip()
endif

pkg = import('pkgconfig')

# TODO: Look into what options warning_level=3 provides and compare to add_compile_options in CMakelists.txt

if get_option('asan')
	add_project_arguments(
		'-fnoomit-frame-pointer',
		'-fsanitize=undefined',
		language: 'c'
	)
	add_project_link_argumnets(
		'-fsanitize=address',
	)
endif

if get_option('ubsan')
	add_project_arguments(
		'-fnoomit-frame-pointer',
		'-fsanitize=undefined',
		'-fno-sanitize=alignment',
		language: 'c'
	)
	add_project_link_argumnets(
		'-fsanitize=address',
	)
endif

uuid = dependency('uuid')
valgrind_dep = dependency('valgrind')
pthread_dep = cc.find_library('pthread')

public_includes = include_directories(
	'include',
)

subdir('include')
subdir('src')
subdir('test')
