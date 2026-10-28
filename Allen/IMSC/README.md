## About

Five cells from the Allen Institute for Cell Science
[Integrated Mitotic Stem Cell](https://www.allencell.org/hips-cells-during-mitosis.html)
(IMSC) 3D viewer, one per mitotic stage: interphase, M1-M2, M3, M4-M5 and M6-M7.
Each cell is a volume-viewer atlas: a `<name>_atlas.json` sidecar plus the 11 PNG
tiles it lists in `images[]`. A cell is 256 x 256 x 58 voxels with 32 channels:
DNA plus 15 tagged structures (ACTB, LMNB1, TOMM20, ...), each as raw intensity
and as a segmentation, packed three channels per PNG.

The files are byte-for-byte copies of `https://imsc.allencell.org/assets/`,
which sends no CORS header, so browser demos cannot load them from the source.
The sidecars and PNGs are stored with Git LFS, so both resolve from the same
media URL (GitHub's raw endpoint would return LFS pointers for the PNGs).

## License

**Not BSD.** These files are Allen Institute for Cell Science Content, usable
for research and other noncommercial purposes with citation. Commercial use
needs written permission from the Allen Institute. See [LICENSE](LICENSE) and
the [Terms of Use](https://www.allencell.org/terms-of-use.html).

## Citation

Following the Allen Institute [Citation Policy](https://alleninstitute.org/legal/citation-policy):

 - The cell science accelerator at Allen Institute. Integrated Mitotic Stem Cell [dataset]. Available from imsc.allencell.org (accessed October 2026).

## Loading

Browser demos fetch the sidecars and tiles through GitHub's LFS media endpoint,
which serves CORS `*` and byte ranges:

```text
https://media.githubusercontent.com/media/niivue/niivue-demo-images-lfs/main/Allen/IMSC/COMP_crop_M1-M2_atlas.json
```

In NiiVue the sidecar loads like any volume; the Allen atlas reader resolves the
PNG names relative to the sidecar URL.
