---
version: 0.1.0
name: goodtake-generate
description: |
  Generate images using the Goodtake (gt) CLI. Supports text-to-image,
  image-to-image editing with reference URLs, model selection, aspect ratios,
  and model-specific parameters (quality, style, num_images, etc.).
  Use when: "generate an image", "create an image with goodtake",
  "use gt to make", "make an image of", "generate with flux",
  "generate with gpt-image", "goodtake generate".
  NOT for: video generation, text generation, 3D modeling, audio.
argument-hint: "<prompt> [--model <name>] [--aspect-ratio <ratio>] [--param key=value]"
allowed-tools: Bash
---

# Goodtake Image Generation

Generate images via the Goodtake CLI (`gt`).

## Step 0 — Bootstrap

Check if `gt` is installed and authenticated before generating:

```bash
which gt 2>/dev/null || echo "NOT_INSTALLED"
gt auth status 2>/dev/null || echo "NOT_AUTHENTICATED"
```

If not installed:
```bash
npm install -g @goodtake/cli
```

If not authenticated:
```bash
gt auth login
```

After login, confirm balance:
```bash
gt account balance
```

## UX Rules

1. **Be concise.** Print the image path or URL on success. Do not narrate every step.
2. **Default model.** If the user did not specify a model, omit `--model` — the server picks a sensible default (typically `gpt-image-2`).
3. **Detect language.** Reply in the user's language; CLI flags stay English.
4. **One question at a time.** If clarification is needed, ask the single most important question.
5. **Don't estimate cost.** The CLI prints actual credits used after generation.
6. **Prefer `--no-download`** when the user only wants the URL (e.g. to embed elsewhere). Default is to download.

## Generation Workflow

```bash
gt generate image --prompt "<prompt>" [--model <identifier>] [--aspect-ratio <ratio>] [--param key=value ...]
```

**Examples:**

```bash
# Basic text-to-image (default model)
gt generate image --prompt "a cinematic sunset over mountains, golden hour"

# Specific model + aspect ratio
gt generate image --model gpt-image-2 --prompt "product shot of white sneakers on marble" --aspect-ratio 1:1

# Multiple images
gt generate image --prompt "abstract watercolor" --model flux-pro --param num_images=4

# Image-to-image (reference must be a hosted URL)
gt generate image --prompt "in watercolor style" --reference https://example.com/photo.jpg

# Print URL only, no download
gt generate image --prompt "logo concept" --no-download
```

## Model Selection

Run `gt models list --type image` to see all enabled models. Pass the identifier directly:

| Common identifiers | Good for |
|---|---|
| `gpt-image-2` | Detailed images, text in images |
| `flux-pro` | Photorealistic, high quality |
| `flux-schnell` | Fast drafts |
| `imagen-4` | Google's flagship |

Model names are fuzzy-matched — `gt generate image --model flux` will resolve to the best flux match.

## Parameters

Pass model-specific options with `--param key=value` (repeatable):

```bash
--param quality=high
--param num_images=2
--param style=vivid
```

Valid keys depend on the model. Unknown keys are rejected by the server with a list of supported keys.

## Error Handling

| Error | Fix |
|---|---|
| `Not authenticated` | Run `gt auth login` |
| `Insufficient credits` | Run `gt account topup` |
| `unknown or disabled model_identifier` | Run `gt models list --type image` and pick a valid identifier |
| `unsupported param` | Server lists supported params in the error — retry with valid keys |
| `image_urls may not reference internal addresses` | Reference images must be publicly hosted URLs |

## References

- [Available models and params](references/models.md)
- [More examples](references/examples.md)
