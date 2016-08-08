ClearAll["Global`*"]

The energies of the states |1>, |2>, as well as the energy of the interaction are

Subscript[E, 1], Subscript[E, 2], Subscript[E, int] = [HBar] [CapitalOmega] Cos[[Omega] t - [Phi]];

The matrix with the ground state energies is

MatrixForm[{{Subscript[E, 1], 0}, {0, Subscript[E, 2]}}]

!( TagBox[ RowBox[{"(", "", GridBox[{ { SubscriptBox["E", "1"], "0"}, {"0", SubscriptBox["E", "2"]} }, GridBoxAlignment->{ "Columns" -> {{Center}}, "ColumnsIndexed" -> {}, "Rows" -> {{Baseline}}, "RowsIndexed" -> {}}, GridBoxSpacings->{"Columns" -> { Offset[0.27999999999999997], { Offset[0.7]}, Offset[0.27999999999999997]}, "ColumnsIndexed" -> {}, "Rows" -> { Offset[0.2], { Offset[0.4]}, Offset[0.2]}, "RowsIndexed" -> {}}], "", ")"}], Function[BoxForme$, MatrixForm[BoxForme$]]])

These are associated with the states Subscript[c, 1 ]and Subscript[c, 2 ] whose phases are Subscript[[Xi], 1 ]and Subscript[[Xi], 2 ]. We choose these phases in interaction picture so that

Subscript[[Xi], 1 ] = Subscript[E, 1] t /[HBar] Subscript[[Xi], 2 ] = Subscript[E, 1] t/[HBar] + [Omega]t

(t Subscript[E, 1])/[HBar]

[Omega]t + (t Subscript[E, 1])/[HBar]

Where [Omega] is the frequency of the laser and Subscript[[Omega], 0]is the difference in frequency between the two energy levels that help us define the detuning [CapitalDelta]

[CapitalDelta] = [HBar] (Subscript[[Omega], 0] - [Omega])

[HBar] (-[Omega] + Subscript[[Omega], 0])

which give a hamiltonian such as

