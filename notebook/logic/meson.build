# Use wildcard.py to collect all test source files for the directory
logic_cards = run_command(['python3', meson.source_root() / '..' / 'tools' / 'wildcard.py'], check: true)

# Split the stdout into a list of filenames
logic_source = ['main.c'] + logic_cards.stdout().strip().split('\n')

# Create executable for pizza tests
notebook = executable(
    'notebook',
    logic_source,
    include_directories: include_directories('.'),
    dependencies: [dependency('fossil-test')]
)

# Add test
test('notebook test cases', notebook)
