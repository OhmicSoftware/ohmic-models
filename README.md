# Ohmic Models

Community-maintained model registry for [Ohmic](https://github.com/OhmicSoftware), an AI-assisted music production tool for Ableton Live.

The Ohmic app fetches `models.json` on startup to get the latest available LLM models. This lets us update the model list without releasing a new version of the app.

## How it works

- Ohmic fetches this file on launch
- If the fetch fails (offline, GitHub down, etc.), the app falls back to its built-in model list
- Models are grouped by provider (`gemini`, `anthropic`)
- Each provider has a `default` model and a list of available `models`

## Contributing

Know about a new model that should be added? Open a PR!

1. Edit `models.json`
2. Add the model ID to the appropriate provider's `models` array
3. Submit a pull request with the model name and a link to its documentation

### Format

```json
{
  "version": 1,
  "providers": {
    "provider_name": {
      "default": "recommended-model-id",
      "models": [
        "model-id-1",
        "model-id-2"
      ]
    }
  }
}
```

### Guidelines

- Use the exact model ID as accepted by the provider's API
- Order models from most capable to most affordable
- Only add models that support text generation (no image-only, audio-only, or embedding models)
- Test that the model ID works before submitting

## License

This repository is public domain. The model list is factual information (API model identifiers) and is not copyrightable.
