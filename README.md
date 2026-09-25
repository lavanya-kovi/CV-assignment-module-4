---
Title: CSc 8830 Computer Vision
---

# CSc 8830 · Computer Vision — assignment portal

One public web app for every assignment. Each module is a page in the sidebar.

- **Live demo:** https://cv-assignments-7a1l.onrender.com

## Run locally

```bash
pip install -r requirements.txt
streamlit run Home.py
```

## Modules on the site

| Page | Assignment | Original repo |
|---|---|---|
| Module 2 | Camera calibration and real-world object measurement | [cv-module2-calibration](https://github.com/lavanya-kovi/cv-module2-calibration) |
| Module 3 | Image blurring: spatial vs frequency-domain filtering | [cv-week-3-image-blur-fourier](https://github.com/lavanya-kovi/cv-week-3-image-blur-fourier) |
| Module 4 | Human boundary segmentation (RGB + thermal) vs SAM2 | this repo |

The Module 2 and 3 pages are those repos' Streamlit apps with their logic unchanged. The Module 2 page also offers bundled sample data:

- the 14 checkerboard photos and 20 object photos, downscaled by 1/3 (`samples/m2/`);
- the saved calibration, plus a copy scaled to the downscaled photos (`assets/m2/`);
- the 20-object `results.csv`, for Step 3.

## Repository layout

```
Home.py                               landing page
pages/2_Module_2_Camera_Calibration.py Module 2 web demo
pages/3_Module_3_Fourier_Blur.py      Module 3 web demo
pages/4_Module_4_Human_Segmentation.py Module 4 web demo
```
### Command-line use

```bash
python modules/m4_segmentation.py rgb samples/rgb/astronaut.png --rect 20 0 350 511 --sam2 assets/sam2_masks/astronaut.png
python modules/m4_segmentation.py thermal samples/thermal/person.jpg --sam2 assets/sam2_masks/person.png
```

### Adding SAM2 masks

1. Put the images in `samples/rgb` and `samples/thermal`, and add one box per person to `tools/sam2_boxes.json`.
2. Run `tools/sam2_generate_masks.py` in Colab. Instructions are at the top of that file.
3. Commit the resulting `assets/sam2_masks/*.png`.
   Use an access token with *write* scope as the password.
3. Push to GitHub as well, with `git push origin main`, so graders can read the code.

## Credits

The sample RGB image `astronaut.png` is the NASA public-domain portrait of Eileen Collins, as distributed with scikit-image.
