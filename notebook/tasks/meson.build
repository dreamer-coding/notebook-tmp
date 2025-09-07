# Use wildcard.py to collect all test source files for the directory
tasks_cards = run_command(['python3', meson.source_root() / '..' / 'tools' / 'wildcard.py'], check: true)

# Split the stdout into a list of filenames
tasks_source = ['main.c'] + tasks_cards.stdout().strip().split('\n')

# Create executable for pizza tests
challenge = executable(
    'notebook',
    tasks_source,
    dependencies: [dependency('fossil-test')]
)

# Add test
test('tasks test cases', challenge)
