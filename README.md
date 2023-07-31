# RISC-V_Microprogrammed

<!-- TABLE OF CONTENTS -->
<h2 id="table-of-contents"> Table of Contents</h2>
<ol>
  <li><a href="#about-the-project">About The Project</a></li>
  <li><a href="#description">Description</a></li>
</ol>

<img src="https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png" alt="a line" height="10" >

<!-- ABOUT THE PROJECT -->
<h2 id="about-the-project">About The Project</h2>
<p>This project focuses on designing and implementing a multi-cycle RISC-V processor using microprogrammed control that can execute these instructions:</p>
<ul>
  <li><b>R-type instructions</li>
  <li><b>I-type instructions</li>
  <li><b>lw</li>
  <li><b>sw</li>
  <li><b>beq</li>
  <li><b>jal</li>
</ul>
<p>The synthesis stages assume the execution of the design on the DE1-SoC board.</p>

<!-- DESCRIPTION -->
<h2 id="description">Description</h2>
<p>The processor consists of three main units:</p>
<img src="imgs/multicycle.png" alt="top module img">

<!-- MEMORY DESCRIPTION -->
<h3>Memory:</h3>
<p>The memory unit is responsible for storing both instructions and data.</p>

<!-- DATA PATH DESCRIPTION -->
<p>Multi-cycle data paths break up instructions into separate steps. The steps based on the executing instruction, are as follows:</p>
<p></p>
<p>Therefore the data path consists of a Register File, ALU, Extend unit, several multiplexers for picking up the input of other units, and 5 Nonarchitectural registers to hold the results of each step:</p>
<!-- <img src=""> -->
<p>Each functional unit can be used more than once in an instruction, as long as it is used in different clock cycles.</p>

<!-- CONTROLLER DESCRIPTION -->
<h3>Controller:</h3>
<p>The controller results in the instructions to be implemented by constructing a definite collection of signals at each system clock cycle. Each of these output signals generates one micro-operation including register transfer. Thus, the sets of control signals are generated definite micro-operations that can be saved in the internal memory.</p>
<p>Each bit that forms the microinstruction is linked to one control signal. When the bit is set, the control signal is active. When it is cleared the control signal turns inactive. These microinstructions in a sequence can be saved in the internal ’control’ memory:</p>
