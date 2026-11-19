# 6T SRAM Cell: Static Noise Margin Model

A Python model of a 6-transistor SRAM cell using a simplified square-law MOSFET model. It solves each half-cell's voltage transfer curve, builds the butterfly plot, and extracts the read and hold static noise margin (SNM) with the 45-degree method. It then shows how SNM changes with supply voltage and with the cell ratio (pull-down strength divided by access-transistor strength).

**Tools:** Python (NumPy, SciPy, Matplotlib). Runs in Google Colab with no installs.
**Author:** Kiranmayee Vaddepally, M.Tech, Quantum and Solid State Devices, IIT Hyderabad

## How to run

1. Open `SRAM\_6T\_Static\_Noise\_Margin.ipynb` in [Google Colab](https://colab.research.google.com) (File > Upload notebook).
2. Choose Runtime > Run all.
3. Change the transistor parameters in the model cell and re-run.

## What the model does

1. Solves the output voltage of each cell half-inverter, with the access transistor included for the read case.
2. Builds the butterfly curves from the two mirrored transfer curves.
3. Extracts SNM as the side of the largest square that fits inside the smaller lobe.
4. Sweeps supply voltage and cell ratio.

## Checks

* A balanced inverter switches at exactly VDD/2.
* The SNM from the 45-degree method agrees with an independent brute-force search for the largest inscribed square to within about 0.5%.

## Example results (VDD = 1.0 V, cell ratio 2)

* Hold SNM: about 413 mV.
* Read SNM: about 225 mV.
* Read SNM rises with cell ratio (about 162 mV at a ratio of 0.8 to about 270 mV at a ratio of 4) and falls as the supply voltage is lowered.

## Assumptions and limitations

* Long-channel square-law model, with illustrative parameters that are not from a real technology.
* No channel-length modulation, velocity saturation, subthreshold current, process variation or temperature dependence.
* Without channel-length modulation the inverter gain is unrealistically high, so hold SNM is larger than real cells show. The trends are meaningful, but the absolute values are not.
* Below about 0.7 V the model is least reliable.
* Only read and hold margins are computed. Write margin is not modelled.
* This is a first-principles study of the method, not a replacement for transistor-level SPICE simulation with a real technology model.

