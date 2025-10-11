# Week-3 LAB

# GLS BabySoC
```bash
$ ls
$ cd VSDBabySoC
$ ls
$ cd src
$ cd module
$ ls
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog avsdpll_stub.v
> read_verilog avsddac_stub.v
> read_verilog rvmyth.v
> read_verilog vsdbabysoc.v
> synth -top vsdbabysoc
> dfflibmap -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> flatten
> setundef -zero
> clean -purge
> rename -enumerate
> write_verilog -noattr vsdbabysoc_net.v
> show vsdbabysoc
> !gvim vsdbabysoc_net.v
$ iverilog iverilog avsdpll_stub.v  avsddac_stub.v  rvmyth.v  vsdbabysoc_net.v testbench.v
$ ./a.out
$ gtkwave dump.vcd
```


# OpenSTA
```
$ sta
% read_liberty /home/kmu/Desktop/yosys/OpenSTA/examples/nangate45_slow.lib
% read_verilog /home/kmu/Desktop/yosys/OpenSTA/examples/example1.v
% link_design top
% create_clock -name clk -period 10 {clk1 clk2 clk3}
% set_input_delay -clock clk 0 {in1 in2}
% report_checks
```
```
% report_checks -path_delay min_max
Startpoint: in1 (input port clocked by clk)
Endpoint: r1 (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: min

  Delay    Time   Description
---------------------------------------------------------
   0.00    0.00   clock clk (rise edge)
   0.00    0.00   clock network delay (ideal)
   0.00    0.00 ^ input external delay
   0.00    0.00 ^ in1 (in)
   0.00    0.00 ^ r1/D (DFF_X1)
           0.00   data arrival time

   0.00    0.00   clock clk (rise edge)
   0.00    0.00   clock network delay (ideal)
   0.00    0.00   clock reconvergence pessimism
           0.00 ^ r1/CK (DFF_X1)
   0.01    0.01   library hold time
           0.01   data required time
---------------------------------------------------------
           0.01   data required time
          -0.00   data arrival time
---------------------------------------------------------
          -0.01   slack (VIOLATED)


Startpoint: r2 (rising edge-triggered flip-flop clocked by clk)
Endpoint: r3 (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: max

  Delay    Time   Description
---------------------------------------------------------
   0.00    0.00   clock clk (rise edge)
   0.00    0.00   clock network delay (ideal)
   0.00    0.00 ^ r2/CK (DFF_X1)
   0.23    0.23 v r2/Q (DFF_X1)
   0.08    0.31 v u1/Z (BUF_X1)
   0.10    0.41 v u2/ZN (AND2_X1)
   0.00    0.41 v r3/D (DFF_X1)
           0.41   data arrival time

  10.00   10.00   clock clk (rise edge)
   0.00   10.00   clock network delay (ideal)
   0.00   10.00   clock reconvergence pessimism
          10.00 ^ r3/CK (DFF_X1)
  -0.16    9.84   library setup time
           9.84   data required time
---------------------------------------------------------
           9.84   data required time
          -0.41   data arrival time
---------------------------------------------------------
           9.43   slack (MET)


```
```
% report_checks -digits 4 -fields capacitance
Startpoint: r2 (rising edge-triggered flip-flop clocked by clk)
Endpoint: r3 (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: max

      Cap     Delay      Time   Description
----------------------------------------------------------------------
             0.0000    0.0000   clock clk (rise edge)
             0.0000    0.0000   clock network delay (ideal)
             0.0000    0.0000 ^ r2/CK (DFF_X1)
   0.8352    0.2332    0.2332 v r2/Q (DFF_X1)
   0.8533    0.0810    0.3142 v u1/Z (BUF_X1)
   1.0301    0.0956    0.4098 v u2/ZN (AND2_X1)
             0.0000    0.4098 v r3/D (DFF_X1)
                       0.4098   data arrival time

            10.0000   10.0000   clock clk (rise edge)
             0.0000   10.0000   clock network delay (ideal)
             0.0000   10.0000   clock reconvergence pessimism
                      10.0000 ^ r3/CK (DFF_X1)
            -0.1575    9.8425   library setup time
                       9.8425   data required time
----------------------------------------------------------------------
                       9.8425   data required time
                      -0.4098   data arrival time
----------------------------------------------------------------------
                       9.4327   slack (MET)


```
```
% report_checks -digits 4 -fields [list capacitance slew input_pins fanout]
Startpoint: r2 (rising edge-triggered flip-flop clocked by clk)
Endpoint: r3 (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: max

Fanout       Cap      Slew     Delay      Time   Description
-------------------------------------------------------------------------------------
                    0.0000    0.0000    0.0000   clock clk (rise edge)
                              0.0000    0.0000   clock network delay (ideal)
                    0.0000    0.0000    0.0000 ^ r2/CK (DFF_X1)
     1    0.8352    0.0164    0.2332    0.2332 v r2/Q (DFF_X1)
                    0.0164    0.0000    0.2332 v u1/A (BUF_X1)
     1    0.8533    0.0146    0.0810    0.3142 v u1/Z (BUF_X1)
                    0.0146    0.0000    0.3142 v u2/A2 (AND2_X1)
     1    1.0301    0.0165    0.0956    0.4098 v u2/ZN (AND2_X1)
                    0.0165    0.0000    0.4098 v r3/D (DFF_X1)
                                        0.4098   data arrival time

                    0.0000   10.0000   10.0000   clock clk (rise edge)
                              0.0000   10.0000   clock network delay (ideal)
                              0.0000   10.0000   clock reconvergence pessimism
                                       10.0000 ^ r3/CK (DFF_X1)
                             -0.1575    9.8425   library setup time
                                        9.8425   data required time
-------------------------------------------------------------------------------------
                                        9.8425   data required time
                                       -0.4098   data arrival time
-------------------------------------------------------------------------------------
                                        9.4327   slack (MET)
```
```
% report_power
Group                  Internal  Switching    Leakage      Total
                          Power      Power      Power      Power (Watts)
----------------------------------------------------------------
Sequential             1.08e-06   8.25e-09   1.63e-07   1.25e-06  94.4%
Combinational          3.38e-08   9.24e-09   3.08e-08   7.38e-08   5.6%
Clock                  0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
Macro                  0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
Pad                    0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
----------------------------------------------------------------
Total                  1.11e-06   1.75e-08   1.94e-07   1.33e-06 100.0%
                          84.1%       1.3%      14.6%
```
```
% report_pulse_width_checks                                                                              
                                     Required  Actual
Pin                                    Width   Width   Slack
------------------------------------------------------------
r1/CK (low)                             0.22    5.00    4.78 (MET)
r2/CK (low)                             0.22    5.00    4.78 (MET)
r3/CK (low)                             0.22    5.00    4.78 (MET)
r1/CK (high)                            0.19    5.00    4.81 (MET)
r2/CK (high)                            0.19    5.00    4.81 (MET)
r3/CK (high)                            0.19    5.00    4.81 (MET)

```
```
% report_units
 time 1ns
 capacitance 1fF
 resistance 1kohm
 voltage 1v
 current 1mA
 power 1nW
 distance 1um
 ```

