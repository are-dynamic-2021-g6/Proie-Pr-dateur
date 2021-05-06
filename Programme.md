# Modèles
    from matplotlib import pyplot as plt
    # x : Proies
    # y : Prédateurs
    a = 1               # Taux de reproduction proies
    b = 0.1             # Taux de mortalité proies dû aux prédateurs
    c = 0.1             # Taux de reproduction prédateurs
    d = 1               # Taux de mortalité prédateurs naturel

## Modèle 1: Prédation naturelle

    def courbeee(x, y, a, b, c, d, t):
        """ """
        lt = [0]
        lx = [x]
        ly = [y]
        for i in range(t*10000):
            dxdt = x*(a-b*y)*0.0001 # le pas de la derivée
            dydt = y*(c*x-d)*0.0001
            x = x + x*dxdt
            y = y + y*dydt
            lt.append(i*0.0001)
            lx.append(x)
            ly.append(y)
        plt.plot(lt, lx, label = "Proies")
        plt.plot(lt, ly, label = "Prédateurs")
        plt.xlabel("Temps en ? ")
        plt.ylabel("Nbr d'animaux")
        plt.title("Modèle de Lotka-Volterra : Nombre de Proie / Prédateur en fonction du temps")
        plt.legend()
        plt.show()
    
    def courbe_mix(x, y, a, b, c, d, t):
        """ """
        lx = [x]
        ly = [y]
        for i in range(t*10000):
            dxdt = x*(a-b*y)*0.0001 # le pas de la derivée
            dydt = y*(c*x-d)*0.0001
            x = x + x*dxdt
            y = y + y*dydt
            lx.append(x)
            ly.append(y)
        plt.plot(lx, ly, label = "Prédateurs en fonction des Proies")
        plt.xlabel("Nbr de proies")
        plt.ylabel("Nbr de prédateurs")
        plt.title("Modèle de Lotka-Volterra : Nombre de Proie en fonction du nombre de Prédateur")
        plt.legend()
        plt.show()

## Modèle 2: Prédation avec modification de paramètres dans la boucle

    def courbeee2(x, y, a, b, c, d, t):
        """ """
        lt = [0]
        lx = [x]
        ly = [y]
        boool = True
        for i in range(t*10000):
            if 2*x < y and boool:
                c = c/2
                b = 2*b
                boool = False
            elif 2*x > y and not(boool):
                c = c*2
                b = b/2
                boool = True
            dxdt = x*(a-b*y)*0.0001 # le pas de la derivée
            dydt = y*(c*x-d)*0.0001
            x = x + x*dxdt
            y = y + y*dydt
            lt.append(i*0.0001)
            lx.append(x)
            ly.append(y)
        plt.plot(lt, lx, label = "Proies")
        plt.plot(lt, ly, label = "Prédateurs")
        plt.xlabel("Temps en ? ")
        plt.ylabel("Nbr d'animaux")
        plt.title("Modèle de Lotka-Volterra : Nombre de Proie / Prédateur en fonction du temps (Avec changement des paramètres en fonction du ratio)")
        plt.legend()
        plt.show()
    
    def courbe_mix2(x, y, a, b, c, d, t):
        """ Quand le nombre de prédateurs monte au dessus de 2 fois le nombre de proies
        le taux de reproduction des prédateurs est divisé par deux, car manque de proies
        le taux de mortalité des proies diminue car il passe en mode survie """
        lx = [x]
        ly = [y]
        boool = True
        for i in range(t*10000):
            if 2*x < y and boool:
                c = c/2
                b = 2*b
                boool = False
            elif 2*x > y and not(boool):
                c = c*2
                b = b/2
                boool = True
            dxdt = x*(a-b*y)*0.0001 # le pas de la derivée
            dydt = y*(c*x-d)*0.0001
            x = x + x*dxdt
            y = y + y*dydt
            lx.append(x)
            ly.append(y)
        plt.plot(lx, ly, label = "Prédateurs en fonction des Proies")
        plt.xlabel("Nbr de proies")
        plt.ylabel("Nbr de prédateurs")
        plt.title("Modèle de Lotka-Volterra : Nombre de Proie en fonction du nombre de Prédateur (Avec changement des paramètres en fonction du ratio)")
        plt.legend()
        plt.show()
    
