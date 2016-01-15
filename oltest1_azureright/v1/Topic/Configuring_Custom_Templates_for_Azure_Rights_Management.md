---
description: na
keywords: na
title: Configuring Custom Templates for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c
---
# Aangepaste sjablonen configureren voor Azure Rights Management
Nadat u Azure Rights Management (Azure RMS) hebt geactiveerd, zich kunnen gebruikers automatisch aan twee standaardsjablonen waarmee u eenvoudig kunnen beleid toepassen om gevoelige bestanden met toegang tot gemachtigde gebruikers in uw organisatie beperkte te gebruiken. Deze twee sjablonen hebben de volgende rechten beleidsbeperkingen:

-   Alleen-lezen voor de beveiligde inhoud weergeven

    -   Weergavenaam: **&lt; organisatienaam &gt; - alleen vertrouwelijke weergeven**

    -   Specifieke machtiging: Inhoud weergeven

-   Lezen of wijzigen van machtigingen voor de beveiligde inhoud

    -   Weergavenaam: **&lt; organisatienaam &gt; - vertrouwelijke**

    -   Specifieke machtigingen: Inhoud weergeven, opslaan, bewerken, inhoud, toegewezen rechten weergeven, toestaan macro's, doorsturen, beantwoorden, Allen beantwoorden

