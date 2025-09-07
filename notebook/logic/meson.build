# Collect all source files using wildcard.py
logic_cards = run_command(
    ['python3', meson.source_root() / '..' / 'tools' / 'wildcard.py'],
    check: true
)

# Split stdout into a list of filenames
logic_source = logic_cards.stdout().strip().split('\n')

# Filter only .c, .cpp, .m, .mm files
logic_source = [f for f in logic_source if f.endswith(('.c', '.cpp', '.m', '.mm'))]

# Create an executable for each source file
foreach src : logic_source
    exe_name = files(src).name().replace(files(src).extension(), '')  # filename without extension
    executable(
        exe_name,
        src,
        dependencies: [dependency('fossil-io')]
    )
endforeach