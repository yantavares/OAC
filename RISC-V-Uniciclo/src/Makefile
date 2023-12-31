# Define the compiler
GHDL=ghdl
GTKWAVE=gtkwave

# VHDL source files
SOURCES=./PC/PC.vhdl ./Add_4/Add_4.vhdl ./Adder/Adder.vhdl ./Alu_Control/Alu_Control.vhdl ./Control/Control.vhdl ./Mux_2_1/Mux_2_1.vhdl ./Mux_2_5bits/Mux_2_5bits.vhdl ./Mux_8_1/Mux_8_1.vhdl ./NewImmediateGenerator/NewImmediateGenerator.vhdl ./NewRAM/NewRAM.vhdl ./NewROM/NewROM.vhdl ./NewXREG/NewXREG.vhdl ./NewALU/NewALU.vhdl RV32_Processor.vhdl Testbench_RV32_Processor.vhdl

# Top level entity
TOP_LEVEL=RV32_Processor

# Testbench
TESTBENCH=Testbench_RV32_Processor

# Default target: compile all VHDL files and run the testbench
all: compile run_testbench

# Compile VHDL files
compile: $(SOURCES)
	$(GHDL) -a --std=08 $(SOURCES)

# Elaborate top level
elaborate: compile
	$(GHDL) -e --std=08 $(TOP_LEVEL)
	$(GHDL) -e --std=08 $(TESTBENCH)

# Run the testbench
run_testbench: elaborate
	$(GHDL) -r --std=08 $(TESTBENCH) --vcd=testbench_waveform.vcd

# Run the processor simulation
run_processor: elaborate
	$(GHDL) -r --std=08 $(TOP_LEVEL) --vcd=processor_waveform.vcd

# Open the waveform with GTKWave
view_waveform:
	$(GTKWAVE) testbench_waveform.vcd

# Clean up generated files
clean:
	$(GHDL) --clean
	rm -f *.vcd

.PHONY: all compile elaborate run_testbench run_processo{r view_waveform clean