```
$ sta
% read_liberty -max /home/kmu/Desktop/yosys/OpenSTA/examples/nangate45_slow.lib
% read_liberty -min /home/kmu/Desktop/yosys/OpenSTA/examples/nangate45_fast.lib
% read_verilog /home/kmu/Desktop/yosys/OpenSTA/examples/example1.v
% link_design top
% create_clock -name clk -period 10 {clk1 clk2 clk3}
% set_input_delay -clock clk 0 {in1 in2}
% report_checks
```
```
% report_checks
Startpoint: r2 (rising edge-triggered flip-flop clocked by clk)
Endpoint: r3 (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: max

  Delay    Time   Description
---------------------------------------------------------
   0.00    0.00   clock clk (rise edge)
   0.00    0.00   clock network delay (ideal)
   0.00    0.00 ^ r2/CK (DFF_X1)
   0.23    0.23 v r2/Q (DFF_X1)
   0.08    0.31 v u1/Z (BUF_X1)
   0.10    0.41 v u2/ZN (AND2_X1)
   0.00    0.41 v r3/D (DFF_X1)
           0.41   data arrival time

  10.00   10.00   clock clk (rise edge)
   0.00   10.00   clock network delay (ideal)
   0.00   10.00   clock reconvergence pessimism
          10.00 ^ r3/CK (DFF_X1)
  -0.16    9.84   library setup time
           9.84   data required time
---------------------------------------------------------
           9.84   data required time
          -0.41   data arrival time
---------------------------------------------------------
           9.43   slack (MET)

```



# OpenSTA BabySoC
```
% read_liberty -min /home/kmu/Desktop/yosys/VSDBabySoC/src/module/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
% read_liberty -max /home/kmu/Desktop/yosys/VSDBabySoC/src/module/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
% read_liberty -min /home/kmu/Desktop/yosys/VSDBabySoC/src/lib/avsdpll.lib
% read_liberty -max /home/kmu/Desktop/yosys/VSDBabySoC/src/lib/avsdpll.lib
% read_liberty -min /home/kmu/Desktop/yosys/VSDBabySoC/src/lib/avsddac.lib
% read_liberty -max /home/kmu/Desktop/yosys/VSDBabySoC/src/lib/avsddac.lib
% read_liberty /home/kmu/Desktop/yosys/VSDBabySoC/src/module/vsdbabysoc.v
% link_design vsdbabysoc
% read_sdc /home/kmu/Desktop/yosys/VSDBabySoC/src/sdc/vsdbabysoc_synthesis.sdc
% report_checks

