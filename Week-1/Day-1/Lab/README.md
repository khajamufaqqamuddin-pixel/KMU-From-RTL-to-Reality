# DAY1 LAB
File Path
```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
```
🖼️ ![file_path](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-1/Lab/file_path.jpeg)
# Good_mux using iverilog

```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ iverilog good_mux.v tb_good_mux.v
$ ./a.out
$ gtkwave tb_good_mux.vcd
$ gvim tb_good_mux.v -o good_mux.v
```
🖼️ ![good_mux](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-1/Lab/good_mux.jpeg)
🖼️ ![tb_good_mux](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-1/good_mux_gtkwave.jpeg)
🖼️ ![gvim_goo_mux](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-1/Lab/gvim_goo_mux.jpeg)
# Good_mux using yosys
```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog good_mux.v
> synth -top good_mux
> abc -liberty   /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
> write_verilog good_mux_netlist.v
> !gvim good_mux_netlist.v
> write_verilog -noattr good_mux_netlist.v
> !gvim good_mux_netlist.v
```
🖼️ ![yosys_good_mux](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-1/Lab/yosys_good_mux.jpeg)
🖼️ ![good_mux_netlist](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-1/Lab/good_mux_netlist.jpeg)
