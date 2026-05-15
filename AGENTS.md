# AGENTS.md

## Purpose
These instructions help AI coding agents quickly understand and contribute to the `laboratorio-copilot` repository.

## Project overview
- Python web app built with FastAPI, Jinja2 templates, and HTMX.
- The app is a social bingo experience called `Soc Ops`.
- No database or external services; state is stored in-memory for each session.

## Key files
- `app/main.py` - FastAPI routes and app startup configuration.
- `app/game_logic.py` - bingo board generation and winning-line logic.
- `app/game_service.py` - in-memory session state and game event handling.
- `app/data.py` - bingo question strings and free-space label.
- `app/templates/` - Jinja2 templates, including HTMX-enabled UI components.
- `tests/test_api.py` - route/UI behavior tests.
- `tests/test_game_logic.py` - core bingo logic tests.

## Development commands
- `uv sync` - install/sync dependencies.
- `uv run pytest` - run test suite.
- `uv run uvicorn app.main:app --reload --host 0.0.0.0 --port 8000` - start the dev server.
- `uv run ruff check .` - run lint checks.

## Coding guidance
- Keep UI text and tests aligned when updating templates.
- HTMX partial render responses are returned from template fragments in `app/templates/components/`.
- `GameSession` state is keyed by `session_id` and lives in `_sessions` inside `app/game_service.py`.
- `FREE_SPACE` in `app/data.py` is used in the center bingo square and expected by templates/tests.

## Notes
- The repository also contains `workshop/` docs and `.solutions/` example branches; focus changes on the root project files.
- The app targets Python `>=3.13`.
- Use the root `README.md` and `workshop/` docs for larger context when needed.
