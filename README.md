# MATHS_SAE_S2.04
## Projet réalisé par :
 - Mathias PLACIDE--CONTRERAS
 - Lukas SIMOES
## Exercice 1
### 1. **Pour toutes les variables numériques, donner sous forme de tableau :** 
> [!NOTE]
> Script pour calculer moyenne, écart-type, minimum, maximum, quartiles.
```
function [tab] = resume_stats(var)

   
    moy = mean(var);
    ecart_type = stdev(var);
    min_num = min(var);
    max_num = max(var);
    quartiles = quart(var);

    tab = [ moy; ecart_type; min_num; max_num; quartiles];

    mprintf("Moyenne    │ %.2f \n", moy);
    mprintf("Écart-type │ %.2f \n", ecart_type);
    mprintf("Minimum    │ %.2f \n", min_num);
    mprintf("Maximum    │ %.2f \n", max_num);
    mprintf("Quartiles  │ %.2f \n", quartiles);
endfunction
```
> [!NOTE]
>  Lancer le script avec la commande `exec("resume_stats.sci")`
>  Lire des entiers numériques avec la commande `data = csvRead("data.csv")`

### **Student_ID :**

``` 
---> studentid = data(2:$,1)
---> resume_stats(var)

Résultat :
Moyenne    │ 353.00 
Écart-type │ 203.66 
Minimum    │ 1.00 
Maximum    │ 705.00 
Quartiles  │ 176.75 
Quartiles  │ 353.00 
Quartiles  │ 529.25 
```

### **Age :**

```
---> age = data(2:$,2)
---> resume_stats(age)

Résultat :
Moyenne    │ 20.66 
Écart-type │ 1.40 
Minimum    │ 18.00 
Maximum    │ 24.00 
Quartiles  │ 19.00 
Quartiles  │ 21.00 
Quartiles  │ 22.00 
```

### **Avg_Daily_Usage_Hours :**

``` 
---> usagehours = data(2:$,6)
---> resume_stats(usagehours)

Résultat :
Moyenne    │ 4.92 
Écart-type │ 1.26 
Minimum    │ 1.50 
Maximum    │ 8.50 
Quartiles  │ 4.10 
Quartiles  │ 4.80 
Quartiles  │ 5.80 
```

### **Sleep_Hours_Per_Night :**

``` 
---> sleephours = data(2:$,9)
---> resume_stats(sleephours)

Résultat :
Moyenne    │ 6.87 
Écart-type │ 1.13 
Minimum    │ 3.80 
Maximum    │ 9.60 
Quartiles  │ 6.00 
Quartiles  │ 6.90 
Quartiles  │ 7.70 
```

### **Mental_Health_Score :**

``` 
---> mentalhealth = data(2:$,10)
---> resume_stats(mentalhealth)

Résultat :
Moyenne    │ 6.23 
Écart-type │ 1.11 
Minimum    │ 4.00 
Maximum    │ 9.00 
Quartiles  │ 5.00 
Quartiles  │ 6.00 
Quartiles  │ 7.00  
```

### 2. **Pour les autres variables, donner les effectifs des différentes valeurs par ordre décroissant (genre, niveau scolaire, pays, etc.)** :
> [!NOTE]
>  Script pour récuperer l'effectif et trier les valeurs par ordre décroissant
>  Lancer le script avec la commande `exec("freq_desc.sci")`
```
function freq_desc(var)
    valeurs = unique(var);
    effectifs = zeros(1, size(valeurs, '*'));
    
    for i = 1:size(valeurs, '*')
        effectifs(i) = sum(var == valeurs(i));
    end

    [effectifs_sorted, ordre] = gsort(effectifs, "g", "d");
    valeurs_sorted = valeurs(ordre);

    for i = 1:size(valeurs, '*')
        mprintf("%s : %d\n", string(valeurs_sorted(i)), effectifs_sorted(i));
    end
endfunction
```
> [!NOTE]
>  Lire en chaîne de caractères avec la commande `data = read_csv("data.csv")`

