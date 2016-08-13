Simulations of increasing complexity

2 Level System 
Meant to depict the coherent laser-matter interaction between two levels within an atom, the conditions necessary for simple Coherent Population Return(CPR) as well as for total excitation to the second level, no excitation at all or anything in between in a controlled fashion.

3 Level System 
As in the previous simulation, our objective is to control de population of different levels through coherent laser-matter interaction For this case more conditions must be met for maximum coherence between levels 1 and 3 while the previous simulation of a 2 level system can be reproduced as well within this simulation given the correct initial conditions, values of Rabi frequencies(Capital Omegas), pulse durations(tau)

Propagation within a crystal in a 3 Level System

  * Creación Popu_Cohe_Rabi_Propagacion MB 2 Photon CPR v_4
  Generates files with the Population of every level, the coherence between those levels and the laser pulse shape and peak frequency

  The following programs read each of the previous aspects
    -Lectura Cohe Propagacion MB 2 Photon CPR_v2
    -Lectura Popu Propagacion MB 2 Photon CPR_v2
    -Lectura Rabi Propagacion MB 2 Photon CPR_v2

  * Creación Trigger_and_Generated_Propagacion MB 2 Photon CPR
  Using the program Creación Popu_Cohe_Rabi_Propagacion MB 2 Photon CPR v_4 and adding the trigger laser we generate a file with the evolution of this given trigger laser and a generated laser which is the signal we are to read

  * Lectura Trigger_and_Generated_Propagacion MB 2 Photon CPR
  This is the program we use to read the evolution of the trigger and generated pulses
