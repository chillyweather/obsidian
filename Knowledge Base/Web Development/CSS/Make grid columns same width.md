# Make grid columns same width

If you really need the columns to be the exact same width you should use:

grid-template-columns: repeat(3, minmax(0, 1fr));
minmax(0, 1fr) allows the grid tracks to be as small as 0 but as large as 1fr, creating columns that will stay equal.