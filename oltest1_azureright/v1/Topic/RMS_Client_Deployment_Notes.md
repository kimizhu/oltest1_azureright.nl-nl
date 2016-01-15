---
description: na
keywords: na
title: RMS Client Deployment Notes
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03cc8c6f-3b63-4794-8d92-a5df4cdf598f
---
# Opmerkingen bij de implementatie van de RMS-Client
Rights Management-Service (client RMS) clientversie 2 is ook wel bekend als de client MSIPC. Het is software voor Windows-computers die met Microsoft Rights Management communiceert services lokaal of beheerd in de cloud te beschermen toegang tot en gebruik van informatie zoals het doorloopt toepassingen en apparaten binnen de grenzen van uw organisatie of buiten de grenzen. Naast de verzending met de [Rights Management-toepassing voor Windows delen](https://technet.microsoft.com/library/dn919648.aspx), de RMS-client is beschikbaar [als een optionele download](http://www.microsoft.com/download/details.aspx?id=38396) die, met bevestiging en instemming met de gebruiksrechtovereenkomst vrij kan worden gedistribueerd met software van derden zodat clients kunnen worden beveiligd en inhoud die is beveiligd door Rights Management services gebruiken.

Dit onderwerp vindt u de volgende secties:

-   [Die de RMS-Client](#BKMK_RedistributeInstaller)

-   [De RMS-Client installeren](#BKMK_InstallClient)

-   [Vragen en antwoorden over de RMS-Client](#BKMK_QA)

-   [Instellingen voor RMS-Client](#BKMK_Settings)

-   [AD RMS: De RMS-Client beperken vertrouwde AD RMS-Servers](#BKMK_UsingTrustedServers)

-   [Detectie van RMS-Service](#BKMK_ServiceDiscovery)

## <a name="BKMK_RedistributeInstaller"></a>Die de RMS-Client
De RMS-client kan vrijelijk worden gedistribueerd en gebundeld met andere toepassingen en IT-oplossingen. Als u een toepassingsontwikkelaar of de oplossingsprovider van de en wilt distribueren van de RMS-client, hebt u twee opties:

-   Aanbevolen: Het installatieprogramma voor de RMS-client insluiten in uw installatie van de toepassing en in stille modus uitvoert (de **/quiet** switch, aangegeven in de volgende sectie).

-   Controleer de RMS-client een vereiste voor de toepassing. Met deze optie moet u mogelijk gebruikers voorzien van aanvullende instructies te verkrijgen, installeren en hun computers bijwerken met de client voordat uw toepassing kan worden gebruikt.

## <a name="BKMK_InstallClient"></a>De RMS-Client installeren
De RMS-client deel uitmaakt van een uitvoerbaar bestand met de naam van het installatieprogramma **setup_msipc_***&lt; boog &gt;***.exe**, waarbij *&lt; boog &gt;* is **x86** (voor 32-bits client-computers) of **x64** (voor 64-bits clientcomputers). De 64-bits (x 64)-installer-pakket installeert zowel een 32-bits runtime uitvoerbare voor compatibiliteit met de 32-bits toepassingen die worden uitgevoerd op een 64-bits besturingssysteem, evenals een 64-bits runtime uitvoerbare voor native 64-bits toepassingen ondersteunen. Het installatieprogramma van 32-bits (x 86) wordt niet uitgevoerd op een 64-bits Windows-installatie.

> [!NOTE]
> U moet verhoogde bevoegdheden voor het installeren van de RMS-client, zoals een lid van de groep Administrators op de lokale computer.

U kunt de RMS-client installeren met behulp van een van de volgende manieren installeren:

-   **Stille modus.** Met behulp van de **/quiet** overschakelen als onderdeel van de opdrachtregelopties, kunt u de RMS-client zonder interactie installeren op computers. Het volgende voorbeeld ziet een installatie in stille modus voor de RMS-client op een 64-bits client:

    ```
    setup_msipc_x64.exe /quiet
    ```

-   **Interactieve modus.** U kunt ook de RMS-client installeren met behulp van het installatieprogramma GUI-hulpprogramma dat wordt geleverd door de installatiewizard van de RMS-Client. Hiertoe dubbelklikt u op de RMS-client installer-pakket (**setup_msipc_***&lt; boog &gt;***.exe**) in de map waarnaar werd gekopieerd of gedownload op de lokale computer.

## <a name="BKMK_QA"></a>Vragen en antwoorden over de RMS-Client
De volgende sectie bevat veelgestelde vragen over de RMS-client en de antwoorden op deze.

### Welke besturingssystemen ondersteunen de RMS-client?
De RMS-client wordt ondersteund met de volgende besturingssystemen:

|Windows Server-besturingssysteem|Windows Client-besturingssysteem|
|------------------------------------|------------------------------------|
|Windows Server 2012 R2|Windows 8.1|
|Windows Server 2012|Windows 8|
|Windows Server 2008 R2|Windows 7 met minimale van SP1|
|Windows Server 2008 (alleen AD RMS)|Windows Vista met minimale van SP2 (alleen AD RMS)|

### Welke processors of platforms ondersteund door de RMS-client?
De RMS-client wordt ondersteund op x 86 en x 64-platforms te berekenen.

### Waar is de RMS-client geïnstalleerd?
De RMS-client wordt standaard geïnstalleerd in %ProgramFiles%\Active Directory Rights Management Services Client 2. &lt; secundair versienummer &gt;.

### Welke bestanden zijn gekoppeld aan de RMS-clientsoftware?
De volgende bestanden zijn geïnstalleerd als onderdeel van de clientsoftware RMS:

-   Msipc.dll

-   Ipcsecproc.dll

-   Ipcsecproc_ssp.dll

-   MSIPCEvents.man

Naast deze bestanden de RMS-client geïnstalleerd multilingual interface (MUI) ondersteuning gebruikersbestanden in 44 talen. Om te controleren of de ondersteunde talen, voert u de installatie van RMS-client en wanneer de installatie voltooid is, controleert u de inhoud van de ondersteuning voor meerdere talen mappen onder het standaardpad.

### Is de RMS-client standaard opgenomen wanneer ik een ondersteund besturingssysteem installeren?
Nr. Deze versie van de RMS-client wordt geleverd als een optionele download die kan worden geïnstalleerd afzonderlijk op computers waarop ondersteunde versies van de Microsoft Windows-besturingssysteem wordt uitgevoerd.

### De RMS-client automatisch bijgewerkt door Microsoft Update?
Als u deze RMS-client geïnstalleerd via de optie stille installatie, neemt de RMS-client de huidige instellingen van Microsoft Update. Als u de RMS-client met de GUI-hulpprogramma Setup geïnstalleerd, wordt de installatiewizard van de RMS-client vraagt u Microsoft Update inschakelen.

## <a name="BKMK_Settings"></a>Instellingen voor RMS-Client
De volgende sectie bevat instellingen voor informatie over de RMS-client. Deze informatie kan handig zijn als u problemen hebt met toepassingen of services die gebruikmaken van de RMS-client.

> [!NOTE]
> Sommige instellingen, is afhankelijk van of de toepassing RMS enlightened wordt uitgevoerd als een toepassing van de client-modus (zoals Microsoft Word en Outlook of de RMS-toepassing voor delen) of servertoepassing-modus (zoals SharePoint en Exchange).  Deze instellingen zijn in de volgende tabellen aangeduid als **clientmodus** en **modus**, respectievelijk.

### Waar de winkels RMS-Client op clientcomputers licenties
De RMS-client licenties opgeslagen op de lokale schijf en ook in de cache opgeslagen sommige gegevens in het Windows-register.

|Beschrijving|Client-modus paden|Server-modus paden|
|----------------|----------------------|----------------------|
|De opslaglocatie van licentie|%localappdata%\Microsoft\MSIPC|%ALLUSERSPROFILE%\Microsoft\MSIPC\Server\*&lt; SID &gt;*\|
|Sjabloon archieflocatie|%localappdata%\Microsoft\MSIPC\Templates|%ALLUSERSPROFILE%\Microsoft\MSIPC\Server\Templates\*&lt; SID &gt;*\|
|Registerlocatie|HKEY_CURRENT_USER<br /> \Software<br /> \Classes<br /> \Local instellingen<br /> \Software<br /> \Microsoft<br /> \MSIPC|HKEY_CURRENT_USER<br /> \Software<br /> \Microsoft<br /> \MSIPC<br /> \Server<br /> \*&lt; SID &gt;*|
> [!NOTE]
> *&lt; SID &gt;* is de veilige id (SID) voor het account waaronder de servertoepassing wordt uitgevoerd. Bijvoorbeeld als de toepassing wordt uitgevoerd onder de ingebouwde netwerkserviceaccount, vervangen *&lt; SID &gt;* met de waarde van de bekende beveiligings-id voor dat account (S-1-5-20).

### Windows-registerinstellingen voor de RMS-Client
Registersleutels voor Windows kunt u instellen of wijzigen van bepaalde configuraties RMS-client. Bijvoorbeeld als een beheerder voor RMS enlightened toepassingen die met de AD RMS-servers communiceren u wilt bijwerken van de locatie van de enterprise (onderdrukking van de AD RMS-server die momenteel is geselecteerd voor publicatie), afhankelijk van de huidige locatie van de clientcomputer in uw Active Directory-topologie. Of u kunt de tracering RMS op de clientcomputer helpen bij het oplossen van een probleem met een toepassing RMS enlightened inschakelen. Gebruik de volgende tabel om te identificeren van de registerinstellingen die u voor de RMS-client wijzigen kunt.

|Taak|Instellingen|
|--------|----------------|
|AD RMS: De locatie van de onderneming voor een clientcomputer bijwerken|Update voor de volgende registersleutels:<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification<br />    REG_SZ: standaard<br />    **Waarde:**&lt; http- of https-&gt; :// *RMS_Cluster_Name*/_wmcs/Certification<br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing<br />    REG_SZ: standaard<br />    **Waarde:** &lt; http- of https-&gt; :// *RMS_Cluster_Name*/_wmcs/Licensing|
|En tracering uitschakelen|Update voor de volgende registersleutel:<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC<br />    REG_DWORD: Tracering<br />    **Waarde:** 1 tot en met tracering, 0 om uit te schakelen tracering (standaard) inschakelen|
|De frequentie in dagen voor het vernieuwen van sjablonen wijzigen|Opgeven hoe vaak de volgende registerwaarden sjablonen wordt vernieuwd op basis van de computer van de gebruiker als de waarde TemplateUpdateFrequencyInSeconds niet is ingesteld.  Als geen van deze waarden zijn ingesteld, is het interval voor het vernieuwen van standaard voor toepassingen die gebruikmaken van de RMS-client (versie 1.0.1784.0) te downloaden van sjablonen 1 dag. Versies voorafgaand aan dit hebben een standaardwaarde van 7 dagen.<br /><br />**Clientmodus:**<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: TemplateUpdateFrequency<br />    **Waarde:** Een geheel getal dat het aantal dagen (minimaal 1) tussen downloads.<br /><br />**Server-modus:**<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*&lt; SID &gt;*<br />    REG_DWORD: TemplateUpdateFrequency<br />    **Waarde:** Een geheel getal dat het aantal dagen (minimaal 1) tussen downloads.|
|De frequentie in seconden voor het vernieuwen van sjablonen wijzigen **Important:** Als deze is opgegeven, wordt de waarde voor het vernieuwen van sjablonen in dagen genegeerd. Geef een of andere, niet beide.|Opgeven hoe vaak de volgende registerwaarden sjablonen wordt vernieuwd op basis van de computer van de gebruiker. Als deze waarde of wijzigen van de frequentie in dagen (TemplateUpdateFrequency) niet is ingesteld, is het interval voor het vernieuwen van standaard voor toepassingen die gebruikmaken van de RMS-client (versie 1.0.1784.0) te downloaden van sjablonen 1 dag. Versies voorafgaand aan dit hebben een standaardwaarde van 7 dagen.<br /><br />**Clientmodus:**<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: TemplateUpdateFrequencyInSeconds<br />    **Waarde:** Een geheel getal dat Hiermee geeft u het aantal seconden (minimaal 1) tussen downloads.<br /><br />**Server-modus:**<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*&lt; SID &gt;*<br />    REG_DWORD: TemplateUpdateFrequencyInSeconds<br />    **Waarde:** Een geheel getal dat Hiermee geeft u het aantal seconden (minimaal 1) tussen downloads.|
|AD RMS: Sjablonen direct bij de volgende publicatieservers aanvraag downloaden|Tijdens het testen en evaluaties kunt u de RMS-client zo snel mogelijk sjablonen downloaden. U doet dit door de volgende registersleutel verwijderen en de RMS-client wordt sjablonen direct bij de volgende publicatieservers aanvraag downloaden in plaats van de tijd die is opgegeven door de registerinstelling TemplateUpdateFrequency wacht:<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\ &lt; servernaam &gt; \Template **Note:** &lt; servernaam &gt; kan externe (corprights.contoso.com) en (corprights) interne URL's en daarom twee verschillende posten hebben.|
|AD RMS: Ondersteuning voor federatieve verificatie inschakelen|Als de RMS-clientcomputer verbinding met een AD RMS-cluster maakt met behulp van een federatieve vertrouwensrelatie, moet u de thuisrealm federatieserver configureren.<br /><br />-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />    REG_SZ: FederationHomeRealm<br />    **Waarde:** De waarde van deze registervermelding is de uniform resource identifier (URI) voor de federation service (bijvoorbeeld "https://fs-01.contoso.com").|
|AD RMS: Ter ondersteuning van partner federation-servers die verificatie op basis van formulieren op gebruikersinvoer vereisen|Standaard de RMS-client in stille modus werkt en invoer van de gebruiker is niet vereist. Partner federation-servers kunnen, worden geconfigureerd voor vereisen gebruikersinvoer, zoals in verificatie op basis van formulieren. In dit geval moet u de RMS-client configureren negeren stille modus zodat het formulier federatieve verificatie wordt weergegeven in een browservenster en de gebruiker wordt geplaatst voor verificatie.<br /><br />-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />    REG_DWORD: EnableBrowser **Note:** Als de federatieserver is geconfigureerd voor verificatie op basis van formulieren gebruiken, moet deze sleutel is vereist. Als de federatieserver is geconfigureerd voor gebruik van geïntegreerde Windows-verificatie, is deze sleutel niet vereist.|
|AD RMS: ILS-serviceverbruik blokkeren|De RMS-client kan in beslag inhoud beveiligd door de ILS-service standaard, maar kunt u de client voor deze service blokkeren door de volgende registersleutel instellen. Als deze registersleutel is ingesteld op de ILS-service blokkeren, retourneert alle pogingen om te openen en gebruiken van inhoud beveiligd door de ILS-service de volgende fout:<br />HRESULT_FROM_WIN32(ERROR_ACCESS_DISABLED_BY_POLICY)<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: **DisablePassportCertification**<br />    **Waarde:** 1 blokkeren ILS verbruik, 0 om toe te staan ILS verbruik (standaard)|

### Sjabloondistributie voor de RMS-Client beheren
Sjablonen kunnen u gemakkelijk voor gebruikers en beheerders snel toepassen Rights Management-beveiliging en sjablonen de RMS-client automatisch gedownload uit de RMS-servers of -service als u de sjablonen in de locatie van de volgende map, wordt de RMS-client niet alle sjablonen downloaden van de standaardlocatie en in plaats daarvan de sjablonen die u hebt ingevoerd in deze map downloaden. De RMS-client mogelijk blijven sjablonen downloaden van andere beschikbare RMS-servers.

**Clientmodus:** %localappdata%\Microsoft\MSIPC\UnmanagedTemplates

**Modus:** %allusersprofile%\Microsoft\MSIPC\Server\UnmanagedTemplates\*&lt; SID &gt;*

Wanneer u deze map gebruikt, is er geen speciale naamgevingsconventie vereist, behalve dat de sjablonen moeten worden uitgegeven door de RMS-server of service en ze moeten de bestandsnaamextensie hebben. Contoso Confidential.xml of Contoso ReadOnly.xml zijn bijvoorbeeld een geldige naam.

## <a name="BKMK_UsingTrustedServers"></a>AD RMS: De RMS-Client beperken vertrouwde AD RMS-Servers
De RMS-client kan worden beperkt tot het gebruik van alleen specifieke vertrouwde AD RMS-servers door de volgende wijzigingen aanbrengen in het Windows-register op de lokale computer.

**Om in te schakelen beperken RMS vertrouwde client alleen AD RMS-servers**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_DWORD: AllowTrustedServersOnly

    **Waarde:** Als u een andere waarde dan nul opgeeft, wordt alleen de opgegeven servers die zijn geconfigureerd in de lijst TrustedServers en de Azure Rights Management-service de vertrouwensrelatie van de RMS-client.

**Leden toevoegen aan de lijst met vertrouwde AD RMS-servers**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_SZ: *&lt; URL_or_HostName &gt;*

    **Waarde:** De tekenreekswaarden in deze sleutel registerlocatie toegevoegd kunnen worden beide DNS-domein naamindeling (bijvoorbeeld **adrms.contoso.com**) of de volledige URL's op vertrouwde AD RMS-servers (bijvoorbeeld **https://adrms.contoso.com**). Als een opgegeven URL met begint **https://**,  de RMS-client gebruiken SSL of TLS contact opnemen met de opgegeven AD RMS-server.

## <a name="BKMK_ServiceDiscovery"></a>Detectie van RMS-Service
Detectie van RMS-service kan de RMS-client controleren welke RMS-server of kan communiceren met voordat inhoud is beveiligd. Detectie-service kan ook gebeuren als de RMS-client beveiligde inhoud verbruikt, maar dit minder zullen is worden uitgevoerd omdat het beleid is gekoppeld aan de inhoud het gewenste RMS-server of de service bevat en als dat mislukt de client u detectie-service voert is.

Detectie-service wordt eerst gezocht naar een lokale versie van Rights Management (AD RMS). Als dat niet lukt, zoekt detectie-service automatisch naar de cloud-versie van Rights Management (Azure RMS).

Detectie-service uitvoeren voor een on-premises implementatie, controleert u de RMS-client de volgende:

1.  Het Windows-register op de lokale computer: Als service detectie-instellingen zijn geconfigureerd in het register, worden deze instellingen eerst geprobeerd.  Deze instellingen zijn niet geconfigureerd in het register.

2.  Active Directory Domain Services: Een computer domein-samengevoegde wordt Active Directory voor een service connection point (SCP). Als een SCP is geregistreerd, wordt de URL van de RMS-server heeft geretourneerd aan de RMS-client te gebruiken.

### AD RMS: Detectie van Server-Side-Service inschakelen met Active Directory
Als uw account heeft onvoldoende bevoegdheden (Ondernemingsadministrators en lokale beheerder van de AD RMS-server), kunt u automatisch registreert een service connection point (SCP) tijdens de installatie van de AD RMS-hoofdserver cluster. Als een SCP al in de forest bestaat, moet u eerst de bestaande SCP verwijderen voordat u kunt een nieuw registreren.

U kunt registreren en verwijderen van een SCP nadat AD RMS met behulp van de volgende procedure is geïnstalleerd. Voordat u begint, zorg ervoor dat uw account de vereiste machtigingen (Ondernemingsadministrators en lokale beheerder van de AD RMS-server heeft).

##### Detectie van AD RMS-service inschakelen met een SCP registreren in Active Directory

1.  Open de console Active Directory Management-Services op de AD RMS-server:

    -   Als u van Windows Server 2008 R2 of Windows Server 2008 gebruikmaakt, klikt u op **Start**, klikt u op **Systeembeheer**, en klik vervolgens op **Active Directory Rights Management Services**.

    -   Als u van Windows Server 2012 R2 of Windows Server 2012 in Serverbeheer gebruikmaakt, klikt u op **hulpprogramma's voor**, en klik vervolgens op **Active Directory Rights Management Services**.

2.  Met de rechtermuisknop op de AD RMS-cluster in de AD RMS-console en klik vervolgens op **eigenschappen**.

3.  Klik op de **SCP** tabblad.

4.  Selecteer de **SCP wijzigen** selectievakje.

5.  Selecteer de **SCP ingesteld met het huidige certificeringscluster** optie en klik vervolgens op **OK**.

### Detectie van Client-Side-Service inschakelen via het Windows-register
Als een alternatief voor het gebruik van een SCP of waarop een SCP niet bestaat, kunt u het register op de client zodat de RMS-client kan worden gevonden voor de AD RMS-server.

##### Detectie van client-side AD RMS-service inschakelen via het Windows-register

1.  Open de Windows-Register-editor, Regedit.exe:

    -   Typ op de clientcomputer in het venster uitvoeren **regedit**, en druk vervolgens op ENTER om de Register-Editor.

2.  De Register-Editor, gaat u naar **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC**.

    > [!IMPORTANT]
    > Als u een 32-bits toepassing op een 64-bits computer worden uitgevoerd, is het pad als volgt: 
    > **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC**

3.  Voor het maken van de subsleutel ServiceLocation met de rechtermuisknop op **MSIPC**, wijs **Nieuw**, klikt u op **sleutel**, en typ **ServiceLocation**.

4.  Voor het maken van de subsleutel EnterpriseCertification met de rechtermuisknop op **ServiceLocation**, wijs **Nieuw**, klikt u op **sleutel**, en typ **EnterpriseCertification**.

5.  Dubbelklik op de enterprise-certificering-URL om de **(standaard)** waarde onder de **EnterpriseCertification** subsleutel, en wanneer de **tekenreeks bewerken** dialoogvenster wordt weergegeven, voor **Waardegegevens**, type &lt;http or https&gt;://*AD RMS_cluster_name*/_wmcs/Certification, en klik vervolgens op **OK**.

6.  Voor het maken van de subsleutel EnterprisePublishing met de rechtermuisknop op **ServiceLocation**, wijs **Nieuw**, klikt u op **sleutel**, en typ EnterprisePublishing.

7.  Dubbelklik op om de URL voor publicatie onderneming **(standaard)** , onder de **EnterprisePublishing** subsleutel, en wanneer de **tekenreeks bewerken** dialoogvenster wordt weergegeven, typt u voor **Waardegegevens** de volgende &lt;http or https&gt;://*AD RMS_cluster_name*/_wmcs/Licensing, en klik vervolgens op **OK**.

8.  Sluit de Register-Editor.

Als de RMS-client een SCP een query uitgevoerd op Active Directory niet vinden en deze niet is opgegeven in het register kan, mislukken detectie van serviceaanvragen voor AD RMS.

### Omleiden verkeer van Server-licentieverlening
In sommige gevallen moet u mogelijk om verkeer tijdens de detectie van service, bijvoorbeeld wanneer twee organisaties worden samengevoegd en de oude licenties server in een organisatie is buiten gebruik gesteld en clients moeten worden omgeleid naar een nieuwe licenties server. Of u migreert van AD RMS naar Azure RMS. Gebruik de volgende procedure om in te schakelen licenties omleiding.

##### RMS-licentieverlening omleiding via het Windows-register inschakelen

1.  Open de Windows-Register-editor, Regedit.exe:

    -   Typ op de clientcomputer in het venster uitvoeren **regedit**, en druk vervolgens op ENTER om de Register-Editor.

2.  De Register-Editor, navigeert u naar een van de volgende:

    -   Voor 64-bits versie van Office op x 64 platform: HKLM\SOFTWARE\Microsoft\MSIPC\Servicelocation

    -   Voor 32-bits versie van Office op x 64 platform: HKLM\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Servicelocation

3.  Een subsleutel LicensingRedirection maken met de rechtermuisknop op **Servicelocation**, wijs **Nieuw**, klikt u op **sleutel**, en typ **LicensingRedirection**.

4.  De licenties omleiding stelt met de rechtermuisknop op de **LicensingRedirection** subsleutel, schakelt **Nieuw**, en selecteer vervolgens **tekenreekswaarde**.  Voor **naam**, de vorige server-licentieverlening URL opgeven en voor **waarde** de nieuwe server-licentieverlening URL opgeven.

    U kunt bijvoorbeeld de volgende waarden invoeren om het omleiden van een server op Contoso.com-licentieverlening naar een voor Fabrikam.com:

    **Naam:** `https://contoso.com/_wmcs/licensing`

    **Waarde:** `https://fabrikam.com/_wmcs/licensing`

    > [!NOTE]
    > Als de oude licenties server heeft intranet en extranet-URL's opgegeven vervolgens een nieuwe naam en waardetoewijzing moet worden ingesteld voor beide van deze URL's onder de sleutel LicensingRedirection.

5.  Herhaal de vorige stap voor alle servers die moeten worden omgeleid.

6.  Sluit de Register-Editor.

