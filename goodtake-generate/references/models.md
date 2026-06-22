# Goodtake Image Models

Run `gt models list --type image` for the live list with costs. This file contains commonly used identifiers and their supported params.

## Listing models

```bash
gt models list --type image
```

Output columns: identifier, name, cost per generation.

## Common models

| Identifier | Provider | Strengths |
|---|---|---|
| `gpt-image-2` | OpenAI | Text in images, coherent compositions, instruction-following |
| `flux-pro` | Black Forest Labs | Photorealistic, high detail |
| `flux-schnell` | Black Forest Labs | Fast, lower cost drafts |
| `imagen-4` | Google | High fidelity, artistic styles |

## Common params

Not all params apply to all models. The server returns a list of supported keys if you pass an unknown one.

| Param | Type | Example | Notes |
|---|---|---|---|
| `num_images` | int | `--param num_images=4` | Batch size; model-specific max |
| `quality` | string | `--param quality=high` | `standard` or `high` |
| `style` | string | `--param style=vivid` | `vivid` or `natural` (gpt-image-2) |
| `aspect_ratio` | string | `--aspect-ratio 16:9` | Sugar for `--param aspect_ratio=...` |

## Aspect ratios

Common values: `1:1`, `4:3`, `3:4`, `16:9`, `9:16`, `2:3`, `3:2`. Availability varies by model.