## Modèle 3: Prédation avec chasse extérieure

    def courbeee3(x, y, a, b, c, d, e, f, t):
        """ """
        lt = [0]
        lx = [x]
        ly = [y]
        for i in range(t*10000):
            dxdt = x*(a-e-b*y)*0.0001 # le pas de la derivée
            dydt = y*(c*x-d-f)*0.0001
            x = x + x*dxdt
            y = y + y*dydt
            lt.append(i*0.0001)
            lx.append(x)
            ly.append(y)
        plt.plot(lt, lx, label = "Proies")
        plt.plot(lt, ly, label = "Prédateurs")
        plt.xlabel("Temps en ? ")
        plt.ylabel("Nbr d'animaux")
        plt.title("Modèle de Lotka-Volterra : Nombre de Proie / Prédateur en fonction du temps (Avec mort par chasse / pêche)")
        plt.legend()
        plt.show()
    
    def courbe_mix3(x, y, a, b, c, d, e, f, t):
        """ e et f des facteurs liées à la chasse """
        lx = [x]
        ly = [y]
        for i in range(t*10000):
            dxdt = x*(a-e-b*y)*0.0001 # le pas de la derivée
            dydt = y*(c*x-d-f)*0.0001
            x = x + x*dxdt
            y = y + y*dydt
            lx.append(x)
            ly.append(y)
        plt.plot(lx, ly, label = "Prédateurs en fonction des Proies")
        plt.xlabel("Nbr de proies")
        plt.ylabel("Nbr de prédateurs")
        plt.title("Modèle de Lotka-Volterra : Nombre de Proie en fonction du nombre de Prédateur (Avec mort par chasse / pêche)")
        plt.legend()
        plt.show()
    
## Modèle 4: Prédation avec cannibalisme (manque de proies)

    def courbeee4(x, y, a, b, c, d, k, t):
        """ Cannibalisme chez les prédateurs si pas assez de proies """
        lt = [0]
        lx = [x]
        ly = [y]
        boool = True
        for i in range(t*10000):
             if x < y and boool:
                 d = d + k
                 boool = False
             elif x > y and not(boool):
                 d = d - k
                 boool = True
             dxdt = x*(a-b*y)*0.0001 # le pas de la derivée
             dydt = y*(c*x-d)*0.0001
             x = x + x*dxdt
             y = y + y*dydt
             lt.append(i*0.0001)
             lx.append(x)
             ly.append(y)
        plt.plot(lt, lx, label = "Proies")
        plt.plot(lt, ly, label = "Prédateurs")
        plt.xlabel("Temps en ? ")
        plt.ylabel("Nbr d'animaux")
        plt.title("Modèle de Lotka-Volterra : Nombre de Proie / Prédateur en fonction du temps (Avec cannibalisme au dessous d'un certain ratio)")
        plt.legend()
        plt.show()
    
    def courbe_mix4(x, y, a, b, c, d, k, t):
        """ """
        lx = [x]
        ly = [y]
        boool = True
        for i in range(t*10000):
            if x < y and boool:
                 d = d + k
                 boool = False
            elif x > y and not(boool):
                 d = d - k 
                 boool = True
            dxdt = x*(a-b*y)*0.0001 # le pas de la derivée
            dydt = y*(c*x-d)*0.0001
            x = x + x*dxdt
            y = y + y*dydt
            lx.append(x)
            ly.append(y)
        plt.plot(lx, ly, label = "Prédateurs en fonction des Proies")
        plt.xlabel("Nbr de proies")
        plt.ylabel("Nbr de prédateurs")
        plt.title("Modèle de Lotka-Volterra : Nombre de Proie en fonction du nombre de Prédateur (Avec cannibalisme au dessous d'un certain ratio)")
        plt.legend()
        plt.show()