### **Gender :**
```
---> gender = data(2:$,3)
---> freq_desc(gender)

Résultat :
Female : 353
Male : 352
```

### **Academic_Level :**
```
---> AcademLevel = data(2:$,4)
---> freq_desc(gender)

Résultat :
Undergraduate : 353
Graduate : 325
High School : 27
```

### **Country :**
```
---> country = data(2:$,5)
---> freq_desc(country)

Résultat :
India : 53
USA : 40
Canada : 34
Denmark : 27
France : 27
Ireland : 27
Mexico : 27
Spain : 27
Switzerland : 27
Turkey : 27
UK : 22
Italy : 21
Japan : 21
Russia : 21
Bangladesh : 20
Maldives : 19
Nepal : 19
Pakistan : 19
Sri Lanka : 19
China : 16
Poland : 16
Australia : 14
Germany : 14
South Korea : 13
Brazil : 8
Finland : 8
Malaysia : 8
Netherlands : 8
New Zealand : 8
Singapore : 8
UAE : 8
Afghanistan : 1
Albania : 1
Andorra : 1
Argentina : 1
Armenia : 1
Austria : 1
Azerbaijan : 1
Bahamas : 1
Bahrain : 1
Belarus : 1
Belgium : 1
Bhutan : 1
Bolivia : 1
Bosnia : 1
Bulgaria : 1
Chile : 1
Colombia : 1
Costa Rica : 1
Croatia : 1
Cyprus : 1
Czech Republic : 1
Ecuador : 1
Egypt : 1
Estonia : 1
Georgia : 1
Ghana : 1
Greece : 1
Hong Kong : 1
Hungary : 1
Iceland : 1
Indonesia : 1
Iraq : 1
Israel : 1
Jamaica : 1
Jordan : 1
Kazakhstan : 1
Kenya : 1
Kosovo : 1
Kuwait : 1
Kyrgyzstan : 1
Latvia : 1
Lebanon : 1
Liechtenstein : 1
Lithuania : 1
Luxembourg : 1
Malta : 1
Moldova : 1
Monaco : 1
Montenegro : 1
Morocco : 1
Nigeria : 1
North Macedonia : 1
Norway : 1
Oman : 1
Panama : 1
Paraguay : 1
Peru : 1
Philippines : 1
Portugal : 1
Qatar : 1
Romania : 1
San Marino : 1
Serbia : 1
Slovakia : 1
Slovenia : 1
South Africa : 1
Sweden : 1
Syria : 1
Taiwan : 1
Tajikistan : 1
Thailand : 1
Trinidad : 1
Ukraine : 1
Uruguay : 1
Uzbekistan : 1
Vatican City : 1
Venezuela : 1
Vietnam : 1
Yemen : 1
```

### **Most_Used_Platform :**
```
---> mostusedplat = data(2:$,7)
---> freq_desc(mostusedplat)

Résultat :
Instagram : 249
TikTok : 154
Facebook : 123
WhatsApp : 54
Twitter : 30
LinkedIn : 21
WeChat : 15
Snapchat : 13
KakaoTalk : 12
LINE : 12
VKontakte : 12
YouTube : 10
```

### **Relationship_Status :**
```
---> relationstatus = data(2:$,11)
---> freq_desc(relationstatus)

Résultat :
Single : 384
In Relationship : 289
Complicated : 32
```

## Exercice 2
> [!NOTE]
> Script d'affichage
> Lancer le script avec la commande `exec("effecgraph.sci")`
```
function effecgraph(var)
    bar(var(2))
    ax=gca();
    ax.x_ticks.labels=var(1);
endfunction
```

