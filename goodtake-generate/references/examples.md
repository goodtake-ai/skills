# Generation Examples

## Product photography

```bash
gt generate image \
  --model gpt-image-2 \
  --prompt "studio product shot of a matte black water bottle on a white marble surface, soft shadows, commercial photography" \
  --aspect-ratio 1:1
```

## Social media (portrait)

```bash
gt generate image \
  --prompt "lifestyle photo, woman holding coffee cup in a sunlit café, warm tones" \
  --aspect-ratio 9:16
```

## Batch of variations

```bash
gt generate image \
  --model flux-pro \
  --prompt "minimalist logo concept for a tech startup, geometric shapes" \
  --param num_images=4 \
  --no-download
```

## Image-to-image (style transfer)

```bash
gt generate image \
  --prompt "in the style of a vintage travel poster, bold colors" \
  --reference https://example.com/my-photo.jpg
```

## Quick draft (fast model)

```bash
gt generate image \
  --model flux-schnell \
  --prompt "rough concept: futuristic city skyline at dusk"
```

## Download to specific path

```bash
gt generate image \
  --prompt "hero banner background, abstract gradient, blue and purple" \
  --aspect-ratio 16:9 \
  --output ./assets/hero-bg.png
```
