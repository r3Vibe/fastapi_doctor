# Changelog

All notable changes to this project will be documented in this file.

## [Unreleased]

### Changed
- **Package Rename**: Renamed package from `fastapi_hephaestus` to `fastapi_doctor`
  - CLI command changed from `hephaestus` to `doctor`
  - Module renamed from `hephaestus.py` to `doctor.py`
  - Updated all imports and references
  - Updated GitHub URLs and project metadata

## [1.7.0]

### Changed
- **Major Architecture Refactor**: Restructured monolithic `hephaestus.py` (955 lines) into a modular architecture
  - Extracted all templates into `templates/` module with 6 separate files:
    - `core_templates.py` - main.py, config.py, logging.py templates
    - `api_templates.py` - routes, routers, auth templates
    - `db_templates.py` - database session templates
    - `middleware_templates.py` - CORS middleware templates
    - `frontend_templates.py` - index.html, visual.py, root_route.py templates
    - `misc_templates.py` - .env, dev.py, lifespan templates
  - Created `generators/` module for project generation logic:
    - `FileWriter` class for file operations
    - `ProjectGenerator` class as the main orchestrator
  - Created `config/` module for project configuration:
    - Centralized database driver mappings
    - Directory structure configuration
    - Base dependencies list
  - Reduced CLI file to ~75 lines (thin layer)

### Fixed
- Fixed `UnicodeEncodeError` on Windows when creating project files containing Unicode characters (e.g., box-drawing characters in comments) by explicitly specifying `encoding="utf-8"` for all file write operations

### Changed
- Show help message by default when no command is provided instead of displaying "Missing command" error
- Show help message for subcommands (`new`, `add`) when required arguments are missing instead of displaying error box
