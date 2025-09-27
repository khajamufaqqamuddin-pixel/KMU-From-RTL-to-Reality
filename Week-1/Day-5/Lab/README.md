# DAY5 LAB

# Incomp_If Using Iverilog And Yosys

```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ ls *incomp*
$ gvim *incomp* -o
$ iverilog incomp_if.v tb_incomp_if.v
$ ./a.out
$ gtkwave tb_incomp_if.vcd
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog incomp_if.v
> synth -top incomp_if
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
```

# Incomp Using Iverilog And Yosys

```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ ls *incomp*
$ gvim *incomp* -o
$ iverilog incomp_if2.v tb_incomp_if2.v
$ ./a.out
$ gtkwave tb_incomp_if2.vcd
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog incomp_if2.v
> synth -top incomp_if2
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
```



# Incomp_Case Using Iverilog And Yosys

```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ ls *case*
$ gvim comp_case.v -o incomp_case.v -o partial_case_assign.v -o bad_case.v
$ iverilog incomp_case.v tb_incomp_case.v
$ ./a.out
$ gtkwave tb_incomp_case.vcd
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog incomp_case.v
> synth -top incomp_case
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
```

# comp_Case Using Iverilog And Yosys

```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ ls *case*
$ gvim comp_case.v -o incomp_case.v -o partial_case_assign.v -o bad_case.v
$ iverilog comp_case.v tb_comp_case.v
$ ./a.out
$ gtkwave tb_comp_case.vcd
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog comp_case.v
> synth -top comp_case
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
```

# Partial_Case_Assign Using Iverilog And Yosys

```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ ls *case*
$ gvim comp_case.v -o incomp_case.v -o partial_case_assign.v -o bad_case.v
$ iverilog partial_case_assign.v tb_partial_case_assign.v
$ ./a.out
$ gtkwave tb_partial_case_assign.vcd
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog partial_case_assign.v
> synth -top partial_case_assign
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
```

# Bad_Case Using Iverilog And Yosys

```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ ls *case*
$ gvim comp_case.v -o incomp_case.v -o partial_case_assign.v -o bad_case.v
$ iverilog bad_case.v tb_bad_case.v
$ ./a.out
$ gtkwave tb_bad_case.vcd
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog bad_case.v
> synth -top bad_case
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
```

# Mux_Generate Using Iverilog And Yosys

```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ gvim mux_generate.v
$ iverilog mux_generate.v tb_mux_generate.v
$ ./a.out
$ gtkwave tb_mux_generate.vcd
```






