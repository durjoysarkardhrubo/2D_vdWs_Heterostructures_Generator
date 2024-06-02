# 2D Heterostructure Supercell Generator

This repository contains Python scripts to generate 2D heterostructure supercells of graphene on SiC. The scripts allow user-defined supercell dimensions, SiC sheet height, and interlayer distance. Outputs atomic positions in a text file for further analysis and simulation.

## Usage

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/heterostructure-supercell-generator.git
   cd heterostructure-supercell-generator
   ```

2. **Run the script:**
   ```bash
   python Graphene_SiC_2D.py
   ```

3. **Provide input when prompted:**
   - Size of the supercell in the x direction (nx)
   - Size of the supercell in the y direction (ny)
   - Height for the SiC sheet (sic_height)
   - Distance between the SiC and graphene layers (layer_distance)

4. **Output:**
   The atomic positions will be saved in `heterostructure_supercell.txt`.

## Requirements

- Python 3.x
- NumPy

## Example

```bash
Enter the size of the supercell in the x direction: 3
Enter the size of the supercell in the y direction: 3
Enter the height for the SiC sheet: 5.0
Enter the distance between the SiC and graphene layers: 3.4
```

This will generate and save the heterostructure supercell in `heterostructure_supercell.txt`.
