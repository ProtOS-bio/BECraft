# BECraft

**BECraft** (BindEnergyCraft) is a drop-in extension of the protein–binder design pipeline first introduced in BindCraft (Pacesa et al., 2024). By adding an energy-based loss to the original AlphaFold2-back-propagation workflow, we improve binder designs while maintaining the user-friendly pipeline of BindCraft!

![alt text](becraft/method.png)

[Preprint link for BECraft](https://arxiv.org/abs/2505.21241)

## Installation

After cloning this repository, navigate to the ```becraft``` folder and run the BindCraft installation script:

`bash install_bindcraft.sh --cuda '12.4' --pkg_manager 'conda'`

Like BindCraft, BECraft requires a CUDA-compatible Nvidia graphics card to run. In the *cuda* setting, please specify the CUDA version compatible with your graphics card, for example '11.8'. If unsure, leave blank but it's possible that the installation might select the wrong version, which will lead to errors. In *pkg_manager* specify whether you are using 'mamba' or 'conda', if left blank it will use 'conda' by default. Note: This install script will install PyRosetta, which requires a license for commercial purposes. The code requires about 2 Mb of storage space, while the AlphaFold2 weights take up about 5.3 Gb.

Next, navigate to the ```ColabDesign``` directory and run ```pip install -e .```  to install the ptmenergy loss function.

## Running binder design

To run binder design, activate the newly created ```BindCraft``` environment and navigate to the ```becraft``` directory. Then, execute the following command:

```
python -u ./bindcraft.py --settings './settings_target/PDL1.json' --filters './settings_filters/no_filters.json' --advanced './settings_advanced/default_4stage_multimer.json'
```

Importantly, in the default configuration provided in ```default_4stage_multimer.json```, the iptmenergy loss has a weight of $\mathbf{0.05}$, and the iptm loss has a weight of $\mathbf{0}$. Both are set to true to track their values in the logging output during the design process. To use other design configuration jsons, similarly add the iptmenergy field.

By default, MPNN optimization is disabled. Please set this to True if necessary.

For further information on all design and filter settings, see the [Bindcraft documentation](becraft/README.md).

## Tuning the effect of TM-weighting



## Analyzing binders

