## DAY-1 LAB
```bash
$ git clone https://github.com/kunalg123/sky130CircuitDesignWorkshop.git
$ cd  sky130CircuitDesignWorkshop
$ cd design
$ ls
$ cd sky130_fd_pr
$ ls 
$ cd cells
$ ls 
$ cd nfet_01v8
$ ls
$ less sky130_fd_pr__nfet_01v8__ss.pm3.spice
$ less sky130_fd_pr__nfet_01v8__tt.corner.spice
$ cd ..
$ cd pfet_01v8
$ ls
$ cd ../..
$ ls
$ cd models
$ ls
$ less sky130.lib.spice 
$ less all.spice
$ cd ../..
$ vim day1_nfet_idvds_L2_W5.spice
$ ngspice day1_nfet_idvds_L2_W5.spice
> plot -vdd#branch
> exit
```
🖼️
![ngspice](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-4/Lab/ngspice.jpeg)


🖼️
![vim day1](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-4/Lab/vim%20day1.png)


🖼️
![day1 nfet idvds op](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-4/Lab/day1%20nfet%20idvds%20op.jpeg)






## DAY-2 LAB
```bash
$ cd  sky130CircuitDesignWorkshop
$ cd design
$ ls
$ vim day2_nfet_idvds_L015_W039.spice
$ ngspice day2_nfet_idvds_L015_W039.spice
> plot -vdd#branch
> exit
```
🖼️
![vim day2](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-4/Lab/vim%20day2.png)



🖼️
![day2 nfet idvds](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-4/Lab/day2%20nfet%20idvds.jpeg)








## DAY-3 LAB
```bash
$ cd  sky130CircuitDesignWorkshop
$ cd design
$ ls
$ vim day3_inv_vtc_Wp084_Wn036.spice
$ ngspice day3_inv_vtc_Wp084_Wn036.spice
> plot out vs in
> exit	
$ vim day3_inv_tran_Wp084_Wn036.spice 
$ ngspice day3_inv_tran_Wp084_Wn036.spice 
> plot out vs time in
> exit
```

🖼️
![vim day3](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-4/Day-3/Lab/vim%20day3.png)



🖼️
![day3 inv vtc](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-4/Day-3/Lab/day3%20inv%20vtc.jpeg)



🖼️
![vim day3 tran](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-4/Day-3/Lab/vim%20day3%20tran.png)




🖼️
![day3 inv tran](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-4/Day-3/Lab/day3%20inv%20tran.jpeg)
