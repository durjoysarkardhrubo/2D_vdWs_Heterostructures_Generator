import numpy as np

def generate_graphene_unit_cell(a, b, c, alpha, beta, gamma):
    # Convert angles from degrees to radians
    alpha = np.radians(alpha)
    beta = np.radians(beta)
    gamma = np.radians(gamma)

    v1 = [a, 0, 0]
    v2 = [b * np.cos(gamma), b * np.sin(gamma), 0]
    v3 = [c * np.cos(beta), c * (np.cos(alpha) - np.cos(beta) * np.cos(gamma)) / np.sin(gamma), c * np.sqrt(1 - np.cos(beta)**2 - ((np.cos(alpha) - np.cos(beta) * np.cos(gamma)) / np.sin(gamma))**2)]
    
    basis_atoms = np.array([
        [0, 0, 0],
        [1/3, 2/3, 0]
    ])
    
    return np.array([v1, v2, v3]), basis_atoms

def generate_sic_unit_cell(a, b, c, alpha, beta, gamma):
    # Convert angles from degrees to radians
    alpha = np.radians(alpha)
    beta = np.radians(beta)
    gamma = np.radians(gamma)

    v1 = [a, 0, 0]
    v2 = [b * np.cos(gamma), b * np.sin(gamma), 0]
    v3 = [c * np.cos(beta), c * (np.cos(alpha) - np.cos(beta) * np.cos(gamma)) / np.sin(gamma), c * np.sqrt(1 - np.cos(beta)**2 - ((np.cos(alpha) - np.cos(beta) * np.cos(gamma)) / np.sin(gamma))**2)]
    
    basis_atoms = np.array([
        [0, 0, 0],  # Si atom
        [1/3, 2/3, 0]  # C atom
    ])
    
    atom_types = ['Si', 'C']
    
    return np.array([v1, v2, v3]), basis_atoms, atom_types

def generate_heterostructure_supercell(a, b, c, alpha, beta, gamma, nx, ny, sic_height, layer_distance):
    sic_lattice_vectors, sic_basis_atoms, sic_atom_types = generate_sic_unit_cell(a, b, c, alpha, beta, gamma)
    graphene_lattice_vectors, graphene_basis_atoms = generate_graphene_unit_cell(a, b, c, alpha, beta, gamma)
    
    atom_positions = []
    atom_labels = []

    # SiC layer
    for i in range(nx):
        for j in range(ny):
            for k, atom in enumerate(sic_basis_atoms):
                position = i * sic_lattice_vectors[0] + j * sic_lattice_vectors[1] + [0, 0, sic_height] + atom
                atom_positions.append(position)
                atom_labels.append(sic_atom_types[k])
    
    # Graphene layer
    for i in range(nx):
        for j in range(ny):
            for atom in graphene_basis_atoms:
                position = i * graphene_lattice_vectors[0] + j * graphene_lattice_vectors[1] + [0, 0, sic_height + layer_distance] + atom
                atom_positions.append(position)
                atom_labels.append('C')  # Graphene atoms are carbon
    
    return np.array(atom_positions), atom_labels

def save_atom_positions(atom_positions, atom_labels, filename):
    with open(filename, 'w') as f:
        for pos, label in zip(atom_positions, atom_labels):
            f.write(f'{label} {pos[0]:.6f} {pos[1]:.6f} {pos[2]:.6f}\n')

a = 3.08  
b = 3.08
c = 10.0
alpha = 90
beta = 90
gamma = 120

nx = int(input("Enter the size of the supercell in the x direction: "))
ny = int(input("Enter the size of the supercell in the y direction: "))
sic_height = float(input("Enter the height for the SiC sheet: "))
layer_distance = float(input("Enter the distance between the SiC and graphene layers: "))

atom_positions, atom_labels = generate_heterostructure_supercell(a, b, c, alpha, beta, gamma, nx, ny, sic_height, layer_distance)

# Save file
save_atom_positions(atom_positions, atom_labels, 'heterostructure_supercell.txt')

print(f"Heterostructure supercell with size {nx}x{ny}x1, SiC height {sic_height}, and layer distance {layer_distance} has been generated and saved to 'heterostructure_supercell.txt'.")
