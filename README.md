# Aide-Mémoire PowerShell : Connexion à un Serveur Local

## 1. Vérification de la Connectivité Réseau

### Vérifier l'adresse IP de l'ordinateur
```powershell
Get-NetIPAddress
```

### Tester la connexion avec le serveur
```powershell
Test-Connection -ComputerName "NomDuServeur" -Count 4
```

### Afficher la configuration réseau
```powershell
ipconfig /all
```

## 2. Connexion à un Serveur Local via PowerShell

### Vérifier si le serveur est joignable
```powershell
Test-NetConnection -ComputerName "NomDuServeur" -Port 3389
```

### Se connecter à une session PowerShell distante
```powershell
Enter-PSSession -ComputerName "NomDuServeur" -Credential (Get-Credential)
```

### Exécuter une commande sur un serveur distant
```powershell
Invoke-Command -ComputerName "NomDuServeur" -ScriptBlock { Get-Service }
```

## 3. Accéder aux Partages Réseau

### Lister les partages réseau d'un serveur
```powershell
Get-SmbShare -CimSession "NomDuServeur"
```

### Mapper un lecteur réseau
```powershell
New-PSDrive -Name Z -PSProvider FileSystem -Root "\\NomDuServeur\Partage" -Persist
```

## 4. Gestion des Utilisateurs et Groupes

### Lister les utilisateurs du serveur
```powershell
Get-LocalUser
```

### Ajouter un utilisateur à un groupe spécifique
```powershell
Add-LocalGroupMember -Group "Administrateurs" -Member "NomUtilisateur"
```

## 5. Dépannage de la Connexion

### Vérifier les ports ouverts
```powershell
Get-NetTCPConnection | Where-Object { $_.State -eq "Listen" }
```

### Vérifier les règles du pare-feu
```powershell
Get-NetFirewallRule | Where-Object { $_.Enabled -eq $true }
```

### Redémarrer le service de gestion à distance
```powershell
Restart-Service WinRM
```

---

Cet aide-mémoire couvre les commandes essentielles pour se connecter à un serveur local à partir d'un ordinateur du réseau. Bonne pratique !

