# Setup instructions

## Prerequisites

- WSL2 with Ubuntu 22.04+ (or any Linux/macOS)
- pixi (`curl -fsSL https://pixi.sh/install.sh | bash`)
- Git
- At least 16 GB RAM, ideally 32 GB
- 100 GB free disk space (for cutouts and intermediate files)

## Installation

### 1. Clone PyPSA-Eur as a sibling directory

```bash
cd ~/python   # or your preferred parent directory
git clone https://github.com/PyPSA/pypsa-eur.git
cd pypsa-eur
git checkout <PINNED_COMMIT_HASH_HERE>   # Replace with actual hash
pixi install
```

### 2. Clone pypsa-iberia

```bash
cd ~/python
git clone <YOUR_REPO_URL> pypsa-iberia
cd pypsa-iberia
```

### 3. Verify PyPSA-Eur works (tutorial)

```bash
cd ../pypsa-eur
pixi run snakemake -call results/test-elec/networks/base_s_6_elec_.nc \
    --configfile config/test/config.electricity.yaml
```

### 4. Run Iberian baseline (default clustering, ~3 hours first time)

```bash
cd ../pypsa-eur
pixi run snakemake -call solve_elec_networks \
    --configfile ../pypsa-iberia/config/config.yaml
```

Results land in `pypsa-eur/results/iberia-v0-default/`.

## Tested versions

- PyPSA-Eur: `<commit>`
- PyPSA: `<version>`
- HiGHS: `<version>`