H = MatrixForm{{0, [CapitalOmega/ 2}, {[CapitalOmega] (!(TraditionalForm`1\ + \ *SuperscriptBox[(e), (2 i[Omega]t)]))/2, [CapitalDelta]}}]

!( TagBox[ RowBox[{"(", "", GridBox[{ {"0", RowBox[{ FractionBox["1", "2"], " ", RowBox[{"(", RowBox[{"1", "+", SuperscriptBox["e", RowBox[{"2", " ", "i[Omega]t"}]]}], ")"}], " ", "[CapitalOmega]"}]}, { RowBox[{ FractionBox["1", "2"], " ", RowBox[{"(", RowBox[{"1", "+", SuperscriptBox["e", RowBox[{"2", " ", "i[Omega]t"}]]}], ")"}], " ", "[CapitalOmega]"}], RowBox[{"[HBar]", " ", RowBox[{"(", RowBox[{ RowBox[{"-", "[Omega]"}], "+", SubscriptBox["[Omega]", "0"]}], ")"}]}]} }, GridBoxAlignment->{ "Columns" -> {{Center}}, "ColumnsIndexed" -> {}, "Rows" -> {{Baseline}}, "RowsIndexed" -> {}}, GridBoxSpacings->{"Columns" -> { Offset[0.27999999999999997], { Offset[0.7]}, Offset[0.27999999999999997]}, "ColumnsIndexed" -> {}, "Rows" -> { Offset[0.2], { Offset[0.4]}, Offset[0.2]}, "RowsIndexed" -> {}}], "", ")"}], Function[BoxForme$, MatrixForm[BoxForme$]]])

In Rotating Wave Approximation RWA 1+e^(2i[Omega]t)[TildeEqual]1 when averaged over time

H = MatrixForm[{{0, [CapitalOmega]/2}, {[CapitalOmega]/2, [CapitalDelta]}}]

!( TagBox[ RowBox[{"(", "", GridBox[{ {"0", FractionBox["[CapitalOmega]", "2"]}, { FractionBox["[CapitalOmega]", "2"], RowBox[{"[HBar]", " ", RowBox[{"(", RowBox[{ RowBox[{"-", "[Omega]"}], "+", SubscriptBox["[Omega]", "0"]}], ")"}]}]} }, GridBoxAlignment->{ "Columns" -> {{Center}}, "ColumnsIndexed" -> {}, "Rows" -> {{Baseline}}, "RowsIndexed" -> {}}, GridBoxSpacings->{"Columns" -> { Offset[0.27999999999999997], { Offset[0.7]}, Offset[0.27999999999999997]}, "ColumnsIndexed" -> {}, "Rows" -> { Offset[0.2], { Offset[0.4]}, Offset[0.2]}, "RowsIndexed" -> {}}], "", ")"}], Function[BoxForme$, MatrixForm[BoxForme$]]])

So the Schrödinger equation Subscript[c, i]'=H*Subscript[c, i] gives the following system of equations where we suppose the laser is in resonance with the difference in frequencies of the two levels ([CapitalDelta]=0)

c1'[t] == -I [CapitalOmega][t]c2[t]/2; c2'[t] == -I [CapitalOmega][t]c1[t]/2 - I [CapitalDelta] c2[t];

Value of the bandwidth([Tau]) and its inverse at half the amplitude are

[Tau] = 5; 1/[Tau]

1/5

Now we plot these values to find the shape of the gaussian in the time span that goes between(all constatnts and variables are in nanoseconds):

ti = 0; tf = 200;

The frequency when detuned by one peak Rabi is(multiplied by ln(2) for the BW we choose)

Manipulate[ Plot[[CapitalOmega]0Exp[-2 Log2^2/[Tau]^2], {t, ti, tf}, PlotRange -> All], {{[CapitalOmega]0, Sqrt[[Pi] Log[4]]/[Tau]}, 0, 10, 2Sqrt[[Pi] Log[4]]/[Tau]}]

Manipulate[Plot[[CapitalOmega]0Exp[-2Log[2]((t - (tf - \ ti)/2)^2/[Tau]^2)], {t, ti, tf}, PlotRange -> All], {{[CapitalOmega]0, Sqrt[PiLog[4]]/5}, 0, 10, (2Sqrt[PiLog[4]])/5}]

For operating purposes we write down the Rabi frequency relative to its peak

[CapitalOmega]rel[t_] := Exp[-2 Log2^2/[Tau]^2];

As well as the representation of the population for varying detuning [CapitalDelta] and peak Rabi Subscript[[CapitalOmega], 0]

Manipulate[Block[{c1Solved, sc2Solved, c1, c2, t, s},

s = NDSolve[{c1'[t] == -I [CapitalOmega]0[CapitalOmega]rel[t]c2[t]/2, c2'[t] == -I [CapitalOmega]0[CapitalOmega]rel[t]c1[t]/2 - I [CapitalDelta] c2[t], c1[ti] == 1, c2[ti] == 0}, {c1[t], c2[t]}, {t, ti, tf}]; c1Solved = c1[t] /. s[[1, 1]]; c2Solved = c2[t] /. s[[1, 2]]; Plot[{c1SolvedConjugate[c1Solved], c2SolvedConjugate[c2Solved]}, {t, 90, 110}, PlotRange -> All, PlotLegends -> {"Ground state", "Excited state"}]] , {{[CapitalDelta], 0}, 0, 2, 0.1}, {{[CapitalOmega]0, Sqrt[[Pi] Log[4]]/[Tau]}, 0, 20, Sqrt[[Pi] Log[4]]/[Tau]}]

Manipulate[Block[{c1Solved, sc2Solved, c1, c2, t, s}, s = NDSolve[{Derivative[1][c1][t] == \ (-I)[CapitalOmega]0[CapitalOmega]rel[t](c2[t]/2), Derivative[1][c2][t] == \ (-I)[CapitalOmega]0[CapitalOmega]rel[t](c1[t]/2) - \ I[CapitalDelta]c2[t], c1[ti] == 1, c2[ti] == 0}, {c1[t], c2[t]}, {t, ti, tf}]; c1Solved = c1[t] /. s[[1,1]]; c2Solved = c2[t] /. s[[1,2]]; Plot[{c1SolvedConjugate[c1Solved], c2SolvedConjugate[c2Solved]}, {t, 90, 110}, PlotRange -> All, PlotLegends -> {"Ground state", "Excited state"}]], {{[CapitalDelta], \ 1.5000000000000002}, 0, 2, 0.1}, {{[CapitalOmega]0, 9.182381685410135}, 0, 20, Sqrt[Pi*Log[4]]/5}]

The effective Rabi frequency is Subscript[[CapitalOmega], eff]

Manipulate[{[CapitalOmega]0^2/ Sqrt[[CapitalOmega]0^2 + [CapitalDelta]^2]}, {{[CapitalDelta], 0}, 0, 100, 5}, {{[CapitalOmega]0, 1}, 0, 10, 0.5}]

Manipulate[{[CapitalOmega]0^2/Sqrt[[CapitalOmega]0^2 + [CapitalDelta]^2]}, \ {{[CapitalDelta], 0}, 0, 100, 5}, {{[CapitalOmega]0, 1}, 0, 10, 0.5}]