### 1. **Donner, sous forme graphiqe, la répartion des âges et des genres des étudiants :** 
```
---> data = read_csv("data.csv")

---> age = data(2:$,2)
---> tab = tabul(age)

---> effecgraph(tab)
---> xtitle("la répartion des âges des étudiants", "Age", "Nombre Etudiants")
```
![graphe age](/Image/premier.png)
```
---> data = read_csv("data.csv")

---> gender = data(2:$,3)
---> tab = tabul(gender)

---> effecgraph(tab)
---> xtitle("Des genres des étudiants", "Genres", "Nombre Etudiants")
```
![graphe gender](/Image/premier2.png)
### 2. **Donner, sous forme graphique, les effectifs des 10 premiers pays :** 
```
---> data = read_csv("data.csv")

---> country = data(2:$,5)
---> for i = 1:10
        pays(i) = sum(country == country(i));
        nom(i) = string(country(i));
        mprintf("%s : %d\n", nom(i), pays(i));
    end
---> element = list(nom, pays)

---> effecgraph(element)
---> xtitle("Les effectifs des 10 premiers pays", "Pays", "Effectifs")
```
![graphe 10 premiers pays](/Image/deuxiéme.png)
### 3. **Donner, sous forme graphique, les effectifs des niveaux scolaires :** 
```
---> data = read_csv("data.csv")

---> AcademLevel = data(2:$,4)
---> tab = tabul(AcademLevel)

---> effecgraph(tab)
---> xtitle("Les effectifs des niveaux scolaires", "Niveaux Scolaires", "Effectifs")
```
![graphe 10 premiers pays](/Image/troisieme.png)
### 4. **Donner sous forme graphique la distribution du temps moyen d'utilisation des réseaux sociaux :** 
```
---> data = csvRead("data.csv")

---> usagehours = data(2:$,6)
---> tab = tabul(usagehours)

---> bar(tab(:,1),tab(:,2))
---> xtitle("La distribution du temps moyen utilisation des réseaux sociaux.", "Temps Moyen", "Etudiants")
```
![graphe 10 premiers pays](/Image/quatrieme.png)
### 5. **Donner sous forme graphique, dans l'odre décroissant, les effectifs des réseaux sociaux les plus utilisés :** 
```
function freq_desc(var)

    valeurs = unique(var);
    effectifs = zeros(1, size(valeurs, '*'));
    
    for i = 1:size(valeurs, '*')
        effectifs(i) = sum(var == valeurs(i));
    end

    [effectifs_sorted, ordre] = gsort(effectifs, "g", "i");
    valeurs_sorted = valeurs(ordre);

    for i = 1:size(valeurs, '*')
        mprintf("%s : %d\n", string(valeurs_sorted(i)), effectifs_sorted(i));
    end

endfunction

```
## Exercice 3
### **Comparer graphiquement (on pourra utiliser des boîtes à moustaches) :**
```
---> data = read_csv("data.csv")
---> col_age    = find(data(1,:) == "Age");
---> col_usage  = find(data(1,:) == "Avg_Daily_Usage_Hours");
---> col_gender = find(data(1,:) == "Gender");
---> col_score  = find(data(1,:) == "Addicted_Score");
---> col_acad   = find(data(1,:) == "Academic_Level");

---> ages    = evstr(data(2:$, col_age));        
---> usages  = evstr(data(2:$, col_usage));      
---> scores  = evstr(data(2:$, col_score));      
---> genders = data(2:$, col_gender);            
---> acads   = data(2:$, col_acad);    

```
### **1.Le temps d'utilisation des réseaux suivants les deux groupes d'âge [16-20] et [21-25] :**
```
---> idx_16_20 = find(ages >= 16 & ages <= 20);
---> idx_21_25 = find(ages >= 21 & ages <= 25);

---> group1 = usages(idx_16_20);
---> group2 = usages(idx_21_25);

---> colonne-par-groupe (taille égalisée par %nan)
---> nMax = max(length(group1), length(group2));
---> groupMatAge = %nan * ones(nMax, 2);
---> groupMatAge(1:length(group1),1) = group1(:);
---> groupMatAge(1:length(group2),2) = group2(:);

---> scf();
---> boxplot(groupMatAge);
---> xtitle("Temps quotidien sur les réseaux selon le groupe d’âge", "", "Heures / jour");
---> ax = gca();
---> ax.x_ticks = tlist(["ticks","locations","labels"], [1 2], ["16-20" "21-25"]);
```
![Boîte a moustache](/Image/ex3_1.png)
### **2.Le temps d'utilisation des réseaux suivants le genre. :**
```
---> idx_F = find(genders == "Female");
---> idx_M = find(genders == "Male");

---> gF = usages(idx_F);
---> gM = usages(idx_M);

---> nMax = max(length(gF), length(gM));
---> groupMatGender = %nan * ones(nMax, 2);
---> groupMatGender(1:length(gF), 1) = gF(:);
---> groupMatGender(1:length(gM), 2) = gM(:);

---> scf();
---> boxplot(groupMatGender);
---> xtitle("Temps quotidien sur les réseaux\nselon le genre", "", "Heures / jour");
---> ax = gca();
---> ax.x_ticks = tlist(["ticks","locations","labels"], [1 2], ["Female" "Male"]);
```
![Boîte a moustache](/Image/ex3_2.png)
### **3.Le score d'addiction suivant le niveau académique. :**
```
---> idx_HS = find(acads == "High School");
---> idx_UG = find(acads == "Undergraduate");
---> idx_GR = find(acads == "Graduate");

---> gHS = scores(idx_HS);
---> gUG = scores(idx_UG);
---> gGR = scores(idx_GR);

---> nMax = max([length(gHS) length(gUG) length(gGR)]);
---> groupMatAcad = %nan * ones(nMax, 3);
---> groupMatAcad(1:length(gHS), 1) = gHS(:);
---> groupMatAcad(1:length(gUG), 2) = gUG(:);
---> groupMatAcad(1:length(gGR), 3) = gGR(:);

---> scf();
---> boxplot(groupMatAcad);
---> xtitle("Score d’addiction aux réseaux\nselon le niveau académique", "", "Score (/10)");
---> ax = gca();
---> ax.x_ticks = tlist(["ticks","locations","labels"], [1 2 3], ["High School" "Undergraduate" "Graduate"]);
```
![Boîte a moustache](/Image/ex3_3.png)

