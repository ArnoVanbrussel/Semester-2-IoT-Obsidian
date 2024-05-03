# Creating an OU ABCD in domain [HQ.company.com](http://HQ.company.com)

1. Open Active Directory Users and Computers.
2. Rechts klik op domain ([HQ.company.com](http://HQ.company.com))
3. New → Organizational unit![[Pasted image 20240428112242.png]]
4. vul de naam in en klik op “OK”

# Maak een share \\win00-ms\abcd_homedirs voor de homedirectories van de ABCD gebruikers

1. ga naar Server Manager
2. klik op All Servers
3. rechtsklik op MS Server → Computer Management![[Pasted image 20240428112550.png]]
4. computer management → System Tools → Shared Folders → Shares
5. rechtklik in de witte ruimte → New → Share
6. Next → Folder Path = C:\abcd_homedirs → next → yes
7. next → customize permissions → everyone → Full Control![[Pasted image 20240428112632.png]]
8. Security → Adavanced → Disabel Inheritance → convert inherited → ok
9. Edit → remove everyone exept admin → add Authenticated Users → ok![[Pasted image 20240428112645.png]]
10. Finish
11. Users & Computers -> dubbelklik user -> profile -> Connect -> O: -> \\win00-ms\cde_homedirs\%username%
# Creating an Extra UPN

An extra UPN (User Principal Name) can be created in **Active Directory Domains and Trusts**. Follow these steps:

1. Open **Active Directory Domains and Trusts**.
2. Right-click “Active Directory Domains and Trust” select **Properties**.
3. Go to the **UPN Suffixes** tab.
4. Click **Add**.
5. Enter the new UPN suffix, for example `@mybusiness.com`.
6. Click **OK**.
7. Click **OK** to save the domain properties.

# Aanmaken Gebruikers

1. Open Active Directory Users and Computers.
2. ga naar de OU waar je de gebruikers wilt aanmaken
3. rechts klik in witte ruimte → New → User
4. Vul gegvens in en zet de logon name op het juiste → next![[Pasted image 20240428112724.png]]
5. Vul het wachtwoord in zet de settings juist → finish

# GPO Om documenten te redirecten

1. Ga naar Server Manager → Tools → Group Policy Management
2. Rechts klik op Group Policy → new
3. Geef het een naam
4. Rechts klik op de gpo en klik edit
5. "User Configuration" → "Policies" → "Windows Settings" → "Folder Redirection”
6. "Documents" en selecteer "Properties" -> "Target" selecteer je "Basic - Redirect everyone's folder to the same location”![[Pasted image 20240428112738.png]]
7. rechts klik op ou waar je het wilt toevegen → link an existing GPO → kies hem → OK
8. gpupdate /force

# GPO voor drive letters

1. Ga naar Server Manager → Tools → Group Policy Management
2. Rechts klik op Group Policy → new
3. Geef het een naam
4. Rechts klik op de gpo en klik edit
5. "User Configuration" → "Preferences" → "Windows Settings" → rechts klik "Drive Maps". → new
6. Action: "Create". → Location \\win00-ms\abcd-public → Reconnect: "Enable”
7. Label as: Laat dit leeg of voer een label in als je de schijfnaam wilt wijzigen.
8. Location: Voer het pad in naar de gedeelde map "abc_public", bijvoorbeeld "\server\abc_public".![[Pasted image 20240428112752.png]]
9. tab common -> Selecteer "Run in logged-on user's security context".
10. Klik op "OK" om de instellingen op te slaan.
11. rechts klik op ou waar je het wilt toevegen → link an existing GPO → kies hem → OK
12. gpupdate /force

# GPO iedereen voor Edge met homepage [www.mct.be](http://www.mct.be/)
1. Ga naar Server Manager → Tools → Group Policy Management
2. Rechts klik op Group Policy → new
3. Geef het een naam
4. Rechts klik op de gpo en klik edit
5. User Configuration" > "Policies" > "Administrative Templates" > "Microsoft Edge"
6. "Startup, home pages, and search pages" → Configure the home page URL
7. rechts klik op ou waar je het wilt toevegen → link an existing GPO → kies hem → OK
8. gpupdate /force

# maak een GPO voor alle engineers zodat ze hun schermachtergrond niet kunnen wijzigen

1. Ga naar Server Manager → Tools → Group Policy Management
2. Rechts klik op Group Policy → new
3. Geef het een naam
4. Rechts klik op de gpo en klik edit
5. "User Configuration" > "Policies" > "Administrative Templates" > "Control Panel" >
6. "Personalization". → "Prevent changing desktop background"

# installeer PuTTY via GPO voor alle medewerkers van Engineering

1. Zorg dat je een Share hebt waar de nodige gebruikers (Engineers) permissions voor hebben
2. Download een .msi installer voor de gewenste software (PuTTY)
3. Plaats de installer in de share
4. Ga naar Server Manager → Tools → Group Policy Management
5. Rechts klik op de OU waar je de Group Policy wil aanmaken (OU Engineering)
6. “Create New Group Policy And Link It Here”
7. Rechts klik te GPO en selecteer edit
8. "Computer Configuration" > "Policies" > "Software Settings" > "Software Installation”
9. Klik met de rechtermuisknop op "Software Installation" en selecteer "New" > "Package".
	- Blader naar de netwerkshare waar je de PuTTY MSI hebt geplaatst en selecteer deze

# maak een zwervend gebruikersprofiel aan dat opgeslagen wordt op een share

1. Ga naar Computer management van de Server waarop je de share plaatst (bv DC2)
2. Maak een share met permissies voor Authenticated Users en Administrators
3. Ga naar Server Manager → Tools → Users and Computers
4. Dubbelklik de user voor wie je een zwervend profiel wil aanmaken
5. Ga naar het tabblad ‘Profile’
6. Vul in het vakje ‘User Profile’ het pad naar de share in
	- bv.: \\win00-dc2\profiles$\%username%

# Installeer een HP netwerkprinter op een server

([https://newhelptech.wordpress.com/2017/07/20/step-by-step-how-to-install-configure-printer-pool-in-windows-server-2016/](https://newhelptech.wordpress.com/2017/07/20/step-by-step-how-to-install-configure-printer-pool-in-windows-server-2016/))

1. Server manager → Add Roles & Features → klik 3 keer “Next”
2. “Select Server Roles” interface: klik “Print and Document Services” → Next
3. “Select Features” interface → Next
4. “Print and Document Services” interface → Next
5. “Select Role Services” interface: “Print Server” checkbox moet aangevinkt zijn → next
6. Install → (wacht) → close
7. Server Manager → Tools → Print Management
8. expand Print Servers → expand Server of choice (DC2) → Add Printer
9. Add a TCP/IP or Web Services Printer by IP address or hostname → Next
10. Type of Device = TCP/IP Device; Host name or IP address: printer_ip (172.23.82.3)
11. Turn “auto detect the printer driver to use checkbox” OFF → Next
12. Device Type: Generic Network Card → Next
13. Printer Driver interface: Install a new driver → Next
14. Printer Installation Interface: Manufacturer = HP; Printer = select correct printer
15. Printer Name and Sharing Settings: Change name → Next
16. Accept of change default printer name and share name → Install → Finish
17. Print Management → Rechts klikken op de aangemaakte printer → Enable Branch Office Direct Printing
18. Print Management → Rechts klikken op de aangemaakte printer → Properties
    1. Sharing tab → List in the directory AAN → OK
19. Print Management → Rechts klikken op “Ports” → Add Port → Standard TCP/IP Port → New Port
20. Wizard → Next → ‘Add Port’ interface:
    1. ‘Printer Name or IP Address’: second printer ip (172.23.80.3) → Next
21. ‘Additional Port Information Required’ → Next → Finish → Close
22. Print Management → Rechts op printer → Properties → Ports tab → Enable printer pooling → Select port with ip of second printer as ip (172.23.80.3) → Apply → OK
23. Print Management → Rechts op printer → Properties → Advanced → Selecteer de beschikbare tijd
24. Voor nacht printer pool → nieuwe pool aanmaken met zelfde printers → andere tijd instellen