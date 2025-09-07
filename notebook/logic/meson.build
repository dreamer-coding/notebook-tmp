# Collect all source files using wildcard.py
logic_cards = run_command(
    ['python3', meson.source_root() / '..' / 'tools' / 'wildcard.py'],
    check: true
)

# Split stdout into a list of filenames
logic_source = [logic_cards.stdout().strip().split('\n')]

# Filter only supported extensions
logic_source = [f for f in logic_source if f.endswith(('.c', '.cpp', '.m', '.mm'))]

# Function to get suffix based on extension
suffix_map = {
    '.c': '_c',
    '.cpp': '_cpp',
    '.m': '_objc',
    '.mm': '_objcpp'
}

# Create an executable for each source file
foreach src : logic_source
    file_obj = files(src)
    base_name = file_obj.name().replace(file_obj.extension(), '')
    exe_name = base_name + suffix_map[file_obj.extension()]
    
    executable(
        exe_name,
        src,
        dependencies: [dependency('fossil-io')]
    )
endforeach