# Physics-Informed-Hybrid-Neural-Operator-for-Transient-Magnetization-Prediction

`PI-HNO_Official.ipynb` is the only training entry point. It contains the model,
energy-aware loss, training loop, and validation NRMSE diagnostic.

## Setup

```bash
conda env create -f environment.yml
conda activate PI-HNO-cu128
python -m ipykernel install --user --name PI-HNO-cu128
```
Open the notebook in VS Code with the Jupyter extension and select this kernel.

## Train

Supply `Dataset/<material>/<material>_Training_Full.h5` containing:

- `B_scal`: shape `[N, 1000]`, in tesla.
- `H_scal`: shape `[N, 1000]`, in A/m.
- `T_scal`: shape `[N, 1]`, in degrees Celsius.

Use at least two full sequences. In the first code cell, set `MATERIAL`
, `DATASET_ROOT`, `OUTPUT_DIR`, and `DEVICE`. Restart the kernel
and run all cells. Outputs are saved under `outputs/<material>/` by default;
choose a new output directory before another run.

For two GPUs, run separate notebook kernels with different materials and
set `DEVICE` to `cuda:0` and `cuda:1`, respectively.
