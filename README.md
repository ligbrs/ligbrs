# LigBrs: Ligands by Brute-force Substituent Replacement

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Framework](https://img.shields.io/badge/GUI-PyQt5-green.svg)](https://pypi.org/project/PyQt5/)

**LigBrs** is a computational tool developed for Fragment-Based Drug Design (FBDD), specifically focused on the *fragment growing* strategy. Implemented in Python 3 with a PyQt5 graphical interface, LigBrs automates the generation of new ligands by combinatorially replacing hydrogen atoms on a core scaffold with molecular fragments.

## 🚀 Key Features

* **Hybrid Chemoinformatics Engine:** Integrates **Open Babel** (for robust topological manipulation and file parsing) and **RDKit** (for 2D rendering, 3D embedding, and energy minimization).
* **Intuitive GUI:** A user-friendly interface built with **PyQt5** allows for visual selection of anchor points (vectors) and file management.
* **Brute-Force Algorithm:** Supports both manual vector selection and an automated **batch mode** that iterates through all possible combinations of fragment hydrogens against selected core anchors.
* **Automated Post-Processing:** Every generated molecule undergoes automatic valency correction, 3D coordinate generation (`AllChem.EmbedMolecule`), and geometry optimization using the **MMFF94** force field.
* **Traceability:** Output files are named programmatically (e.g., `combined_frag1_coreH15_fragH10.sdf`) to ensure full data traceability.

## ⚙️ How It Works

LigBrs operates using a rigorous geometric and topological approach:

1.  **Input:** The user provides a **Core Scaffold** (`.mol2`) and a **Fragment Library** (`.sdf`).
2.  **Vector Selection:** The user selects explicit hydrogen atoms on both the core and fragments to serve as growth vectors.
3.  **Alignment & Fusion:**
    * The algorithm translates both molecules so that the selected hydrogen atoms coincide at the Cartesian origin (0, 0, 0).
    * Topological fusion is performed via Open Babel, including index shifting to maintain connectivity matrices.
    * A new single bond is created between the heavy atoms, and the guide hydrogens are removed.
4.  **Optimization:** The crude structure is refined using RDKit to resolve steric clashes and find a local energy minimum.

## 🛠️ Dependencies

To run LigBrs, you need the following Python libraries installed:

* Python 3.x
* PyQt5
* Open Babel (Python bindings)
* RDKit

## 📦 Installation

```bash
# Clone the repository
git clone [https://github.com/your-username/ligbrs.git](https://github.com/your-username/ligbrs.git)

# Navigate to the directory
cd ligbrs

# Install dependencies (using conda is recommended for RDKit/OpenBabel)
conda install -c conda-forge rdkit openbabel
pip install PyQt5
