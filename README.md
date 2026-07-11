# my-sparkrun

Personal [sparkrun](https://github.com/spark-arena/recipe-registry) recipe registry for NVIDIA DGX Spark inference workloads.

## Structure

- `recipes/` — recipe YAML files (one per model/config)
- `.sparkrun/registry.yaml` — manifest read by `sparkrun registry add`

## Adding a recipe

Copy an existing file in `recipes/` as a starting point and adjust `model`, `container`,
`defaults`, and `command`. See the sparkrun registry skill for the full recipe format.

Validate before committing:

```bash
sparkrun recipe validate <recipe-name>
sparkrun recipe vram <recipe-name>
```

Give each recipe file a unique name across the sparkrun ecosystem — `sparkrun list`
dedupes by filename stem, first-registry-wins, so a name collision with another
registry's recipe (e.g. the built-in `official`/`sparkrun-transitional` ones) will
silently hide yours from listings even though `recipe show`/`recipe search` still
find it.

## Registering this repo

```bash
sparkrun registry add /home/diego/Documents/vscode/my-sparkrun
```

After pushing to a remote, use the remote URL instead so it can be updated with
`sparkrun registry update`.
