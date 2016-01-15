---
description: na
keywords: na
title: Helping Users to Protect Files by Using Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
---
# Waardoor gebruikers kunnen bestanden beveiligen met Azure Rights Management
Nadat u hebt geïmplementeerd en Azure Rights Management (Azure RMS) geconfigureerd voor uw organisatie, bieden u help en richtlijnen voor gebruikers, beheerders en uw helpdesk:

-   **Eindgebruikers informatie:**

    Laten weten wanneer en hoe documenten en e-mailberichten met vertrouwelijke informatie te beschermen. Indien mogelijk, bevatten deze informatie voor hun bestaande processen zodat ze de aanvullende stappen om een proces al bekend in plaats van introductie van volledig nieuwe processen kunnen opnemen. Zorg dat wilt laten weten voordelen (en de risico's) die specifiek zijn voor uw bedrijf, evenals bieden aanwijzingen voor het wanneer ze bestanden en e-mailberichten moeten beschermen. Als u hebt geconfigureerd [aangepaste sjablonen](http://technet.microsoft.com/library/dn642472.aspx), instructies over waarvoor een selecteren als de sjabloonnaam en beschrijving is niet voldoende ervoor kiezen de juiste is.

    > [!TIP]
    > Voorbeeld van de video's voor eindgebruikers:
    > 
    > -   [Azure RMS gebruikerservaring](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-user-experience)
    > -   [Azure RMS Document bijhouden en intrekken](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Beheerdersgegevens:**

    Beveiliging van gegevens, toepassen sommige toepassingen automatisch via beleid en de instellingen die beheerders configureren. Mogelijk moet u voor deze toepassingen met instructies voor het andere beheerders die deze toepassingen en services beheren. Zie voor meer informatie [Hoe toepassingen ondersteunen Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md) en [Toepassingen voor Azure Rights Management configureren](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

-   **Help helpdesk-informatie:**

    Een van de meest nuttige hulpprogramma's voor de helpdesk is de [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437).   Help helpdesk operators kunnen worden uitgevoerd met de optie Azure RMS-beheerder en ze kunnen gebruikers uit te voeren met de optie Azure RMS gebruiker vragen. Dit hulpprogramma kan niet alleen problemen achterhalen, maar ook het oplossen van problemen dat wordt gevonden en als nog niet is opgelost, record tracering aanmeldt.

    Als er legitieme aanvragen volledige rechten toegang hebben tot beveiligde documenten, bijvoorbeeld een aanvraag door de juridische afdeling of een manager nadat een werknemer heeft de organisatie verlaten Zorg ervoor dat de helpdesk processen voor het aanvragen van dit met behulp van de Azure RMS heeft [supergebruiker functie](https://technet.microsoft.com/en-us/library/mt147272.aspx).

    Bovendien volgen hieronder enkele van de typische problemen die gebruikers kunnen rapporteren:

    -   **Meld u aan help:**

        Gebruikers kunnen worden gevraagd om referenties wanneer Azure RMS moet een gebruiker te verifiëren en referenties in de cache kan niet worden gebruikt. Dit is van de gebruiker werk of opleiding account en wachtwoord dat is gekoppeld aan uw Office 365-tenant of Azure Active Directory-tenant. Deze worden niet een Microsoft-account (voorheen Microsoft Live-ID) of hun persoonlijke e-mailaccount, omdat deze momenteel niet worden ondersteund door Azure RMS. Gebruikers en uw helpdesk voor instructies over welke account moet worden gebruikt wanneer gebruikers wordt gevraagd om referenties als ze deze toepassingen met Azure RMS geven.

    -   **Problemen met het beschermen van of verbruikt inhoud:**

        Zorg ervoor dat gebruikers beschikken over de juiste instructies voor de toepassingen die ze gebruiken en toepassingen en apparaten die worden ondersteund door Azure RMS gebruikt. Zie voor meer informatie over ondersteunde toepassingen en apparaten [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

        Als gebruikers een fout opgetreden bij het beschermen of gebruik van inhoud, vragen om uit te voeren de [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) als een gebruiker Azure RMS.

        Als gebruikers melden dat ze beveiligde inhoud kunnen openen, maar niet de rechten die zij nodig hebben, vragen om uit te voeren de [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) als een gebruiker Azure RMS en downloaden en de sjablonen. Hierdoor kunt u vaststellen dat ze hebt gedownload de sjablonen en wat de sjablonen rechten geven. Het probleem mogelijk dat de gebruiker is niet in de juiste groep die voor de sjabloon geconfigureerd of dat de sjabloon opnieuw configureren voor de gebruiker moet zijn.

Gebruik de volgende secties voor toepassingsspecifieke informatie om te helpen beveiligen van gevoelige documenten en e-mailberichten voor gebruikers.

## Met behulp van de beveiliging van gegevens met de delen Rights Management-toepassing
De RMS (Rights Management) voor het delen van toepassing is vereist voor de gebruikers te beschermen en beveiligde inhoud gebruiken als ze Office 2010 gebruikt, maar ook aanbevolen voor alle computers en mobiele apparaten die ondersteuning van Azure RMS.

Naast het gemakkelijker voor gebruikers te beschermen belangrijke documenten, de RMS sharing toepassing kiest, kunnen gebruikers de documenten die deze beveiligd traceren en indien nodig, toegang tot deze intrekken.

Zie voor instructies voor deze toepassing voor Windows-computers de [delen toepassing Rights Management-handleiding](http://technet.microsoft.com/library/dn339006.aspx).

Voor mobiele apparaten, raadpleegt u de [Veelgestelde vragen over Microsoft Rights Management delen van de toepassing voor mobiele Platforms](http://technet.microsoft.com/dn451248).

> [!TIP]
> Voor een op hoog niveau voorbeeldscenario met schermafdrukken, raadpleegt u de [Bijlagen delen gebruikers veilig met mobiele gebruikers](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Example_SharingApp) sectie de [Wat is Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) onderwerp.

## Met behulp van de beveiliging van gegevens met Office 365, Office 2016 of Office 2013
Als u van Azure RMS gebruikmaakt en de Rights Management delen van de toepassing niet is geïnstalleerd, niet zichtbaar voor gebruikers de **beveiligd delen** knop in het lint of **beveiligen** uit bestand Explorer die is het gemakkelijk om ze om bestanden te beschermen. Voor deze gebruikers, moeten deze lijkt op deze instructies volgen.

> [!TIP]
> Als u zelfstudies toepassingsspecifieke help en instructies voor het gebruik van de beveiliging van gegevens voor deze toepassingen, zoekt u **IRM** en de naam van een toepassing en de versie.

#### Een document in Word 2013 beveiligen

1.  Maak een nieuw document in Microsoft Word.

2.  Uit de **bestand** menu, klikt u op **Info**, klikt u op **Document beveiligen**, klikt u op **Beperk toegang**, en kies vervolgens een sjabloon voor snel de juiste gebruiksrechten toepassen of selecteer **Beperk toegang** en de gebruiksrechten zelf selecteren.

    > [!NOTE]
    > Als dit de eerste keer dat u Rights Management hebt gebruikt, neemt u contact met de [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] service en wordt gevraagd om referenties voor de Office IRM-client configureren.

3.  Sla het document.

Als u anderen het document openen, worden ze eerst geverifieerd. Als ze zijn niet gemachtigd om het document te openen, wordt het document niet openen. Als ze gemachtigd zijn om het document te openen, wordt de geopend met beperkt gebruiksrechten die zijn opgegeven voor die gebruiker. Bijvoorbeeld kunnen een gebruik van alleen-lezen niet de gebruiker om te bewerken of het document opslaat, zelfs als het eerst is gekopieerd naar een andere locatie. De gebruiksrechten worden weergegeven aan de bovenkant van het document met behulp van een banner beperking. Het logo van de machtigingen die worden toegepast op het document kan weergeven of het mogelijk een koppeling om deze weer te geven.

#### Een e-mailbericht met Outlook 2013 en Exchange Online beveiligen

1.  In Outlook, maken een nieuw e-mailbericht naar een geadresseerde binnen uw organisatie verholpen.

2.  Uit de **opties** en klik op **toestemming**, en selecteer vervolgens een optie. Bijvoorbeeld: **Niet doorsturen**, **&lt; bedrijfsnaam &gt; - vertrouwelijke** of **&lt; bedrijfsnaam &gt; - vertrouwelijk alleen in de weergave**.

3.  Het bericht verzenden.

Op dezelfde manier als het weergeven van een beveiligd document zijn wanneer de geadresseerden het e-mailbericht ontvangen ze eerst geverifieerd. Als ze gemachtigd zijn om te zien van het e-mailbericht, wordt de geopend met beperkt gebruiksrechten die zijn opgegeven voor die gebruiker. Als u hebt geselecteerd bijvoorbeeld **niet doorsturen**, de knop volgende op het lint is niet beschikbaar.

#### Een e-mailbericht met behulp van de Outlook Web-App beveiligen

1.  In de Outlook Web-App maken een nieuw e-mailbericht naar een geadresseerde binnen uw organisatie verholpen.

2.  Klik op  **...**,  klikt u op **machtiging**, en selecteer vervolgens een optie. Bijvoorbeeld: **Niet doorsturen**, **allen niet beantwoorden**, **&lt; bedrijfsnaam &gt; - vertrouwelijke** of **&lt; bedrijfsnaam &gt; - vertrouwelijk alleen in de weergave**.

3.  Het bericht verzenden.

Op dezelfde manier als het weergeven van een beveiligd document zijn wanneer de geadresseerden het e-mailbericht ontvangen ze eerst geverifieerd. Als ze gemachtigd zijn om te zien van het e-mailbericht, wordt de geopend met beperkt gebruiksrechten die zijn opgegeven voor die gebruiker. Als u hebt geselecteerd bijvoorbeeld **doen niet allen beantwoorden**, de **Allen beantwoorden** optie in het berichtvenster is niet beschikbaar.

## Zie ook
[Met behulp van Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

