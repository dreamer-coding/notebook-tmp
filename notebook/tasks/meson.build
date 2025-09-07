# Collect all test source files using wildcard.py
tasks_cards = run_command(
    ['python3', meson.project_source_root() / '..' / 'tools' / 'wildcard.py'],
    check: true
)
run_command(
    ['python3', meson.project_source_root() / '..' / 'tools' / 'runner.py'],
    check: true
)

# Split stdout into a list of filenames and include main.c
tasks_source = ['main.c'] + tasks_cards.stdout().strip().split('\n')

# Filter only supported extensions
tasks_source = [f for f in tasks_source if f.endswith(('.c', '.cpp', '.m', '.mm'))]

# Single executable with all sources
challenge = executable(
    'notebook',
    tasks_source,
    dependencies: [dependency('fossil-test')]
)

# Add test
test('tasks test cases', challenge)