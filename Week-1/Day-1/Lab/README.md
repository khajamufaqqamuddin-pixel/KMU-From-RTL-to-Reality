# DAY1 LAB
File Path
```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
```
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
