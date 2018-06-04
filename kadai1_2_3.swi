1.

?- trace(my_append).
%         my_append/3: [call,redo,exit,fail]
true.
[debug]  ?- my_append([a,b],[c,d],X).
 T Call: (7) my_append([a, b], [c, d], _G9134)
 T Call: (8) my_append([b], [c, d], _G9216)
 T Call: (9) my_append([], [c, d], _G9219)
 T Exit: (9) my_append([], [c, d], [c, d])
 T Exit: (8) my_append([b], [c, d], [b, c, d])
 T Exit: (7) my_append([a, b], [c, d], [a, b, c, d])
X = [a, b, c, d].

→[c,d]にｂが加わり、そしてaが加わる
→my_append([X|Y],Z,[X|U]):-my_append(Y,Z,U)で生じている


2.


?- trace(my_reverse).
%         my_reverse/2: [call,redo,exit,fail]
true.
[debug]  ?- my_reverse([a,b,c],X).
 T Call: (7) my_reverse([a, b, c], _G1867)
 T Call: (8) my_reverse([b, c], _G1984)
 T Call: (9) my_reverse([c], _G1984)
 T Call: (10) my_reverse([], _G1984)
 T Exit: (10) my_reverse([], [])
 T Exit: (9) my_reverse([c], [c])
 T Exit: (8) my_reverse([b, c], [c, b])
 T Exit: (7) my_reverse([a, b, c], [c, b, a])
X = [c, b, a].

→ｃの後ろにｂを入れて、そのｂの後ろにaを入れている
→my_reverse([X | Y], Z) :- my_reverse(Y, W), append(W, [X], Z)の部分のappendで、リストの最後尾に入れている


3.


double([],[]):-!.
double([L1|L],[L1,L1|L2]):-double(L,L2).