## Exercice 4
### **Comparer graphiquement l'impact de la durée d'utilisation des réseaux sur la performance académique. On regroupera les usages en 4 sous-groupes : utilisation faible (0-2h), modérée (2-4h), élevée (4-6h) et très élevé (6-12h). :**
```
---> data = read_csv("data.csv")
---> heures = evstr(data(2:$,6))
---> performances = data(2:$,8)
```
> [!NOTE]
> Script pour récuper les Yes et No en valeurs booléennes
> Lancer le script avec la commande `exec("booleen.sci")`
```
function[tableau] = booleen(tab, string)
    taille = size(tab, 1);
    tableau = zeros(taille,0)

    for i = 1:taille
        if tab(i) == string then
            tableau(i)=1;
        else
            tableau(i)=0;
        end
    end
endfunction
```
```
---> exec("booleen.sci")
---> bool_performances = booleen(performances,"Yes")

---> [trie_heures, indice] = gsort(heures, "g", "d")
---> trie_performances= bool_performances(indice)
```
> [!NOTE]
> Script pour attribuer les valeurs par catégories
> Lancer le script avec la commande `exec("attribuCate.sci")`
```
function [categorie] = attribuCate(heures)
    categorie(heures >=0 & heures <2) = 1 
    categorie(heures >=2 & heures <4) = 2 
    categorie(heures >=4 & heures <6) = 3 
    categorie(heures >=6 & heures <12) = 4 
endfunction
```
> [!NOTE]
> Script pour faire la moyenne en pourcentage et afficher sous forme de graphique
> Lancer le script avec la commande `exec("affichageCate.sci")`
```
function affichageCate(categorie, bool_performances)
    moyennes = zeros (4,1)
    for i =1:4
        indices = find(categorie == i)
        moyennes(i) = mean(bool_performances(indices))
    end
    txt_categorie = ["0-2h","2-4h","4-6h","6-12h"]
    titre = "Impact de utilisation des réseaux sociaux sur la performance académique en pourcentage."
    bar(moyennes*100);
    xtitle(titre);
    ax=gca();
    ax.x_ticks = tlist(["ticks", "locations", "labels"],[1,2,3,4], txt_categorie);
endfunction
```
```
---> categorie = attributionCategorie(trie_heures)
---> affichageMoyennesCategorie(categorie,trie_performances)
```
![l'impact de la durée d'utilisation des réseaux sur la performance académique](/Image/exo4.png)

