# Service-airtel-money
#Enregistrement du client
print("entrez votre nom")
print("entrez votre mot de passe")
# Fonction pour vérifier l'identité de l'utilisateur
def taper_le_code():
    nom = input("Entrez votre nom d'utilisateur: ")
    if nom in utilisateurs:
        mot_de_passe = input("Entrez votre mot de passe: ")
        if utilisateurs[nom]['mot_de_passe'] == mot_de_passe:
            return nom
        else:
            print("Mot de passe incorrect.")
            return None
    else:
        print("Nom d'utilisateur non trouvé.")
        return None

# Fonction pour afficher le solde
def afficher_solde(nom):
    print(f"Votre solde Airtel Money est: {utilisateurs[nom]['solde']}")

# Fonction pour effectuer un dépôt
def depot(nom):
    montant = float(input("Entrez le montant à déposer: "))
    if montant > 0:
        utilisateurs[nom]['solde'] += montant
        print(f"Dépot réussi! Votre nouveau solde est: {utilisateurs[nom]['solde']}")
    else:
        print("Le montant doit être positif.")

# Fonction pour effectuer un retrait
def retrait(nom):
    montant = float(input("Entrez le montant à retirer: "))
    if montant > 0:
        if utilisateurs[nom]['solde'] >= montant:
            utilisateurs[nom]['solde'] -= montant
            print(f"Retrait réussi! Votre nouveau solde est: {utilisateurs[nom]['solde']}")
        else:
            print("Solde insuffisant pour ce retrait.")
    else:
        print("Le montant doit être positif.")

# Fonction principale pour interagir avec l'utilisateur
def main():
    print("Bienvenue dans le système Airtel Money.")
    
    nom = taper_le_code 
    if not nom:
        return
    
    while True:
        print("\nQue voulez-vous faire ?")
        print("1. Voir le solde")
        print("2. Effectuer un dépôt")
        print("3. Effectuer un retrait")
        print("4. Quitter")
        
        choix = input("Entrez votre choix: ")
        
        if choix == '1':
            afficher_solde(nom)
        elif choix == '2':
            depot(nom)
        elif choix == '3':
            retrait(nom)
        elif choix == '4':
            print("Merci d'avoir utilisé notre service.")
            break
        else:
            print("Choix invalide. Veuillez réessayer.")

# Exécution du programme
if __name__ == "__main__":
    main()
