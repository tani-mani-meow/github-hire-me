This is my first python automation script! It programmatically renders typography onto the GitHub contribution graph by generating commits at specific calendar dates.

## Implementation Details

The GitHub contribution graph is basically just a 7x52 matrix (7 days a week, 52 weeks a year). I mapped a 2D array to this coordinate system to draw the pattern.

### Core Mechanics

- **Grid Mapping:** I used a custom 2D bitmask for the layout. The script calculates the exact dates by taking the first Sunday of the year and adding `datetime.timedelta` offsets based on the grid coordinates.
- **Commit Automation:** I used the python `subprocess` module to run git commands. It schedules the commits by configuring the `GIT_AUTHOR_DATE` and `GIT_COMMITTER_DATE` environment variables to align with the calculated grid dates.
- **Density Control:** To make sure the text shows up distinctly on the github profile, the script generates 3-5 commits per coordinate so the squares get dark green.
