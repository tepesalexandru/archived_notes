Transformarile geometrice pot fi:
- 2D (bi-dimensionale)
- 3D (tri-dimensionale)

Transformarile esentiale sunt `translatia`, `rotatia` si `scalare`.

### Preliminarii matematice
Pentru a intelege transformarile geometrice, ne vom folosi de concepte matematice precum `vectorii` si `matricile`.

### Vectorii si proprietatile lor
Vom folosi vectorii pentru a reprezenta: `pozitia punctelor` intr-un sistem cartezian de referinta, `orientarea suprafetelor` in spatiu, `comportamentul luminii` in contact cu obiecte transparente si solide si pentru multe alte scopuri.

- Pentru vectorii in 2D vom folosi un n-uplu cu doua elemente
- Pentru vectorii in 3D vom folosi un n-uplu cu trei elemente

Pe acesti vectori vom aplica doua operatii: `adunare` si `inmultire cu numere reale`.

Exista vectorul `0` cu proprietatea ca `0 + v = v`.
Exista inversul oricarei vector `v` acesta fiind `w` cu proprietatea `v + m = 0`
Inmultirea cu scalar are urmatoarele proprietati:

```latex
(ab)V = a(bV)
1V = V
(a + b)V = aV + bV
a(V + W) = aV + aW
```

Pentru a aduna doi vectori:

![[Pasted image 20221106150716.png]]

Bine de stiut: `metoda paralelogramului`.

### Produsul scalar al vectorilor
Vectorii v si w:

![[Pasted image 20221106151354.png]]

Produsul `scalar` (sau `intern`) a doi vectori `v` si `w` se noteaza $v\cdot\ w$ , si este egal cu:

![[Pasted image 20221106151334.png]]

Distanta din plan `(x, y)` pana la originea `(0, 0)` este $\sqrt{x^2 \cdot y^2}$

In general, distanta de la un punct n-dimensional pana la origine va fi 

![[Pasted image 20221106151639.png]]

Lungimea unui vector n-dimensional este $\sqrt{v \cdot v}$ , pe care o vom nota cu `||v||`.
Dinstanta dintre doua puncte `P` si `Q` in spatiul n-dimensional va fi lungimea vectorului `Q - P`.

`Normalizarea` unui vector inseamna transformarea dimensiunii sale la `1`
Pentru a normaliza un vector, vom calcula `v' = v / ||v||`. Vectorul care rezulta are lungime `1` si se numeste `versor`.

`Unghiul dintre vectorii` v si w este 

![[Pasted image 20221106152717.png]]

![[Pasted image 20221106152924.png]]

## Transformarile 2D
Putem `translata` punctele din planul xOy adaugand translatii coordonatelor punctelor.

Pentru a muta un punct `P(x, y)` intr-un punct `P'(x', y')`. Vom adauga `dx` si `dy` coordonatelor initiale:

![[Pasted image 20221106153414.png]]

Punctele pot fi `scalate` (intinse) cu `sx` si cu `sy` prin inmultirie:

![[Pasted image 20221106154257.png]]

Se numeste o `scalare diferentiata` daca `sx != dy`. Altfel, se numeste `scalare uniforma`.

Punctele pot fi `rotite` cu un unghi `theta`  in jurul originii. O rotatie se defineste astfel:

![[Pasted image 20221106154511.png]]

![[Pasted image 20221106154531.png]]

## Coordonatele omogene si reprezentarea matriceala a transformarilor 2D

Reprezentarile matriceala pentru `translatie`, `scalare` si `rotatie` sunt respectiv:

```latex
P' = T + P # translatie
P' = S * P # scalare
P' = R * P # rotatie
```
- In `coordonate omogene`, un punct 2D este reprezentat printr-un triplet `(x, y, W)`.

Formula `translatiei` pentru coordonate omogene este urmatoarea:

![[Pasted image 20221113183012.png]]

Formula de mai sus se poate nota si astfel:

![[Pasted image 20221113183138.png]]

![[Pasted image 20221113183154.png]]

Formula `scalarii` pentru coordonate omogene este urmatoarea:

![[Pasted image 20221113183608.png]]

Formula `rotatiei` pentru coordonate omogene este urmatoarea:

![[Pasted image 20221113183655.png]]

`Transformarile afine` au proprietatea ca pastreaza paralelismul dreptelor insa nu si lungimile sau unghiurile. Ele sunt produsul unei succesiuni arbitrare de rotatii, translatii si scalari.

`Transformarile rigide` sunt cele care nu distorsioneaza obiectul in niciun fel.

## Compunerea transformarilor 2D
