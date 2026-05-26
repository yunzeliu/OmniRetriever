# OmniRetriever Project Page

Static HTML project page for the paper *OmniRetriever: Any-to-Any Audio-Video-Text Retrieval via Fusion-as-Teacher Distillation*.

All files live at the root — no nested folders. Just drop the directory contents into a GitHub Pages repo and it works.

## Files

```
project_page/
├── index.html                # main page
├── style.css                 # custom styles on top of Bulma
├── teaser.png                # rendered from Teaser_OmniRetriever.pdf
├── method.png                # rendered from OmniRetriever_method.pdf
├── bench_samples_grid.jpg    # bench sample cards
└── README.md                 # this file
```

## Deploy on GitHub Pages

### Option A — dedicated project-page repo (recommended)
```
# create a new public repo, e.g. omniretriever-page, then:
cp -r project_page/* /path/to/omniretriever-page/
cd /path/to/omniretriever-page
git init && git add . && git commit -m "init project page"
git branch -M main
git remote add origin git@github.com:<org>/omniretriever-page.git
git push -u origin main
```
On GitHub: **Settings → Pages → Source = Deploy from a branch → main / (root) → Save**.
Live at `https://<org>.github.io/omniretriever-page/`.

### Option B — `/docs` folder of an existing repo
```
cp -r project_page/* /path/to/OmniRetriever/docs/
```
**Settings → Pages → Source = main / /docs → Save**.

### Option C — `gh-pages` branch
```
git checkout --orphan gh-pages
cp -r project_page/* .
git add . && git commit -m "project page"
git push origin gh-pages
```

## Before going live, replace placeholders in `index.html`

| Button | Link to point at |
| --- | --- |
| **Paper** | PDF on your release (e.g. `paper.pdf` next to `index.html`, or arXiv PDF URL) |
| **arXiv** | `https://arxiv.org/abs/XXXX.XXXXX` |
| **Code** | `https://github.com/<org>/OmniRetriever` |
| **Model** | `https://huggingface.co/<org>/OmniRetriever-7B` |
| **OmniRetriever-Bench** | `https://huggingface.co/datasets/<org>/OmniRetriever-Bench` |

Update the BibTeX `journal` / `year` / cite key once you have the arXiv ID or venue.

## Local preview

```
cd project_page
python -m http.server 8000
# open http://localhost:8000
```

## Regenerating images

If you update the source figures in `paper_acl/image/`, re-render the PNGs from this directory:

```
pdftoppm -png -r 150 ../image/Teaser_OmniRetriever.pdf teaser
pdftoppm -png -r 150 ../image/OmniRetriever_method.pdf method
mv teaser-1.png teaser.png && mv method-1.png method.png
```

## ⚠️ Anonymity reminder

During ARR / EMNLP review, do **not** publish this page under your real names — it would deanonymize the submission. Host it only after the review period ends.
