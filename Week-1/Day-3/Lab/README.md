# DAY3 LAB

# Opt_Check Using Yosys

```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ ls *opt*
$ ls *opt_check*
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog opt_check.v
> synth -top opt_check
> opt_clean -purge
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
```

🖼️ ![opt_check](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-3/Lab/opt_check.jpeg)

---

# Opt_Check2 Using Yosys

```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog opt_check2.v
> synth -top opt_check2
> opt_clean -purge
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
```

🖼️ ![opt_check2](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-3/Lab/opt_check2.jpeg)

---

# Opt_Check3 Using Yosys

```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog opt_check3.v
> synth -top opt_check3
> opt_clean -purge
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
```

🖼️ ![opt_check3](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-3/Lab/opt_check3.jpeg)

---

# Opt_Check4 Using Yosys


```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog opt_check4.v
> synth -top opt_check4
> opt_clean -purge
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
```

🖼️ ![opt_check4](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-3/Lab/opt_check4.jpeg)

---

# Dff_Const1 Using Iverilog And Yosys


```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ ls *dff*const*
$ gvim dff_const1.v -o dff_const2.v
$ iverilog dff_const1.v tb_dff_const1.v
$ ./a.out
$ gtkwave tb_dff_const1.vcd
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog dff_const1.v
> synth -top dff_const1
> dfflibmap -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
```
🖼️ ![gvim_dff_const1](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-3/Lab/gvim_dff_const1.jpeg)
🖼️ ![gtkwave_dff_const1](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-3/Lab/gtkwave_dff_const1.jpeg)
🖼️ ![dff_const1](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-3/Lab/dff_const1.jpeg)



---

# Dff_Const2 Using Iverilog And Yosys


```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ ls *dff*const*
$ iverilog dff_const2.v tb_dff_const2.v
$ ./a.out
$ gtkwave tb_dff_const2.vcd
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog dff_const2.v
> synth -top dff_const2
> dfflibmap -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
```

🖼️ ![gtkwave_dff_const2](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-3/Lab/gtkwave_dff_const2.jpeg)
🖼️ ![dff_const2](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-3/Lab/dff_const2.jpeg)

---

# Dff_Const3 Using Iverilog And Yosys


```bash
$ ls
$ cd sky130RTLDesignAndSynthesisWorkshop
$ ls
$ cd verilog_files
$ ls *dff*const*
$ iverilog dff_const3.v tb_dff_const3.v
$ ./a.out
$ gtkwave tb_dff_const3.vcd
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog dff_const3.v
> synth -top dff_const3
> dfflibmap -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show
```

🖼️ ![gtkwave_dff_const3](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-3/Lab/gtkwave_dff_const3.jpeg)
🖼️ ![dff_const3](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-3/Lab/dff_const3.jpeg)

---
