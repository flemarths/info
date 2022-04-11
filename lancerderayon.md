## Sujet Centrale IPT

### I-Géométrie 

#### Q1: *Écire la fonction d'entête* 

```
def vect(A,B):
	res=np.array(3)
    for i in range [0,3]:
	    res[i]=B[i]-A[i]
    return res
```  
  
ou encore  
  
```
def vect(A,B):  
    return B-A
```

#### Q2: *Écrire une fonction d'entête*

```
def ps(v1,v2):
    return np.inner(v1,v2)
```

#### Q3: *Écrire une fonction d'entête*

```
def norme(v):
	return np.sqrt(ps(v,v))
```

#### Q4: *Écrire une fonction d'entête*

```
def unitaire(v):
	return (1/norme(v))*v
```

#### Q5: Que font les fonctions **pt**, **dir** et **ra** ci-dessous ?

  * La fonction *pt* retourne le point du rayon (S,u) de mesure algébrique *t* 
  devant être positive ou nulle.  
  
  * La fonction *dir* retourne le vecteur unitaire support du vecteur AB,
  et donc le vecteur directeur de la droite (AB).  
  
  * La fonction *ra* retourne le rayon d'origine A et de vecteur unitaire le
  vecteur directeur de (AB) : elle retourne donc le rayon d'origine *A* et 
  passant par *B*
  

#### Q6: *Écrire une fonction d'entête*

```
def sp(A,b):
	return (A, norme(vec(A,B)))
```

#### Q8: *Écrire une fonction d'entête*

 ```
def intersection(r,s):
	(C,rc) = s #sphère de centre C et de rayon rc
	(A, u) = r #rayon d'origine A et de vecteur directeur u
	a = 1
	b = 2*ps(u, vec(C,A))
	c = ps(vec(C,A),vec(C,A))-rc**2
	delta = b**2-4*a*c #Calcul du discriminant
	if delta < 0:
		return None
	else:
		#premier point est celui de distance minimale
		#soit donc pour la solution avec -racine de delta
		t = (-b-np.sqrt(delta))/(2*a)
		#Résultat valide seulement pour t>0
		if t > 0:
			return (pt(r,t),t)
		else:
			return None
```

### II-Optique

#### Q9: Une source lumineuse ponctuelle S ne peut être vue d'un point P de la shpère (C,r) que si la source est au-dessus de l'horizon de P, défini comme le plan tangent à la sphère en P. Donner une condition géométrique pour que la source soit au-dessus de l'horizon.

Il suffit de remarquer que le plan d'horizon du point P est de vecteur normal N, vecteur unitaire obtenu à partir du vecteur CP, et que selon la position du point S, l'angle theta entre le vecteur N et le vecteur PS sera tel que:

* theta appartient à [0,pi/2[ si S est situé au-dessus de l'horizon ;

* theta = pi/2 si S appartient à l'horizon ;

* theta appartient à ]pi/2,pi] si S est situé au-dessous de l'horizon ;

On peut alors exploiter avantageusement les propriétés du produit scalaire, sachant que le signe du résultat sera le même que si l'on utilise le vecteur normal N ou le vecteur CP, pour en déduire que S sera situé au-dessus de l'horizon de P si CP.PS > 0.

#### Q10: *Écrire une fonction d'entête*

```
def au_dessus(s,P,src):
	(C,rc) = s
	return ps(vec(P,C),vec(P,src)) > 0
```

#### Q11: *Écrire une fonction d'entête*

```
def visible(obj,j,P,src):
	if au_dessus(obj[j],P,src):
		r = ra(src,P)
		d = norme(vec(src,P)
		for i in range(len(obj)):
			if i != j:
			M = intersection(r,obj[j])
			if M != None and M[1] < d :
				return False
	    return True
	else:
		return False
```

#### Q12: *Écrire une fonction d'entête*

```
def couleur_diffusée(r,Cs,N,kd):
	(S,u) = r
	cos_theta = ps(N,-u)
	return kd*Cs*cos_theta
```


fze,gn
lgs,ùqsnù<n
