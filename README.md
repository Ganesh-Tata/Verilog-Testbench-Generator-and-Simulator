# 🚀 Verilog Test Bench Generator & Simulator

An AI-powered hardware verification workflow that automates the creation and execution of Verilog testbenches. By leveraging **Large Language Models (LLMs)** like Gemini and open-source EDA tools, this project bridges the gap between high-level AI and low-level hardware description languages.

## 📌 Project Overview

Verification is a critical and time-consuming phase in the VLSI design cycle. This project simplifies that process by providing a **Google Colab-based environment** where users can input RTL designs and receive fully functional, AI-generated testbenches. The system not only writes the code but also simulates it and provides downloadable waveform data.

### Key Features:
*   **Dynamic RTL Processing:** Accepts any Verilog module via runtime input.
*   **AI-Assisted Verification:** Uses Gemini 1.5 Flash to intelligently infer port lists, clock requirements, and stimulus patterns.
*   **Cloud-Based Simulation:** Runs **Icarus Verilog** and **VVP** in a Linux-based virtual environment (no local installation required).
*   **Waveform Visualization:** Generates `.vcd` files compatible with GTKWave for detailed timing analysis.

---

## 🛠️ Tech Stack

*   **Platform:** Google Colab
*   **Core Logic:** Python 3.x
*   **AI Engine:** Google Gemini API
*   **HDL Tools:** 
    *   **Icarus Verilog:** Compiler/Simulator
    *   **VVP:** Simulation Runtime
    *   **GTKWave:** Waveform Viewer (Local)

---

## 🚀 Getting Started

### Prerequisites
1.  A **Google Gemini API Key** (Get one from [Google AI Studio](https://aistudio.google.com/)).
2.  Google Colab access.

### Usage Instructions
1.  **Open the Notebook:** Upload the `.ipynb` file to your Google Colab.
2.  **Initialize Environment:** Run the first cell to install `iverilog` and required Python libraries.
3.  **Enter API Key:** Provide your Gemini API key in the configuration cell.
4.  **Input RTL:** Run the input cell and paste your Verilog module. For example:
    ```verilog
    module half_adder(input a, b, output sum, carry);
      assign sum = a ^ b;
      assign carry = a & b;
    endmodule
    ```
    *Type `END_CODE` on a new line to finish.*
5.  **Generate & Simulate:** Execute the remaining cells. The AI will generate `testbench.v`, compile it with your design, and run the simulation.
6.  **Download Results:** Download the `waveform.vcd` file and open it locally using GTKWave.

---

## 📂 Project Structure

*   `design.v` - The user-provided RTL module.
*   `testbench.v` - The AI-generated verification environment.
*   `simulation_output` - Compiled binary file for the simulator.
*   `waveform.vcd` - Output file containing all signal transition data.

---

## 📊 Example Console Output
```bash
Generating test bench with Gemini API, please wait...
Generated test bench 'testbench.v' has been created.
Compiling Verilog files...
Compilation successful. Running simulation...
Time=0 | a=0, b=0 | sum=0, carry=0
Time=10 | a=0, b=1 | sum=1, carry=0
Time=20 | a=1, b=0 | sum=1, carry=0
Time=30 | a=1, b=1 | sum=0, carry=1
Simulation completed. 'waveform.vcd' exists.
