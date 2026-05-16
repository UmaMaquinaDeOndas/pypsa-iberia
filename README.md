# PyPSA-Iberia: Power System Model of the Iberian Peninsula with Focus on Sines

A PyPSA-Eur–based capacity expansion model of Portugal and Spain, with detailed
representation of the Sines region for studying large data center load scenarios.

## Model overview

- **Spatial scope:** Portugal (6 nodes), Spain (2 nodes), France (1 node),
  plus Germany, Italy, Belgium, GB, Switzerland (1 node each) as boundary regions
- **Temporal scope:** Hourly resolution; planning horizons 2025, 2030, 2035, 2040, 2050
- **Foresight:** Myopic
- **Solver:** HiGHS (default) or Gurobi (with academic license)
- **Built on:** PyPSA-Eur (commit pinned in `config/config.yaml`)

## Portuguese node structure

| Node      | Location           | Role                                    |
|-----------|--------------------|-----------------------------------------|
| PT_N      | Porto / Douro      | Hydro cascade, northern onshore wind    |
| PT_C      | Coimbra            | Mixed generation, central transit       |
| PT_LIS    | Lisbon / Tagus     | Main load center, Ribatejo CCGT         |
| PT_ALT    | Évora / Alentejo   | Utility solar, Alqueva hydro            |
| PT_SINES  | Sines              | Data center load, offshore wind, H2 hub |
| PT_ALG    | Faro / Algarve     | Southern solar, ES-S corridor           |

## Quick start

Requires PyPSA-Eur installed in a sibling directory (see Setup below).

```bash
cd ../pypsa-eur
pixi run snakemake -call solve_elec_networks \
    --configfile ../pypsa-iberia/config/config.yaml
```

## Setup

See `docs/setup.md`.

## Status

⚠️ Work in progress. Not yet validated against published Iberian system data.

## Citation

If you use this model, please cite PyPSA and PyPSA-Eur:
- Brown et al. (2018) "PyPSA: Python for Power System Analysis"
- Hörsch et al. (2018) "PyPSA-Eur: An open optimisation model of the European
  transmission system"

## License

MIT
