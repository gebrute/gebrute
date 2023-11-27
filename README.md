from gpaw import GPAW, PW
from ase import Atoms
from ase.build import bulk

# Define the transition metal cluster
cluster = Atoms('Ni3', positions=[[0, 0, 0], [1.5, 0, 0], [0, 1.5, 0]])

# Set up the calculator
calc = GPAW(mode=PW(300), xc='PBE', occupations={'name': 'fermi-dirac', 'width': 0.1})

# Set up the cluster and perform the calculation
cluster.calc = calc
cluster.get_potential_energy()

# Get the magnetic moments
magnetic_moments = cluster.get_magnetic_moments()

# Print the results
print(f"Magnetic moments: {magnetic_moments}")
