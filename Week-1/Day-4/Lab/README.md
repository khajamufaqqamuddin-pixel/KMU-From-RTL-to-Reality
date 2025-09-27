# DAY4 LAB

# Ternary_Operator_Mux Using Iverilog,Yosys,GLS

```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ gvim ternary_operator_mux.v -o bad_mux.v -o good_mux.v
$ iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
$ ./a.out
$ gtkwave tb_ternary_operator_mux.vcd
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog ternary_operator_mux.v
> synth -top ternary_operator_mux
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> write_verilog noattr ternary_operator_mux_net.v
> show
// FOR GLS
$ iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v
$ ./a.out
$ gtkwave tb_ternary_operator_mux.vcd
```

🖼️ ![gtkwavw_ternary_operator](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-4/Lab/gtkwave_ternary_operator_mux.jpeg)
🖼️ ![ternary_operator_mux](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-4/Lab/ternary_operator_mux.jpeg)

---

# Blocking_Caveat Using Iverilog,Yosys,GLS

```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ gvim blocking_caveat.v
$ iverilog blocking_caveat.v tb_blocking_caveat.v
$ ./a.out
$ gtkwavetb_blocking_cavaet.vcd
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog blocking_caveat.v
> synth -top blocking_caveat
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> write_verilog -noattr blocking_caveat_net.v
> show
> exit
$ iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v
$ ./a.out
$ gtkwave tb_blocking_caveat.vcd
```

🖼️ ![iverilog_blocking_caveat](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-4/Lab/iverilog_blocking%20caveat.jpeg)
🖼️ ![gvim_blocking_caveat](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-4/Lab/gvim_blocking_caveat.jpeg)
🖼️ ![gtkwave_blocking_caveat](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-4/Lab/gtkwave_blocking_caveat.jpeg)
🖼️ ![blocking_caveat](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-4/Lab/blocking_caveat.jpeg)


---