Bovendien de [RMS sharing toepassing](http://technet.microsoft.com/library/dn339006.aspx) kiest, kunnen gebruikers hun eigen reeks machtigingen definiëren. En voor de Outlook-client en de Outlook Web Access, kunnen gebruikers selecteren de **niet doorsturen** optie voor e-mailberichten.

In veel organisaties wordt de standaardsjablonen mogelijk voldoende. Maar als u wilt uw eigen aangepaste rechten om beleidssjablonen te maken, kunt u dit doen. Mogelijke oorzaken voor het maken van een aangepaste sjabloon zijn de volgende:

-   Wilt u een sjabloon rechten voor een subset van gebruikers in de organisatie in plaats van alle gebruikers.

-   U wilt dat alleen een subset van gebruikers kunnen zien en selecteer een sjabloon (afdelingen sjabloon) van toepassingen in plaats van alle gebruikers in de organisatie zien en de sjabloon kunt selecteren.

-   U wilt definiëren van een aangepaste geschikt voor een sjabloon, zoals weergeven en bewerken, maar niet kopiëren en afdrukken.

-   Wilt u aanvullende opties configureren in een sjabloon met een verloopdatum en of de inhoud die toegankelijk zijn zonder een internetverbinding nodig.

Voor gebruikers kunnen een aangepaste sjabloon met instellingen zoals deze te selecteren, moet u eerst een aangepaste sjabloon maken, configureren en vervolgens te publiceren.

Gebruik de volgende secties om te configureren en gebruiken van aangepaste sjablonen:

-   [Het maken, configureren en publiceren van een aangepaste sjabloon](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToConfigureCustomTemplates)

-   [Het kopiëren van een sjabloon](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates)

-   [Het verwijderen van sjablonen (archief)](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToArchiveTemplates)

-   [Vernieuwen van sjablonen voor gebruikers](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates)

-   [Windows PowerShell-verwijzing](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_PowerShellTemplates)

## <a name="BKMK_HowToConfigureCustomTemplates"></a>Het maken, configureren en publiceren van een aangepaste sjabloon
U maakt en beheren van aangepaste sjablonen in de Azure-beheerportal. U kunt dit doen rechtstreeks vanuit de Azure-beheerportal of meld u aan bij het Office 365-beheercentrum en kies de **Geavanceerde functies** voor Rights Management, dat vervolgens opent wordt u omgeleid naar de Azure-beheerportal.

De volgende procedures gebruiken om te maken, configureren en publiceren van aangepaste sjablonen voor Rights Management.

#### Een aangepaste sjabloon maken

1.  Afhankelijk van of u zich aanmeldt bij het Office 365-beheercentrum of het Azure-Portal, voert u een van de volgende:

    -   Uit de [Office 365-beheercentrum](https://portal.office.com/):

        1.  Klik in het linkerdeelvenster op **service-instellingen**.

        2.  Uit de **service-instellingen** pagina, klikt u op **rights management**.

        3.  In de **beschermen van uw gegevens** sectie, klikt u op **beheren**.

        4.  In de **rights management** sectie, klikt u op **Geavanceerde functies**.

            > [!NOTE]
            > Als u Rights Management nog niet hebt geactiveerd, klikt u eerst **activeren** en de actie te bevestigen. Zie voor meer informatie [Azure Rights Management activeren](../Topic/Activating_Azure_Rights_Management.md).
            > 
            > Als u nog niet hebt geklikt **Geavanceerde functies** nadat Rights Management is geactiveerd, voert u de activeringsinstructies op uw instructies voor het ophalen van een gratis Azure-abonnement die vereist zijn voor toegang tot het Azure-Portal.

            Te klikken op **Geavanceerde functies** wordt geladen het Azure-portal waar u kunt beheren **RIGHTS MANAGEMENT** voor uw organisatie Azure Active Directory.

    -   Uit de [Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=275081):

        1.  Klik in het linkerdeelvenster op **ACTIVE DIRECTORY**.

        2.  Uit de **active directory** pagina, klikt u op **RIGHTS MANAGEMENT**.

        3.  Selecteer de map voor het beheren van voor Rights Management.

        4.  Als u Rights Management nog niet hebt geactiveerd, klikt u op **activeren** en de actie te bevestigen.

            > [!NOTE]
            > Zie voor meer informatie [Azure Rights Management activeren](../Topic/Activating_Azure_Rights_Management.md).

2.  Maak een nieuwe sjabloon:

    -   In de Azure-portal van de **aan de slag met Rights Management** snel startpagina, klikt u op **maken van een nieuwe rechtenbeleidssjabloon**.

        Als u deze pagina niet direct ziet nadat u de instructies voor Office 365, gebruikt u de navigatie-instructies hierboven voor de Azure-portal.

3.  Op de **toevoegen van een nieuwe rechtenbeleidssjabloon** pagina, kiest u een taal waarin u de sjabloonnaam en beschrijving die gebruikers zien wordt typen (u kunt meer talen later toevoegen). Vervolgens typt u een unieke naam en beschrijving in en klik op de knop Voltooien.

Uit de **aan de slag met Rights Management** snel startpagina, klik op nu **beheren van uw rechtenbeleidssjablonen**. Ziet u de nieuwe sjabloon toegevoegd aan de lijst met sjablonen, met de status van **gearchiveerde**. In deze fase de sjabloon is gemaakt, maar niet is geconfigureerd, is niet zichtbaar voor gebruikers.

#### Om te configureren en publiceren van een aangepaste sjabloon

1.  Selecteer de zojuist gemaakte sjabloon van het **sjablonen** pagina in de Azure-beheerportal.

2.  Uit de **de sjabloon is toegevoegd** snel startpagina, klikt u op **aan de slag** van stap 1, **configureren rechten voor gebruikers en groepen,** klikt u vervolgens op **nu aan de slag** of **toevoegen**, en selecteer vervolgens de gebruikers en groepen die de rechten voor het gebruik van de inhoud die wordt beveiligd door de nieuwe sjabloon.

    > [!NOTE]
    > De gebruikers of groepen die u selecteert, moeten een e-mailadres hebben. Dit is bijna altijd het geval in een productieomgeving maar in een eenvoudige testomgeving, moet u mogelijk e-mailadressen toevoegen aan accounts van gebruikers of groepen.

    Beste, groepen in plaats van gebruikers, waardoor beheer van de sjablonen eenvoudiger te gebruiken. Als u Active Directory lokale hebben en naar Azure AD synchroniseert, kunt u e-mailadres groepen die beveiligingsgroepen of distributiegroepen zijn. Als u wilt rechten voor alle gebruikers in de organisatie, wordt het echter efficiënter te kopiëren een van de standaardsjablonen in plaats van meerdere groepen opgeven. Zie voor meer informatie de [Het kopiëren van een sjabloon](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates) in dit onderwerp.

    > [!TIP]
    > U kunt gebruikers van buiten uw organisatie aan de sjabloon later toevoegen met de [Windows PowerShell-module voor Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx) en het gebruik van een van de volgende methoden:
    > 
    > -   **Exporteren, bewerken en de bijgewerkte sjabloon importeren**:  Dit is de eenvoudigste methode voor externe gebruikers toevoegen aan een bestaande sjabloon met andere groepen. Gebruik de [exporteren AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) cmdlet exporteren van de sjabloon naar een. CSV-bestand dat u bewerken wilt, om toe te voegen van de externe e-mailadressen van deze gebruikers en hun rechten op de bestaande groepen en rechten. Gebruik vervolgens de [importeren AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) voor het importeren van deze wijziging van de cmdlet weer in Azure RMS.
    > -   **Een rechten definition-object gebruiken om te werken van een sjabloon**:    Geef de externe e-mailadressen en hun rechten in een rechten definition-object dat u het bijwerken van de sjabloon gebruiken. U de rechten definition-object opgeeft door de [Nieuw AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) cmdlet naar een variabele maken en geef deze variabele naar de parameter - RightsDefinition met de [Set AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) cmdlet om een bestaande sjabloon te wijzigen. Echter, als u deze gebruikers aan een bestaande sjabloon toevoegen wilt, u moet ook rechten definitie om objecten te definiëren voor de bestaande groepen in de sjablonen en niet alleen de nieuwe externe gebruikers.

3.  Klik op de knop Volgende en wijs een van de genoemde rechten voor de geselecteerde gebruikers en groepen.

    Gebruik de beschrijving van de weergegeven voor meer informatie over elke rechts (en voor aangepaste rechten). Er is ook meer gedetailleerde informatie beschikbaar in [Gebruiksrechten voor Azure Rights Management configureren](../Topic/Configuring_Usage_Rights_for_Azure_Rights_Management.md). Toepassingen die ondersteuning bieden voor RMS kunnen echter variëren hoe zij deze rechten implementeren. Raadpleeg de documentatie en voer uw eigen testen met de toepassingen die gebruikers gebruiken voor het gedrag controleren voordat u de sjabloon voor gebruikers implementeren. Zorg met deze sjabloon zichtbaar is voor alleen beheerders voor deze testen, zodat deze sjabloon voor een sjabloon afdelingen (stap 6).

4.  Als u hebt geselecteerd **aangepaste**, klikt u op de knop Volgende en selecteer vervolgens de aangepaste rechten.

    Maar u een combinatie van de afzonderlijke rechten beschikbaar in sommige toepassingen gebruiken kunt, kunnen sommige rechten afhankelijkheden op andere individuele rechten hebben. Als dit het geval is, kan de afhankelijke rechten automatisch voor u worden geselecteerd.

    > [!TIP]
    > Voeg eventueel de **kopiëren en inhoud extraheren** rechts en dit geselecteerde beheerders of personeel in andere rollen toe die verantwoordelijk is voor informatie over herstel verlenen. Dit recht kiest, kunnen ze protection indien nodig, van bestanden en e-mailberichten die worden beschermd met deze sjabloon verwijderen. Deze mogelijkheid om te verwijderen van de beveiliging op het sjabloonniveau van de biedt meer afzonderlijke dan met de functie super-gebruiker.

5.  Klik op voltooien.

6.  Als u wilt dat de sjabloon voor slechts een subset van gebruikers zichtbaar zijn wanneer ze een van sjablonen in toepassingen overzicht: Klik op **bereik** configureren dit als een afdelingen sjabloon en klik op **nu aan de slag**. Anders gaat u naar stap 9.

    Meer informatie over afdelingen sjablonen: Standaard alle gebruikers in uw Azure directory overzicht van de gepubliceerde sjablonen en ze kunnen deze selecteren in toepassingen wanneer ze wilt beveiligen van inhoud. Als u wilt dat bepaalde gebruikers slechts enkele van de gepubliceerde sjablonen, moet u het bereik van de sjablonen voor deze gebruikers. Vervolgens wordt alleen deze gebruikers zich kunnen deze sjablonen selecteren. Andere gebruikers die u opgeeft, ziet u de sjablonen en daarom kunnen niet worden geselecteerd. Deze techniek kunt ervoor kiezen de juiste sjabloon gemakkelijker voor gebruikers, vooral wanneer u sjablonen die zijn ontworpen om te worden gebruikt door de specifieke groepen of afdelingen maken. Gebruikers zien vervolgens alleen de sjablonen die zijn ontworpen voor deze.

    U hebt bijvoorbeeld een sjabloon voor de afdeling Human Resources die de machtiging alleen-lezen voor leden van de afdeling Financiën van toepassing is gemaakt. Zodat alleen leden van de afdeling Human Resources deze sjabloon toepassen kunnen bij het gebruik van de Rights Management-toepassing delen, scope de sjabloon aan de groep met e-mailbericht met de naam Personeelszaken. Vervolgens toepassen alleen leden van deze groep Zie en kan deze sjabloon.

7.  Op de **sjabloon zichtbaarheid** pagina, selecteert u de gebruikers en groepen beheerders kunnen zien en selecteer de sjabloon in de RMS-enlightened toepassingen. Als moeten voor, wordt aangeraden, groepen voor gebruik in plaats van gebruikers, en de groepen of gebruikers die u selecteert hebben een e-mailadres.

8.  Klik op de knop Volgende en beslist of moet u de compatibiliteit van toepassingen voor de sjabloon afdelingen configureren. Als u, op **TOEPASSINGSCOMPATIBILITEIT**, schakel het selectievakje in en klik op **voltooid**.

    Waarom mogelijk moet u configureren toepassingscompatibiliteit? Niet alle toepassingen kunnen afdelingen sjablonen ondersteunen. Hiervoor de toepassing moet eerst worden geverifieerd bij de RMS-service voor het downloaden van de sjablonen. Als het verificatieproces niet, standaard optreedt worden geen van de afdeling sjablonen gedownload. U kunt dit probleem negeren door te geven dat de afdelingen sjablonen te downloaden, toepassingscompatibiliteit configureren en selecteert u de **met deze sjabloon voor alle gebruikers worden weergegeven wanneer de toepassingen bieden geen ondersteuning voor gebruikers-id** selectievakje.

    Bijvoorbeeld als compatibiliteit met de afdeling sjabloon niet is geconfigureerd in ons voorbeeld Human Resources, zien alleen gebruikers in de afdeling Human Resources de afdelingen sjabloon als ze de RMS-toepassing voor delen gebruiken, maar er zijn geen gebruikers de afdelingen sjabloon zien wanneer ze met Outlook Web Access (OWA) van Exchange Server 2013 omdat Exchange OWA en Exchange ActiveSync momenteel afdelingen sjablonen ondersteunen. Als u dit standaardgedrag door toepassingscompatibiliteit configureren, Zie alleen gebruikers in de afdeling Human Resources afdelingen sjabloon als ze de RMS sharing toepassing gebruiken, maar alle gebruikers de afdelingen sjabloon zien wanneer ze Outlook Web Access (OWA) gebruiken. Als gebruikers OWA of Exchange ActiveSync van Exchange Online, de afdelingen sjablonen zichtbaar voor alle gebruikers of er zijn geen gebruikers zien de afdeling sjablonen, op basis van de sjabloonstatus (archivering of gepubliceerde) in Exchange Online.

    > [!NOTE]
    > Als u toepassingen die afdelingen sjablonen systeemeigen nog niet ondersteunen, kunt u een [aangepast RMS sjabloon downloaden script](http://go.microsoft.com/fwlink/?LinkId=524506) of andere hulpprogramma's voor deze sjablonen implementeren naar de lokale map voor de RMS-client. Deze toepassingen worden de afdelingen sjablonen vervolgens correct weergegeven voor alleen de gebruikers en groepen die u hebt geselecteerd voor de sjabloon scope:
    > 
    > -   Voor Office 2010 map voor de client is **%localappdata%\Microsoft\DRM\Templates**.
    > -   Vanaf een clientcomputer die alle sjablonen heeft gedownload, kunt u Kopieer en plak de sjabloonbestanden met andere computers.
    > 
    > Office 2016 ondersteunt afdelingen sjablonen, evenals de Office 2013 met de meest recente updates voor Office ([KB 3054853](https://support.microsoft.com/kb/3054853)).

9. Klik op **configureren** en extra talen die gebruikmaken van gebruikers, samen met de naam en beschrijving van deze sjabloon in die taal toevoegen. Als u meerdere talen gebruikers hebt, is het belangrijk toevoegen aan elke taal die ze gebruiken en geef een naam en beschrijving in die taal. Gebruikers vervolgens wordt de naam en beschrijving van de sjabloon in dezelfde taal als de client-besturingssysteem wordt uitgevoerd, waardoor dat ze begrijpen het beleid toegepast op een document of e-mailbericht. Als er geen overeenkomst met hun client-besturingssysteem wordt uitgevoerd, valt de naam en beschrijving die ze zien terug naar de taal en een beschrijving die u hebt gedefinieerd bij het maken van de sjabloon.

    Controleer of u wilt wijzigen in de volgende instellingen:

    |Instelling|Meer informatie|
    |--------------|-------------------|
    |**verlopen van inhoud**|Definieer een datum of een aantal dagen voor deze sjabloon wanneer bestanden die worden beschermd door de sjabloon mag niet worden geopend. U kunt een datum opgeven of een aantal dagen vanaf het moment dat de beveiliging wordt toegepast op het bestand.<br /><br />Als u een datum opgeeft, is het effectieve middernacht in uw huidige tijdzone.|
    |**offline toegang**|Gebruik deze instelling te voorkomen dat een beveiligingsvereisten dat u tegen de vereiste die gebruikers moeten kunnen openen bestanden beveiligde hebt wanneer ze niet over een internetverbinding nodig.<br /><br />Als u opgeven dat de inhoud niet beschikbaar zonder een internetverbinding is of die inhoud alleen beschikbaar voor een opgegeven aantal dagen is, als deze drempel is bereikt, gebruikers moeten opnieuw geverifieerde en hun toegang wordt vastgelegd. Als dit gebeurt, als hun referenties zijn niet in de cache, wordt gebruikers gevraagd zich aan te melden voordat ze het bestand kunnen openen.<br /><br />Naast de nieuwe verificatie is het beleid en het lidmaatschap van de gebruiker opnieuw wordt geëvalueerd. Dit betekent dat gebruikers verschillende toegangsresultaten voor hetzelfde bestand optreden kunnen als er wijzigingen in het beleid of groep lidmaatschap van wanneer ze het bestand het laatst is geopend.|

10. Als u er zeker van te zijn dat de sjabloon correct is geconfigureerd voor uw gebruikers, klikt u op **publiceren** de sjabloon zichtbaar voor gebruikers en klik vervolgens op **Opslaan**.

11. Klik op de knop terug in de beheerportal wilt terugkeren naar de **sjablonen** pagina waar de sjabloon nu een bijgewerkte status heeft **gepubliceerd**.

Wijzigingen aanbrengen in de sjabloon, selecteert u het en gebruik de stappen snel starten vervolgens opnieuw. Of Selecteer een van de volgende opties:

-   Meer gebruikers en groepen toevoegen en de rechten voor deze gebruikers en groepen definiëren: Klik op **rechten**, klikt u vervolgens op **toevoegen**.

-   Verwijderen van gebruikers of groepen die u eerder hebt geselecteerd: Klik op **rechten**, selecteer de gebruiker of groep in de lijst en klik vervolgens op **verwijderen**.

-   Wijzigen welke gebruikers ziet u de sjablonen om deze te selecteren van toepassingen: Klik op **bereik**, klikt u vervolgens op **toevoegen** of **verwijderen**, of **TOEPASSINGSCOMPATIBILITEIT**.

-   U de sjabloon niet meer zichtbaar voor alle gebruikers: Klik op **configureren**, klikt u op **ARCHIEF**, en klik vervolgens op **Opslaan**.

-   Andere configuratiewijzigingen aanbrengen: Klik op **configureren**, breng de gewenste wijzigingen aan en klik vervolgens op **Opslaan**.

> [!WARNING]
> Als u wijzigingen in een sjabloon die is opgeslagen aanbrengt, ziet clients u de wijzigingen aan de sjabloon pas sjablonen worden vernieuwd op hun computers. Zie voor meer informatie de [Vernieuwen van sjablonen voor gebruikers](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates) in dit onderwerp.

## <a name="BKMK_HowToCopyTemplates"></a>Het kopiëren van een sjabloon
Als u maken van een nieuwe sjabloon die vergelijkbaar instellingen van een bestaande sjabloon wilt is, selecteert u de oorspronkelijke sjabloon op de **sjablonen** pagina, klikt u op **kopie**, Geef een unieke naam en de wijzigingen die u nodig hebt.

> [!IMPORTANT]
> Wanneer u een sjabloon kopieert de **gepubliceerd** of **gearchiveerde** status wordt ook gekopieerd. Dus als u een gepubliceerde sjabloon kopieert, de onmiddellijke status wordt gepubliceerd, tenzij u deze wijzigt.

U kunt aangepaste sjablonen en de standaardsjablonen kopiëren. Kopieer aanbevolen om een van de standaardsjablonen in plaats van een nieuwe aangepaste sjabloon maken als u wilt dat de sjabloon rechten voor alle gebruikers in uw organisatie. Deze methode betekent dat u niet meer te maken of meerdere groepen op te geven van alle gebruikers te selecteren. In dit scenario echter wel moet u een nieuwe naam en beschrijving voor de gekopieerde sjabloon voor extra talen opgeven.

## <a name="BKMK_HowToArchiveTemplates"></a>Het verwijderen van sjablonen (archief)
De standaardsjablonen kunnen niet worden verwijderd, maar ze kunnen worden gearchiveerd zodat gebruikers deze niet zien.

Op dezelfde manier als u een aangepaste sjabloon hebt gepubliceerd en niet meer wilt dat gebruikers kunnen zien, kunt u de sjabloon bewerken en kiezen **ARCHIEF** en **Opslaan** van de **configureren** pagina. Of kunt u het selecteren van de **sjablonen** pagina en selecteer **ARCHIEF**.

Omdat u niet de standaardsjablonen om te archiveren deze sjablonen bewerken moet u de **ARCHIEF** optie uit de **sjablonen** pagina. U kunt de Outlook kan niet archiveren **niet doorsturen** optie.

#### Een standaardsjabloon verwijderen

-   Uit de **sjablonen** pagina, de standaardsjabloon selecteren en klik op **ARCHIEF**.

De status wordt gewijzigd van **gepubliceerd** naar **gearchiveerde**. Als u van gedachten verandert, selecteer de sjabloon en klik op **publiceren**.

## <a name="BKMK_RefreshingTemplates"></a>Vernieuwen van sjablonen voor gebruikers
Als u Azure RMS gebruikt, worden sjablonen automatisch gedownload op clientcomputers zodat gebruikers van hun toepassingen selecteren kunnen. Mogelijk moet u echter aanvullende maatregelen nemen als u wijzigingen in de sjablonen aanbrengt:

|Toepassing of service|Hoe sjablonen worden vernieuwd na wijzigingen|
|-------------------------|-------------------------------------------------|
|Exchange Online|Handmatige configuratie vereist voor het vernieuwen van sjablonen.<br /><br />Vouw in de volgende sectie voor de configuratiestappen [Alleen in Exchange Online: Het configureren van Exchange downloaden van aangepaste sjablonen gewijzigd](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_ExchangeOnlineTemplatesUpdate).|
|Office 365|Automatisch vernieuwd: Er is geen aanvullende stappen vereist.|
|Office 2016 en Office 2013<br /><br />RMS delen van de toepassing voor Windows|Automatisch vernieuwd – op basis van een schema:<br /><br />-   Deze nieuwere versies van Office: Het vernieuwen van interval is standaard 7 dagen.<br />-   Voor de RMS sharing van toepassing voor Windows: Het interval voor standaard vernieuwen is vanaf 1.0.1784.0-versie elke 1 dag. Eerdere versies hebben een standaardwaarde interval van 7 dagen vernieuwen.<br /><br />Om te vernieuwen sneller dan deze planning afdwingen uit, vouw de volgende sectie [Office 2016 Office 2013 en RMS sharing toepassing voor Windows: Hoe vernieuwd voor een gewijzigde aangepaste sjabloon](#BKMK_Office2013ForceUpdate).|
|Office 2010|Vernieuwd wanneer gebruikers zich aanmelden.<br /><br />Als u een vernieuwen, vragen of afdwingen dat gebruikers zich afmelden en weer opnieuw aangemeld. Of raadpleegt u de volgende sectie [Office 2010: Hoe vernieuwd voor een gewijzigde aangepaste sjabloon](#BKMK_Office2010ForceUpdate).|
Voor mobiele apparaten die gebruikmaken van de toepassing voor delen RMS sjablonen automatisch gedownload (en indien nodig vernieuwd) zonder aanvullende configuratie vereist.

### <a name="BKMK_ExchangeOnlineTemplatesUpdate"></a>Alleen in Exchange Online: Het configureren van Exchange downloaden van aangepaste sjablonen gewijzigd
Als u al Information Rights Management (IRM) voor Exchange Online hebt geconfigureerd, wordt niet aangepaste sjablonen downloaden voor gebruikers totdat u de volgende wijzigingen aanbrengen met behulp van Windows PowerShell Exchange Online.

> [!NOTE]
> Zie voor meer informatie over het gebruik van Windows PowerShell in Exchange Online [met behulp van PowerShell met Exchange Online](https://technet.microsoft.com/library/jj200677%28v=exchg.160%29.aspx).

Telkens wanneer die u een sjabloon wijzigt, moet u deze procedure doen.

##### Sjablonen voor Exchange Online bijwerken

1.  Met Windows PowerShell Exchange Online, verbinding maken met de service:

    1.  Geef uw Office 365-gebruikersnaam en wachtwoord:

        ```
        $Cred = Get-Credential
        ```

    2.  Verbinding maken met de Exchange Online-service door het uitvoeren van de volgende twee opdrachten:

        ```
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
        ```

        ```
        Import-PSSession $Session
        ```

2.  Gebruik de [importeren RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200724%28v=exchg.160%29.aspx) cmdlet aan uw vertrouwde publicatieserver domein (vertrouwde Uitgiftedomein) van Azure RMS opnieuw te importeren:

    ```
    Import-RMSTrustedPublishingDomain -Name "<TPD name>" -RefreshTemplates -RMSOnline
    ```
    Als de naam van de vertrouwde Uitgiftedomein is bijvoorbeeld **Online RMS - 1** (een standaard naam voor veel organisaties) invoeren: **Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates -RMSOnline**

    > [!NOTE]
    > Om te controleren of de naam van uw vertrouwde Uitgiftedomein, kunt u de [Get-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200707%28v=exchg.160%29.aspx) cmdlet.

3.  Om te bevestigen dat de sjablonen hebt geïmporteerd, wacht enkele minuten en voer de [Get-RMSTemplate](http://technet.microsoft.com/library/dd297960%28v=exchg.160%29.aspx) cmdlet en het Type ingesteld op alle. Bijvoorbeeld:

    ```
    Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
    ```
    > [!TIP]
    > Het is handig om een kopie van de uitvoer bewaren zodat u eenvoudig kopiëren kunt de sjabloonnamen of de GUID's als u een sjabloon later archiveert.

4.  Voor elke geïmporteerde sjabloon die u wilt beschikbaar in de Outlook Web-App, moet u de [Set RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) cmdlet en het Type ingesteld op gedistribueerde:

    ```
    Set-RMSTemplate -Identity "<name  or GUID of the template>" -Type Distributed
    ```
    Omdat Outlook Web Access de gebruikersinterface voor 24 uur slaat, kunnen gebruikers de nieuwe sjabloon voor tot een dag niet zien.

Als u een sjabloon archiveert bovendien (aangepaste of standaard) en gebruik van Exchange Online met Office 365 gebruikers blijven overzicht van de gearchiveerde sjablonen als ze de Outlook Web-App of mobiele apparaten die gebruikmaken van Exchange ActiveSync-Protocol.

Zodat gebruikers niet langer deze sjablonen zien, verbinding maken met de service met behulp van Windows PowerShell in Exchange Online en gebruikt u de [Set RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) cmdlet door het uitvoeren van de volgende opdracht:

```
Set-RMSTemplate -Identity "<name or GUID of the template>" -Type Archived
```

### <a name="BKMK_Office2013ForceUpdate"></a>Office 2016 Office 2013 en RMS sharing toepassing voor Windows: Hoe vernieuwd voor een gewijzigde aangepaste sjabloon
Door het bewerken van het register op de computers met Office 2016, Office 2013 of de RMS (Rights Management) voor het delen van toepassingen voor Windows, kunt u de automatische planning wijzigen zodat gewijzigde sjablonen worden vernieuwd op computers vaker dan de standaardwaarde. U kunt ook een onmiddellijke vernieuwing afdwingen door de bestaande gegevens in een registerwaarde verwijderen.

> [!WARNING]
> Als u de Register-Editor onjuist gebruikt, kunt u er problemen die mogelijk moet u het besturingssysteem opnieuw installeren. Microsoft kan niet garanderen dat u problemen die het gevolg oplossen kunt van onjuist gebruik van de Register-Editor. Gebruik de Register-Editor voor uw eigen risico.

##### De automatische schema wijzigen

1.  Gebruik de Registereditor en stel een van de volgende registerwaarden:

    -   Een updatefrequentie in dagen (minimaal 1 dag) instellen:  Maak een nieuwe registerwaarde met de naam **TemplateUpdateFrequency** en definieer een geheel getal voor de gegevensbron waarmee de frequentie in dagen eventuele wijzigingen aan een gedownloade sjabloon kan worden gedownload. Gebruik de volgende tabel om de registerpad voor het maken van deze nieuwe registerwaarde te vinden.

        |Register-pad|Type|Waarde|
        |----------------|--------|----------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequency|

    -   Een updatefrequentie in seconden (minimaal 1 seconde) instellen:  Maak een nieuwe registerwaarde met de naam **TemplateUpdateFrequencyInSeconds** en definieer een geheel getal voor de gegevensbron waarmee de frequentie in seconden voor het downloaden van eventuele wijzigingen aan een gedownloade sjabloon. Gebruik de volgende tabel om de registerpad voor het maken van deze nieuwe registerwaarde te vinden.

        |Register-pad|Type|Waarde|
        |----------------|--------|----------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequencyInSeconds|

    Zorg ervoor dat u maakt en stel een van deze registerwaarden niet beide. Als beide aanwezig zijn, **TemplateUpdateFrequency** wordt genegeerd.

2.  Als u afdwingen dat een onmiddellijke vernieuwing van de sjablonen wilt, gaat u naar de volgende procedure. Anders wordt nu opnieuw opstarten uw Office-toepassingen en exemplaren van File Explorer.

##### Voor het afdwingen van een onmiddellijk vernieuwen

1.  Met een Registereditor, verwijdert u de gegevens voor de **LastUpdatedTime** waarde. Bijvoorbeeld, de gegevens mogelijk weergegeven **2015-04-20T15:52**; 2015 verwijderen-04-20T15:52 zodat er zijn geen gegevens wordt weergegeven. Gebruik de volgende tabel om de registerpad als u wilt verwijderen van deze gegevens registerwaarden te vinden.

    |Register-pad|Type|Waarde|
    |----------------|--------|----------|
    |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\ &lt; MicrosoftRMS_FQDN &gt; \Template|REG_SZ|LastUpdatedTime|
    > [!TIP]
    > In het registerpad *&lt; MicrosoftRMS_FQDN &gt;* verwijst naar de FQDN-naam van uw Microsoft RMS-service. Als u controleren of deze waarde wilt:
    > 
    > 1.  Voer de [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) cmdlet voor Azure RMS. Als u hebt al de Windows PowerShell-module voor Azure RMS geïnstalleerd, Zie [Installatie van Windows PowerShell voor Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).
    > 2.  Uit de uitvoer identificeren de **LicensingIntranetDistributionPointUrl** waarde.
    > 
    >     Bijvoorbeeld: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  Verwijderen van de waarde **https://** en **_wmcs/licensing** van deze tekenreeks. De resterende waarde is de FQDN-naam van uw Microsoft RMS-service. In ons voorbeeld zouden de FQDN-naam van de Microsoft RMS-service de volgende waarde:
    > 
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  De volgende map en alle bestanden die zich verwijderen: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Uw Office-toepassingen en exemplaren van File Explorer opnieuw gestart.

### <a name="BKMK_Office2010ForceUpdate"></a>Office 2010: Hoe vernieuwd voor een gewijzigde aangepaste sjabloon
Door het bewerken van het register op de computers met Office 2010 kunt u een waarde instellen zodat gewijzigde sjablonen worden vernieuwd op computers zonder te hoeven wachten gebruikers zich afmelden en weer aan. U kunt ook een onmiddellijke vernieuwing afdwingen door de bestaande gegevens in een registerwaarde verwijderen.

> [!WARNING]
> Als u de Register-Editor onjuist gebruikt, kunt u er problemen die mogelijk moet u het besturingssysteem opnieuw installeren. Microsoft kan niet garanderen dat u problemen die het gevolg oplossen kunt van onjuist gebruik van de Register-Editor. Gebruik de Register-Editor voor uw eigen risico.

##### De updatefrequentie wijzigen

1.  Met een Registereditor, maak een nieuwe registerwaarde met de naam **UpdateFrequency** en definieer een geheel getal voor de gegevensbron waarmee de frequentie in dagen eventuele wijzigingen aan een gedownloade sjabloon kan worden gedownload. Gebruik de volgende tabel om de registerpad voor het maken van deze nieuwe registerwaarde te vinden.

    |Register-pad|Type|Waarde|
    |----------------|--------|----------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_DWORD|UpdateFrequency|

2.  Als u afdwingen dat een onmiddellijke vernieuwing van de sjablonen wilt, gaat u naar de volgende procedure. Anders wordt nu opnieuw opstarten uw Office-toepassingen.

##### Voor het afdwingen van een onmiddellijk vernieuwen

1.  Met een Registereditor, verwijdert u de gegevens voor de **LastUpdatedTime** waarde. Bijvoorbeeld, de gegevens mogelijk weergegeven **2015-04-20T15:52**; 2015 verwijderen-04-20T15:52 zodat er zijn geen gegevens wordt weergegeven. Gebruik de volgende tabel om de registerpad als u wilt verwijderen van deze gegevens registerwaarden te vinden.

    |Register-pad|Type|Waarde|
    |----------------|--------|----------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_SZ|lastUpdatedTime|

2.  De volgende map en alle bestanden die zich verwijderen: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Opnieuw opstarten uw Office-toepassingen.

## <a name="BKMK_PowerShellTemplates"></a>Windows PowerShell-verwijzing
Alles wat u kunt uitvoeren in de Azure-beheerportal maken en beheren van sjablonen, kunt u doen vanaf de opdrachtregel met behulp van Windows PowerShell. U kunt bovendien exporteren en importeren van sjablonen, zodat u kunt sjablonen tussen tenants kopiëren of bulksgewijs bewerkingen van complexe eigenschappen in sjablonen, zoals multilingual namen en beschrijvingen uitvoeren.

U kunt ook gebruiken exporteren en importeren om een back-up en herstellen van aangepaste sjablonen, wordt aangeraden, regelmatig back-up van de aangepaste sjablonen, zodat als u een wijziging die niet is bedoeld aanbrengt, u gemakkelijk naar een eerdere versie terugkeren kunt.

> [!IMPORTANT]
> Als u Windows PowerShell wilt Azure RMS rechten beleidssjablonen maken en beheren, moet u er ten minste versie 2.0.0.0 van de [Windows PowerShell-module voor Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Als u deze Windows PowerShell-module eerder hebt geïnstalleerd, voert u de volgende opdracht in een PowerShell-venster om te controleren van het versienummer: `(Get-Module aadrm -ListAvailable).Version`

Zie voor installatie-instructies [Installatie van Windows PowerShell voor Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

De cmdlets die ondersteuning bieden voor sjablonen maken en beheren:

-   [Voeg AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)

-   [Exporteren AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)

-   [Get-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727079.aspx)

-   [Get-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727081.aspx)

-   [Importeer AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)

-   [Nieuwe AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)

-   [Verwijder AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727082.aspx)

-   [Set AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)

## Volgende stappen
Nadat u aangepaste sjablonen voor Azure Rights Management hebt geconfigureerd, gebruikt u de [Azure Rights Management-implementatieschema](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) om te controleren of er andere configuratiestappen die u kunt doen zijn voor de implementatie [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] gebruikers en beheerders. Als er geen andere configuratiestappen die u nodig hebt om te doen, Zie [Met behulp van Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) voor operationele richtlijnen ter ondersteuning van op een succesvolle implementatie voor uw organisatie.

## Zie ook
[Azure Rights Management configureren](../Topic/Configuring_Azure_Rights_Management.md)

