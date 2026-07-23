# Mechanical Design & FEA Thermo-Structural Analysis of an Aluminum 2618 Piston

## ðŸ“Œ Project Overview
This repository contains a comprehensive CAD design and coupled Thermo-Structural Finite Element Analysis (FEA) of a high-performance internal combustion engine piston modeled from **Aluminum Alloy 2618 (Al2618)**.

The evaluation encompasses:
- Precise 2D technical drawings and 3D geometric modeling per ASME Y14.5-2018 standards.
- Transient thermal analysis under severe combustion gas temperatures, surface convection, and radiation.
- Static structural analysis under combustion peak pressure and imported transient thermal stress states.

---

## ðŸ“ 1. Geometric & Mechanical Specifications

| Parameter | Specification / Value |
| :--- | :--- |
| **Part Name** | Piston 2618 |
| **Material** | Aluminum Alloy 2618 (Al-Cu-Mg-Fe-Ni) |
| **Protective Finish** | Anodizing with dry-film skirt coating |
| **Bore Diameter ($D$)** | $100.0\text{ mm}$ |
| **Total Height ($H$)** | $89.4\text{ mm}$ |
| **Crown Radius ($R$)** | $78.83\text{ mm}$ |
| **Crown Dome Height** | $17.73\text{ mm}$ |
| **Crown Thickness ($t_c$)** | $42.5\text{ mm}$ |
| **Piston Pin Hole Diameter ($d_p$)** | $33.8\text{ mm}$ |
| **Pin Center to Skirt Base** | $27.0\text{ mm}$ |
| **Skirt Width** | $38.77\text{ mm}$ |
| **Skirt Height** | $54.8\text{ mm}$ |
| **Ring Groove Dimensions** | Top: $7.3\text{ mm}$, Middle: $4.3\text{ mm}$, Bottom: $5.7\text{ mm}$ |
| **Mass** | $0.12755\text{ kg}$ ($127.55\text{ g}$) |
| **Volume** | $4.6047 \times 10^{-5}\text{ m}^3$ |

---

## ðŸ”¬ 2. Material Properties (Aluminum 2618)

| Property | Symbol | Value | Unit |
| :--- | :--- | :--- | :--- |
| **Density** | $\rho$ | $2770$ | $\text{kg/m}^3$ |
| **Young's Modulus** | $E$ | $73.5$ | $\text{GPa}$ |
| **Poisson's Ratio** | $\nu$ | $0.33$ | dimensionless |
| **Bulk Modulus** | $K$ | $72.06$ | $\text{GPa}$ |
| **Shear Modulus** | $G$ | $27.63$ | $\text{GPa}$ |
| **Thermal Conductivity** | $k$ | $147$ | $\text{W/m}\cdot\text{K}$ |
| **Coeff. of Thermal Expansion** | $\alpha$ | $2.22 \times 10^{-5}$ | $\text{K}^{-1}$ |
| **Tensile Yield Strength** | $\sigma_y$ | $372$ | $\text{MPa}$ |
| **Tensile Ultimate Strength** | $\sigma_u$ | $441$ | $\text{MPa}$ |

---

## âš™ï¸ 3. FEA Simulation Setup & Boundary Conditions

The analysis was executed in **Ansys Mechanical 2025 R2** using a coupled multi-physics framework.

### **3.1 Finite Element Mesh Statistics**
- **Element Control:** Program Controlled 3D Solid Elements
- **Total Nodes:** $16,310$
- **Total Elements:** $8,039$
- **Bounding Box Dimensions:** $85.0\text{ mm} \times 92.38\text{ mm} \times 85.0\text{ mm}$

### **3.2 Thermal Boundary Conditions (Transient Thermal System)**
- **Initial Temperature:** $22^\circ\text{C}$ across all nodes.
- **Crown Thermal Load:** Applied $450^\circ\text{C}$ step temperature on 3 crown top faces.
- **Skirt & Under-crown Convection:** Applied to 13 faces with Film Coefficient $h = 1500\text{ W/m}^2\cdot\text{K}$ and ambient oil mist temperature $T_a = 90^\circ\text{C}$.
- **Thermal Radiation:** Applied to 16 external faces with Emissivity $\epsilon = 0.5$ and ambient temperature $150^\circ\text{C}$.

### **3.3 Structural Boundary Conditions (Static Structural System)**
- **Fixed Constraints:** Pin hole inner contact surfaces (2 faces) fixed to simulate the gudgeon pin constraint.
- **Gas Pressure Load:** Applied normal to crown faces across 3 time steps:
  - **Step 1 ($t = 1.0\text{ s}$):** $7.0\text{ MPa}$ ($70\text{ bar}$)
  - **Step 2 ($t = 2.0\text{ s}$):** $10.0\text{ MPa}$ ($100\text{ bar}$)
  - **Step 3 ($t = 6.0\text{ s}$):** $13.0\text{ MPa}$ ($130\text{ bar}$)
- **Thermal Load Coupling:** Imported nodal temperature field directly from Transient Thermal solution at $t = 1.0\text{ s}$.

---

## ðŸ“Š 4. Key Results & Summary Findings

### **Thermal Analysis Results ($t = 1.0\text{ s}$)**
- **Maximum Crown Temperature:** $452.53^\circ\text{C}$ (located at the center top crown dome)
- **Minimum Skirt Temperature:** $90.382^\circ\text{C}$ (located at lower skirt region near convection surfaces)
- **Average Body Temperature:** $185.6^\circ\text{C}$
- **Maximum Heat Flux:** $4.4084 \times 10^6\text{ W/m}^2$ (concentrated at crown top edges and ring grooves)

### **Structural Analysis Results (Combined Pressure + Thermal Load at $t = 6.0\text{ s}$)**
- **Maximum Total Deformation:** $7.867\text{ mm}$ ($0.007867\text{ m}$)
- **Maximum Equivalent (von-Mises) Stress:** $2.722\text{ GPa}$ ($2.722 \times 10^9\text{ Pa}$)
- **Maximum Equivalent Strain:** $0.0372\text{ m/m}$ ($3.72\%$)

---

## ðŸ“ Repository File Structure

```
â”œâ”€â”€ README.md                # Project documentation and summary
â”œâ”€â”€ CALCULATION_REPORT.md    # Detailed analytical calculations, FEA equations & verification
```

---

## ðŸ‘¤ Author
- **Drawn & Modeled By:** MOHAMMAD MAAWIZ
- **Date:** July 23, 2026
- **Software Tools:** PTC Creo / SpaceClaim, Ansys Mechanical 2025 R2 Student Edition 
