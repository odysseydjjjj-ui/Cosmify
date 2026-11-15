# Tests
The initial project includes the database and service seams needed for unit tests.
Add a test project targeting `net10.0` and cover:
- `LibraryService.ImportFilesAsync` (duplicate paths, unsupported extensions, metadata errors)
- SQLite persistence for tracks and playlists
- search across title, artist and album
- favorites and removal (verify original files are never deleted)

The current execution environment did not include the .NET SDK, so tests and compilation could not be run here.
