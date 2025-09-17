# Chest X-ray Pneumonia Assignment

This notebook is designed to run **on Google Colab** (recommended) or **locally** with identical behaviour.  
All environment setup is fully automated in Sections 0.1–0.5.

---

## How to run

1. **Open the notebook** in either Jupyter or Google Colab.
2. **Run all cells in order**:
   - **0.1 Runtime and working directory**: sets the project and data paths.
   - **0.2 Dependencies**: installs required Python packages from `requirements.txt`.
   - **0.3 Imports**: loads libraries and fixes random seeds.
   - **0.4 Optional GPU configurations**: enables GPU optimisations if available.
   - **0.5 Data download**: downloads and prepares the dataset (train/val/test) into the data folder.
3. Continue with the later sections of the notebook for training, evaluation, and analysis.

---

## Environment setup files

Different environments require slightly different dependency files:

| Environment | Requirements file(s) | Notes |
|-------------|----------------------|-------|
| **Google Colab (recommended)** | `requirements.txt` | Place the project in **Google Drive → `content/code/cxr_assignment/`**. Open the notebook in Colab, mount Drive, then run Sections 0.1–0.5. Colab already ships PyTorch; this installs the remaining libraries. |
| **Local (VS Code + venv)** | `requirements-local.txt` (extends base with kernel, PyTorch, NumPy pin) | Use Python **3.10–3.12** (avoid 3.13+ until PyTorch support lands). In VS Code: **Python: Select Interpreter → Create Environment (venv)** → pick Py 3.10–3.12 → install from `requirements-local.txt`. |
| **Conda (optional)** | `environment.yml` | Mirrors the local venv setup for users who prefer conda. Create with: ```bash\nconda env create -f environment.yml && conda activate cxr\n``` |

👉 **Grading note**: For reproducibility and easiest setup, please use the **Google Colab workflow**.

---

## Notes for reproducibility

- Place the project under:  
  ```
  Google Drive → content/code/cxr_assignment/
  ```
  (to match the expected paths in Section 0.1).
- The notebook automatically handles both Colab and local paths.  
- The dataset is downloaded from [Kaggle](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia).  
- All random seeds are fixed; PyTorch is set to deterministic mode for consistent results.  
- To override the project root manually:
  ```bash
  export CXR_PROJ_ROOT=/path/to/your/project
  ```
- The repository is shipped with a `checkpoints/` folder containing the saved final state of the chosen model.  
  This means rerunning **Block 1.3.6 (training)** is not required for the rest of the analysis,  
  but it can still be executed for verification and will reproduce the same results.

---

## Troubleshooting

**Kernel issues (local VS Code)**
- Ensure you selected **Python 3.10–3.12** and a venv (not system Python).
- Install local deps:
  ```bash
  python -m pip install -r requirements-local.txt
  python -m ipykernel install --user --name cxr-venv
  ```

**NumPy 2.x error**
- Local envs pin `numpy<2`. If you still see errors, reinstall:
  ```bash
  python -m pip install "numpy<2"
  ```

**CUDA / GPU**
- This repo targets CPU or Apple Silicon (MPS) out of the box.  
- For CUDA-enabled PyTorch, create the env and then upgrade Torch following the [PyTorch website](https://pytorch.org/get-started/locally/).


## Viewing the final visualisations

If an HTML export ever shows a banner like **“Output hidden; open in Colab to view.”** for the last cell, please open the saved static images here:

`figures/final_visualizations_*.png`

These PNGs are written by the notebook during the final visualisation cell and match the plots exactly (no interactivity required).