## Exercice 5
### **Comparer graphiquement le score d'addiction en fonction de la qualité de sommeil. On regroupera les étudiant(e)s en 4 sous-groupes suivant la durée de sommeil (<5,[5,7], [7,9], >9) :**
```
---> data = csvRead("data.csv")

---> temp = find(data(2:$,9)<5)
---> groupe1 = data(2:$,13)(temp)

---> temp = find(data(2:$,9)>=5 & data(2:$,9)<=7 )
---> groupe2=data(2:$,13)(temp)

---> temp = find(data(2:$,9)>7 & data(2:$,9)<9 )
---> groupe3=data(2:$,13)(temp)

---> temp = find(data(2:$,9)>9)
---> groupe4 = data(2:$,13)(temp)

---> x = [1, 2, 3, 4]
---> y = [min(groupe1) mean(groupe1) max(groupe1);min(groupe2) mean(groupe2) max(groupe2);min(groupe3) mean(groupe3) max(groupe3);min(groupe4) mean(groupe4) max(groupe4)]
---> bar(x,y)
---> xtitle("score addiction en fonction de la qualité de sommeil")
---> legend(['Min', 'Moyenne', 'Max'], "ul")
```
![graphe addiction en fonction du sommeil](/Image/cinquiéme.png)

## Exercice 6
### **Afficher le nombre d'heures de sommeil en fonction du temps d'utilisation des réseaux, pour les hommes et les femmes :**
```
---> data = read_csv("data.csv")
---> gender = data(2:$, 3); // On saute la ligne d'en-tête
---> reseaux = evstr(data(2:$, 6));
---> sommeil = evstr(data(2:$, 9));


---> indices_h = find(gender == "Male");
---> indices_f = find(gender == "Female");


---> reseaux_h = reseaux(indices_h);
---> sommeil_h = sommeil(indices_h);


---> reseaux_f = reseaux(indices_f);
---> sommeil_f = sommeil(indices_f);

---> plot(reseaux_h, sommeil_h, 'bo');
---> plot(reseaux_f, sommeil_f, 'r+');


---> xlabel("Temps d'utilisation des réseaux (h)");
---> ylabel("Nombre d'heures de sommeil");
---> legend("Hommes", "Femmes");
---> title("Sommeil vs Réseaux sociaux")
```
![graphe heures de sommeil en fonction de l'utilisation des réseaux sociaux](/Image/sixiéme.png)

## Exercice 7 
### **Conflits selon heures de sommeil :**
```
---> data = read_csv("data.csv");

---> col_sleep = find(data(1,:) == "Sleep_Hours_Per_Night");
---> col_conflict = find(data(1,:) == "Conflicts_Over_Social_Media");

---> sleep = evstr(data(2:$, col_sleep));
---> conflicts = evstr(data(2:$, col_conflict));

---> bins = 4:0.5:9.5;
---> nBins = length(bins);
---> meanConflicts = zeros(nBins, 1);

---> for i = 1:nBins
        idx = find(abs(sleep - bins(i)) < 0.25); 
        if ~isempty(idx) then
            meanConflicts(i) = mean(conflicts(idx));
        else
            meanConflicts(i) = %nan;
        end
    end


---> scf();
---> plot(bins, meanConflicts, '-o');
---> xtitle("Nombre moyen de conflits selon les heures de sommeil", "Heures de sommeil", "Conflits");
---> xgrid();
```
![Conflits selon heures de sommeil](/Image/ex7.png)
