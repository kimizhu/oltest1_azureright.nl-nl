---
description: na
keywords: na
title: Deploying the Azure Rights Management Connector
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 90e7e33f-9ecc-497b-89c5-09205ffc5066
---
# Implementatie van de Connector van de Azure Rights Management
Deze informatie gebruiken voor meer informatie over de connector Microsoft Rights Management (RMS) en hoe u deze kunt gebruiken om informatie te beschermen met bestaande lokale implementaties die gebruikmaken van Microsoft Exchange Server, Microsoft SharePoint Server of bestandsservers waarop Windows Server wordt uitgevoerd en de mogelijkheid bestand classificatie infrastructuur (FCI) van Bestandsserverbronbeheer gebruiken.

> [!TIP]
> Voor een op hoog niveau voorbeeldscenario met schermafdrukken, raadpleegt u de [Bestanden op bestandsservers met Windows Server en bestand classificatie infrastructuur beveiligen automatisch](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Example_FCI) sectie de [Wat is Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) onderwerp.

## <a name="OverviewConnector"></a>Overzicht van de Microsoft Rights Management-connector
De connector voor Microsoft Rights Management (RMS) kunt u snel bestaande lokale servers inschakelen voor het gebruik van hun functionaliteit Information Rights Management (IRM) met de cloud-gebaseerde Microsoft Rights Management-service (Azure RMS). Met deze functionaliteit IT en gebruikers kunnen gemakkelijk beschermen documenten en foto's binnen uw organisatie en buiten, zonder te hoeven installeren aanvullende infrastructuur of relaties met andere organisaties vertrouwensrelatie tot stand brengen. U kunt deze connector zelfs als sommige gebruikers verbinding met de online services in een scenario hybride maken. Bijvoorbeeld postvakken van enkele gebruikers gebruik Exchange Online en postvakken van enkele gebruikers Exchange Server gebruikt. Nadat u de RMS-connector hebt geïnstalleerd, alle gebruikers kunnen worden beveiligd en e-mailberichten en bijlagen gebruiken met behulp van Azure RMS en beveiliging van gegevens tussen de twee implementatieconfiguraties naadloos.

De RMS-connector is een klein willen-service op locatie te installeren op servers waarop Windows Server 2012 R2, Windows Server 2012 of Windows Server 2008 R2 wordt uitgevoerd. Naast de connector op fysieke computers wordt uitgevoerd, kunt u deze ook op virtuele machines, met inbegrip van Azure IaaS VM's uitvoeren. Nadat u installeren en configureren van de connector, wordt deze fungeert als een communicatie-interface (relay) tussen de lokale servers en de cloudservice.

Als u uw eigen sleutel tenant beheren voor Azure RMS (het Breng u eigenaar bent sleutel of BYOK scenario), de RMS-connector en de lokale-servers die gebruikmaken van deze de hardware HSM (security module) met de sleutel van de tenant niet openen. Dit is omdat alle cryptografische bewerkingen die gebruikmaken van de tenant-sleutel worden uitgevoerd in Azure RMS, en niet op locatie.

![](../Image/RMS_connector.png)

De RMS-connector ondersteunt de volgende lokale servers: Exchange Server, SharePoint Server en bestandsservers waarop Windows Server wordt uitgevoerd en gebruik bestand classificatie infrastructuur te classificeren en beleid toepassen op de Office-documenten in een map. Als u beveiligen van alle bestandstypen met bestand classificatie wilt, moet u de RMS-connector niet gebruiken, maar in plaats daarvan gebruiken de [RMS Protection cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx).

> [!NOTE]
> Zie voor ondersteunde versies van deze servers lokale "On-premises-servers die ondersteuning van Azure RMS in de [Toepassingen die ondersteuning van Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) sectie van de [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) onderwerp.

Gebruik de volgende secties om te plannen, installeren en configureren van de RMS-connector. Vervolgens moet u een bericht installatie configuratie doen zodat uw servers van de connector gebruikmaken kunnen.

-   [Prerequisites for the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_Prereqs)

-   **Stap 1:**  [Installing the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_InstallingConnector)

-   **Stap 2:**  [Entering credentials](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#EnteringCredentials)

-   **Stap 3:**  [Authorizing servers to use the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#AuthorizingServers)

-   **Stap 4:**  [Configuring load balancing and high availability](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#ConfiguringConnector)

-   Optioneel: [Configuring the RMS connector to use HTTPS](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringHTTPS)

-   Optioneel: [Configuring the RMS connector for a web proxy server](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringWebProxy)

-   Optioneel: [Installing the RMS connector administration tool on administrative computers](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_InstallingStandaloneTool)

-   **Stap 5:**  [Configuring servers to use the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#ConfiguringServers)

    -   [Configuring an Exchange server to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ExchangeServer)

    -   [Configuring a SharePoint server to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringSharePoint)

    -   [Configuring a file server for File Classification Infrastructure to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_FileServer)

-   [Next steps](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_NextSteps)

## <a name="BKMK_Prereqs"></a>Vereisten voor de RMS-connector
Voordat u de RMS-connector hebt geïnstalleerd, ervoor zorgen dat de volgende vereisten zijn.

|Vereiste|Meer informatie|
|------------|-------------------|
|De service Rights Management (RMS) is geactiveerd|[Azure Rights Management activeren](../Topic/Activating_Azure_Rights_Management.md)|
|Directory-synchronisatie tussen uw Active Directory-forest en Azure Active Directory|Na activering van RMS moet Azure Active Directory worden geconfigureerd met de gebruikers en groepen in uw Active Directory-database. **Important:** U moet deze stap directory synchronisatie voor de RMS-connector te werken, zelfs voor een testnetwerk doen. Maar u Office 365 en Azure Active Directory gebruiken kunt met behulp van accounts die u handmatig in Azure Active Directory maken, deze connector is vereist dat de accounts in Azure Active Directory worden gesynchroniseerd met Active Directory Domain Services; handmatige Wachtwoordsynchronisatie is niet voldoende.<br />Voor meer informatie, Zie de volgende bronnen:<br /><br />-   [Instructies voor het configureren van uw Azure AD-tenant](http://technet.microsoft.com/library/hh967611.aspx)<br />-   [Instructies voor het synchroniseren van adreslijsten met AAD met DirSync inschakelen](http://technet.microsoft.com/library/hh967642.aspx)|
|Optioneel maar aanbevolen:<br /><br />-   Federatie tussen uw lokale Active Directory en Azure Active Directory inschakelen|U kunt identiteitsfederatie tussen uw lokale en Azure Active Directory inschakelen. Deze configuratie wordt een naadloze gebruikerservaring kan via eenmalige aanmelding bij de RMS-service. Zonder eenmalige aanmelding voor gebruikers voor hun referenties gevraagd voordat rechten beveiligde inhoud kan worden gebruikt.<br /><br />Zie voor instructies federation configureren met Active Directory Federation Services (AD FS) tussen Active Directory Domain Services en Azure Active Directory, de [Checklist: Gebruik AD FS te implementeren en beheren van eenmalige aanmelding](http://technet.microsoft.com/library/jj205462.aspx) in de bibliotheek voor Windows Server.|
|Ten minste twee lidcomputers waarop de RMS-connector te installeren:<br /><br /><ul><li>Een 64-bits fysieke of virtuele computer met een van de volgende besturingssystemen:<br /><br /><ul><li>Windows Server 2012 R2</li><li>Windows Server 2012</li><li>Windows Server 2008 R2</li></ul></li><li>Ten minste 1 GB RAM-geheugen</li><li>Een minimum van 64 GB schijfruimte</li><li>Ten minste één netwerkinterface</li><li>Toegang tot het Internet via een firewall (of webproxy) die geen verificatie nodig</li><li>Moet zich in een forest of domein dat andere forests in de organisatie die installaties van Exchange of SharePoint-servers die u wilt gebruiken met de RMS-connector bevatten vertrouwensrelaties</li></ul>|Voor fouttolerantie en hoge beschikbaarheid, moet u de RMS-connector installeren op een minimum van twee computers. **Tip:** Als u gebruikmaakt van Outlook Web Access of mobiele apparaten die gebruikmaken van Exchange ActiveSync IRM en is het belangrijk dat u toegang tot e-mailberichten en bijlagen die worden beschermd door Azure RMS onderhouden, wordt u aangeraden dat u een groep taakverdeling connector servers om te controleren of hoge beschikbaarheid implementeren.<br />U hoeft niet aangewezen servers om uit te voeren van de connector, maar moet u deze installeren op een afzonderlijke computer van de servers die door de connector wordt gebruikt. **Important:** Installeer de connector niet op een computer waarop Exchange Server, SharePoint-Server of een bestandsserver die is geconfigureerd voor bestand classificatie infrastructuur als u wilt gebruiken de functionaliteit van deze services met Azure RMS wordt uitgevoerd. Installeer deze connector ook niet op een domeincontroller.|

## <a name="BKMK_InstallingConnector"></a>De connector RMS installeren
Als u de vereiste items in de vorige sectie hebt gecontroleerd, gebruikt u de volgende instructies voor het installeren van de RMS-connector:

1.  Zoek de computers (minimaal twee) die de RMS-connector wordt uitgevoerd. Zij moeten voldoen aan de minimale vereisten vermeld in de voorgaande sectie.

    > [!NOTE]
    > Een enkele RMS-connector (bestaande uit meerdere servers voor hoge beschikbaarheid) installeert u per tenant (Office 365-tenant of Azure AD-tenant). In tegenstelling tot de Active Directory RMS u beschikt niet over een RMS-connector in elke forest installeren.

2.  Download de bronbestanden voor de RMS-connector van de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106).

    Als u wilt de RMS-connector hebt geïnstalleerd, RMSConnectorSetup.exe te downloaden.

    Bovendien:

    -   Als u later configureren van de connector van een 32-bits computer wilt, ook RMSConnectorAdminToolSetup_x86.exe te downloaden.

    -   Als u gebruiken van de server configuration tool voor de RMS-connector wilt, klikt u om de configuratie van de registerinstellingen op u lokale servers, automatiseren ook downloaden GenConnectorConfig.ps1.

3.  Uitvoeren op de computer waarop u wilt installeren van de RMS-connector **RMSConnectorSetup.exe** met beheerdersbevoegdheden.

4.  Selecteer op de pagina van de pagina Microsoft Rights Management-Connector Setup **installeren Microsoft Rights Management-connector op de computer**, en klik vervolgens op **volgende**.

5.  Gelezen en ga akkoord met de licentievoorwaarden van de RMS-connector en klik vervolgens op **volgende**.

Geef een account en wachtwoord de RMS-connector configureren om door te gaan.

## <a name="EnteringCredentials"></a>Invoeren van referenties
Voordat u de RMS-connector configureren kunt, moet u referenties voor een account met voldoende machtigingen heeft voor de RMS-connector hebt geconfigureerd.

Als u hebt geïmplementeerd bovendien [onboarding besturingselementen](https://technet.microsoft.com/library/jj658941.aspx), zorg ervoor dat het account dat u opgeeft kan om inhoud te beschermen. Als u de mogelijkheid om inhoud aan de groep "IT-afdeling" te beschermen beperkt, moet het account dat u hier een lid van de groep zijn. Als dat niet het geval is, ziet u het foutbericht weergegeven: **Het detecteren van de locatie van de beheerservice en de organisatie is mislukt. Zorg ervoor dat Microsoft Rights Management-service is ingeschakeld voor uw organisatie.**

U kunt een account met een van de volgende bevoegdheden:

-   **Office 365-Tenantbeheerder**: Een account dat wordt een globale beheerder voor uw Office 365-tenant.

-   **Microsoft RMS globale Tenantbeheerder**: Een account met beheerdersmachtigingen op de Microsoft RMS-tenant.

-   **Microsoft RMS-connector beheerder**: Een account in Azure Active Directory die rechten om te installeren en beheren van de RMS-connector voor de organisatie is toegekend.

    > [!NOTE]
    > Als u de connector voor Microsoft RMS Administrator-account gebruiken wilt, moet u eerst de volgende stappen uit om de beheerdersrol RMS-connector toewijzen doen:
    > 
    > 1.  Op dezelfde computer downloaden en installeren van Windows PowerShell voor Rights Management. Zie voor meer informatie [Installatie van Windows PowerShell voor Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).
    > 
    >     Start van Windows PowerShell met de **Als administrator uitvoeren** opdracht en verbinding maken met de Azure RMS-service met behulp van de [Connect AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629415.aspx) opdracht:
    > 
    >     ```
    >     Connect-AadrmService                   //provide Office365 Tenant Administrator or Microsoft RMS Tenant Global Administrator credential
    >     ```
    > 2.  Voer de [toevoegen AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/windowsazure/dn629417.aspx) -opdracht, met slechts één van de volgende parameters:
    > 
    >     ```
    >     Add-AadrmRoleBasedAdministrator -EmailAddress <email address> -Role "ConnectorAdministrator"
    >     ```
    > 
    >     ```
    >     Add-AadrmRoleBasedAdministrator -ObjectId <object id> -Role "ConnectorAdministrator"
    >     ```
    > 
    >     ```
    >     Add-AadrmRoleBasedAdministrator -SecurityGroupDisplayName <group Name> -Role "ConnectorAdministrator"
    >     ```
    >     Typ bijvoorbeeld: **Add-AadrmRoleBasedAdministrator -EmailAddress melisa@contoso.com -Role " ConnectorAdministrator "**
    > 
    >     Hoewel deze opdrachten met de rol ConnectorAdministrator, ook u de rol GlobalAdministrator hier ook.

Tijdens de installatie van de connector RMS alle vereiste software is gevalideerd en geïnstalleerd, Internet Information Services (IIS) is geïnstalleerd als dit nog niet geïnstalleerd en de connector-software is geïnstalleerd en geconfigureerd. Bovendien is RMS voorbereid voor configuratie door het maken van het volgende:

-   Een lege tabel geautoriseerd zijn om de connector gebruiken om te communiceren met Azure RMS-servers. U wordt later servers toevoegen aan deze tabel.

-   Een verzameling van beveiligingstokens voor de connector die bewerkingen met Azure RMS toestaan. Deze tokens zijn van Azure RMS gedownload en geïnstalleerd op de lokale computer in het register. Ze worden beschermd met behulp van de data protection application programming interface (DPAPI) en de referenties van de account lokaal systeem.

Voer de volgende stappen uit op de laatste pagina van de wizard en klik vervolgens op **Voltooien**:

-   Als dit de eerste connector die u hebt geïnstalleerd, niet de optie **starten connector beheerdersconsole servers te machtigen** op dit moment. Nadat u uw tweede (of definitieve) RMS-connector hebt geïnstalleerd, wordt u deze optie selecteert. In plaats daarvan de wizard opnieuw uitvoeren op ten minste één andere computer. U moet ten minste twee connectors installeren.

-   Als u de tweede (of definitieve)-connector hebt geïnstalleerd, selecteert u **starten connector beheerdersconsole servers te machtigen**.

> [!TIP]
> Er is op dit moment een verificatiestest die u uitvoeren kunt om te controleren of de webservices voor de RMS-connector operationeel zijn:
> 
> -   Verbinding maken met een webbrowser **http://&lt;connectoraddress&gt;/_wmcs/certification/servercertification.asmx**, vervangt *&lt; connectoraddress &gt;* met het adres van de server of de naam met de RMS-connector geïnstalleerd. Een geslaagde verbinding bevat een **ServerCertificationWebService** pagina.

Als u de RMS-connector verwijderen, voert u de wizard opnieuw uit en selecteer de optie verwijderen.

## <a name="AuthorizingServers"></a>Autorisatie servers gebruik van de RMS-connector
Wanneer u de RMS-connector op ten minste twee computers hebt geïnstalleerd, bent u klaar om te machtigen servers en services die u wilt gebruiken de RMS-connector. Bijvoorbeeld, servers met Exchange Server 2013 of SharePoint Server 2013.

Als u deze servers definieert, voer het beheerprogramma voor RMS-connector en vermeldingen toevoegen aan de lijst met toegestane servers. U kunt dit hulpprogramma uitvoeren wanneer u selecteert **Start connector-beheerconsole servers te machtigen** aan het einde van de Microsoft Rights Management-connector Setup wizard of u kunt uitvoeren afzonderlijk in de wizard.

Als u deze servers machtigen, rekening met de volgende overwegingen:

-   Servers die u toevoegt, speciale bevoegdheden krijgen. Alle accounts die u opgeeft voor de Exchange Server-rol in de configuratie van de connector krijgt de [super gebruikersrol](https://technet.microsoft.com/library/mt147272.aspx) in Azure RMS, waardoor ze toegang tot alle inhoud voor deze tenant RMS. De functie supergebruiker wordt automatisch op dit moment ingeschakeld indien nodig. Zorg dat u alleen de accounts die worden gebruikt door uw organisatie Exchange-servers opgeven om te voorkomen dat het beveiligingsrisico van misbruik van bevoegdheden. Alle servers die zijn geconfigureerd als SharePoint-servers of bestandsservers met FCI krijgt de met normale gebruikersbevoegdheden.

-   U kunt meerdere servers als één vermelding toevoegen door te geven van een Active Directory-beveiliging of distributiegroep of een serviceaccount die wordt gebruikt door meer dan één server. Wanneer u deze configuratie gebruikt, de groep servers delen dezelfde RMS-certificaten en alle komen in aanmerking voor de inhoud die deze zijn beveiligd. U wordt aangeraden deze configuratie van een groep in plaats van afzonderlijke servers te machtigen van uw organisatie Exchange-servers of een SharePoint-server-farm gebruiken om te beperken administratieve overhead.

Op de **Servers kunnen gebruikmaken van de connector** pagina, klikt u op **toevoegen**.

### <a name="BKMK_AddServer"></a>Een server toevoegen aan de lijst met toegestane servers
Op de **dat een server kan gebruikmaken van de connector** pagina, geef de naam van het object of bladeren om u te identificeren van het object toe te staan.

Het is belangrijk dat u de juiste object machtigen. Voor een server naar de connector gebruiken, moet het account dat de lokale service (bijvoorbeeld Exchange of SharePoint) wordt uitgevoerd voor autorisatie worden geselecteerd. Bijvoorbeeld als de service wordt uitgevoerd als een geconfigureerde serviceaccount, de naam van toevoegen die serviceaccount aan de lijst. Als de service wordt uitgevoerd als lokaal systeem, moet u de naam van het computerobject (bijvoorbeeld servernaam$) toevoegen. Aanbevolen om een groep met deze accounts maken en geef de groep in plaats van namen van de afzonderlijke servers.

Meer informatie over de verschillende serverfuncties:

-   Voor servers met Exchange: U moet een beveiligingsgroep opgeven en kunt u de standaard-groep (**Exchange-Servers**) die Exchange automatisch gemaakt en onderhouden van alle Exchange-servers in de forest.

-   Voor servers waarop SharePoint worden uitgevoerd:

    -   Als een SharePoint 2010-server is geconfigureerd om te worden uitgevoerd als lokaal systeem (deze geen gebruik maakt van een serviceaccount), maak handmatig een beveiligingsgroep in Active Directory Domain Services en het computerobject naam voor de server in de configuratie aan deze groep toevoegen.

    -   Als een SharePoint-server is geconfigureerd voor een serviceaccount (de aanbevolen voor SharePoint 2010) en de optie alleen gebruiken voor SharePoint 2013, het volgende doen:

        1.  Voeg de serviceaccount die de service Centraal beheer van SharePoint om in te schakelen SharePoint worden geconfigureerd vanuit de administrator-console wordt uitgevoerd.

        2.  Het account dat is geconfigureerd voor de SharePoint-App Pool toevoegen.

        > [!TIP]
        > Als deze twee accounts verschillende zijn, moet u het maken van een groep die beide accounts om te minimaliseren administratieve overhead bevat.

-   Voor bestandsservers met bestand classificatie infrastructuur, de bijbehorende services uitgevoerd als het account lokaal systeem zodat u moet het computeraccount voor de bestandsservers (bijvoorbeeld servernaam$) of een groep met de computeraccounts van deze toestaan.

Als u klaar bent met het toevoegen van servers aan de lijst, klikt u op **Sluiten**.

Als u nog niet hebt gedaan, moet u nu configureren taakverdeling voor de servers waarvoor de RMS-connector geïnstalleerd en overweeg om te gebruiken HTTPS voor de verbindingen tussen deze servers en de servers die u net hebt gemachtigd.

## <a name="ConfiguringConnector"></a>Configureren van load balancing en hoge beschikbaarheid
Nadat u het tweede of definitieve exemplaar van de RMS-connector hebt geïnstalleerd, een connector-URL-servernaam definiëren en configureren van een systeem voor de taakverdeling.

De naam van de connector URL-server kan elke willekeurige naam onder een naamruimte die u bepalen zijn. U kunt bijvoorbeeld een vermelding maken in uw systeem voor de DNS- **rmsconnector.contoso.com** en configureer deze vermelding voor een IP-adres gebruiken in uw systeem voor de taakverdeling. Er zijn geen speciale vereisten voor deze naam en het niet hoeft te worden geconfigureerd op de connector servers zelf. Tenzij de Exchange- en SharePoint servers communiceren met de connector via het Internet gaat, deze naam hoeft niet omzetten op Internet.

> [!IMPORTANT]
> Het is raadzaam dat u deze naam niet wijzigen nadat u Exchange of SharePoint-servers voor gebruik van de connector hebt geconfigureerd omdat u schakelt u deze servers van alle IRM configuraties en configureer deze vervolgens opnieuw.

Nadat de naam in DNS is gemaakt en is geconfigureerd voor een IP-adres, configureren load balancing voor dit adres die ervoor zorgt het verkeer naar de connector-servers dat. U kunt elke IP-adres op basis van een load balancer voor dit doel, waaronder de functie Network Load Balancing (NLB) in Windows Server. Zie voor meer informatie [Load Balancing Deployment Guide](http://technet.microsoft.com/library/cc754833%28v=WS.10%29.aspx).

Gebruik de volgende instellingen configureren van de NLB-cluster:

-   Poorten: 80 (voor HTTP) of 443 (voor HTTPS)

    Zie de volgende sectie voor meer informatie over de vraag of HTTP-of HTTPS.

-   Affiniteit: Geen

-   Distributiemethode: Gelijk aan

Deze naam die u definieert voor het systeem taakverdeling (voor de servers waarop de RMS-connector-service) is de naam van uw organisatie RMS-connector die u later gebruiken wilt wanneer u de lokale-servers gebruik van Azure RMS configureren.

## <a name="BKMK_ConfiguringHTTPS"></a>De RMS-connector voor gebruik van HTTPS configureren
> [!NOTE]
> Deze configuratiestap is optioneel maar aanbevolen voor aanvullende beveiligingsinstellingen.

Hoewel het gebruik van TLS of SSL optioneel voor de RMS-connector is, wordt aangeraden deze voor elke service vertrouwelijke op basis van HTTP. Deze configuratie wordt geverifieerd door de servers waarop de connector aan de Exchange- en SharePoint-servers die gebruikmaken van de connector wordt uitgevoerd. Bovendien alle gegevens die door deze servers wordt verzonden naar de connector is versleuteld.

Als u de RMS-connector voor gebruik met TLS, op elke server waarop de connector RMS installeert een certificaat voor verificatie met de naam die u voor de connector gebruiken wilt. Als uw RMS-connector die u hebt gedefinieerd de naam DNS is bijvoorbeeld **rmsconnector.contoso.com**, implementeren van een certificaat voor verificatie met **rmsconnector.contoso.com** in de onderwerpregel certificaat als de algemene naam. Of geef **rmsconnector.contoso.com** in de alternatieve naam als de DNS-waarde van het certificaat. Het certificaat heeft niet de naam van de server op te nemen. Klik in IIS, de dit certificaat binden aan de standaardwebsite.

Als u de optie HTTPS, zorg dat alle servers die worden uitgevoerd van de connector een geldige server-verificatie certificaat dat is gekoppeld aan een basis-CA of de vertrouwensrelatie van de Exchange- en SharePoint-servers. Bovendien als de certificeringsinstantie (CA) die de certificaten voor de servers connector publiceert een lijst met certificaatintrekkingen (CRL), moet de Exchange- en SharePoint-Server kunnen deze CRL kan worden gedownload.

> [!TIP]
> U kunt de volgende informatie en bronnen gebruiken om te vragen en een certificaat voor verificatie installeren en dit certificaat binden aan de standaardwebsite in IIS:
> 
> -   Als u deze server-verificatiecertificaten implementeren met Active Directory Certificate Services (AD CS) en een enterprise-certificeringsinstantie (CA), kunt u dubbele en gebruik vervolgens de certificaatsjabloon webserver. Dit certificaatsjabloon gebruikt **opgegeven in de aanvraag** voor de naam van de certificaathouder, dus u kunt de FQDN-naam van de naam van de RMS-connector voor de naam van de certificaathouder of alternatieve onderwerpnaam opgeven wanneer u het certificaat aanvragen.
> -   Als u een zelfstandige Certificeringsinstantie of aankoop van dit certificaat van een ander bedrijf, Zie [Internet servercertificaten configureren (IIS 7)](http://technet.microsoft.com/library/cc731977%28v=ws.10%29.aspx) in de [webserver (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) Documentatiebibliotheek op TechNet.
> -   Zie het configureren van IIS om het certificaat te gebruiken [een Binding toevoegen aan een Site (IIS 7)](http://technet.microsoft.com/library/cc731692.aspx) in de in de [webserver (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) Documentatiebibliotheek op TechNet.

## <a name="BKMK_ConfiguringWebProxy"></a>De RMS-connector voor een webserver proxy configureren
Als de connector-servers in een netwerk dat geen directe verbinding met Internet en handmatige configuratie van een web proxy-server voor uitgaande internettoegang vereist zijn geïnstalleerd, moet u het register op deze servers voor de RMS-connector configureren.

#### De RMS-connector voor gebruik van een web proxy-server configureren

1.  Open op elke server waarop de RMS-connector wordt uitgevoerd, een register-editor, zoals Regedit.

2.  Ga naar **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AADRM\Connector**

3.  Voeg de tekenreekswaarde van **ProxyAddress** en stelt u de gegevens voor deze waarde moet **http://&lt;MyProxyDomainOrIPaddress&gt;:&lt;MyProxyPort&gt;**

    Bijvoorbeeld: **http://proxyserver.contoso.com:8080**

4.  Sluit de Register-editor en start de server of een opdracht IISReset IIS opnieuw uitvoeren.

## <a name="BKMK_InstallingStandaloneTool"></a>Het beheerprogramma voor RMS-connector installeren op administratieve computers
U kunt het beheerprogramma voor RMS-connector uitvoeren op een computer waarop geen de RMS-connector is geïnstalleerd, als deze computer voldoet aan de volgende:

-   Een fysieke of virtuele computer met Windows Server 2012 of Windows Server 2012 R2 (alle edities), Windows Server 2008 R2 of Windows Server 2008 R2 Service Pack 1 (alle edities), Windows 8.1, Windows 8 of Windows 7.

-   Ten minste 1 GB RAM.

-   Een minimum van 64 GB schijfruimte.

-   Ten minste één netwerkinterface.

-   Toegang tot het Internet via een firewall (of webproxy).

Om het beheerprogramma voor RMS-connector hebt geïnstalleerd, voert u de volgende bestanden:

-   Voor een 32-bits-computer: RMSConnectorAdminToolSetup_x86.exe

-   Voor een 64-bits-computer: RMSConnectorSetup.exe

Als u al deze bestanden nog niet hebt gedownload, kunt u dit doen in de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106).

## <a name="ConfiguringServers"></a>Servers gebruik van de connector RMS configureren
Nadat u hebt geïnstalleerd en de RMS-connector geconfigureerd, bent u klaar om uw lokale servers die Rights Management gebruiken en via de connector verbinding maken met Azure RMS te configureren. Dit betekent dat de volgende servers configureren:

-   Voor Exchange 2013: Client-servers en Postvak servers

-   Voor Exchange 2010: Client-servers en hub transport-servers

-   Voor SharePoint: Front-end SharePoint webservers, met inbegrip van die als host fungeert voor de Centraal beheerserver

-   Voor bestand classificatie infrastructuur: Windows Server-computers waarop bestand Resource Manager is geïnstalleerd

Deze configuratie vereist registerinstellingen. Hiervoor hebt u twee opties:

|Configuratieoptie|Voordelen|Nadelen|
|---------------------|-------------|-----------|
|Automatisch met behulp van de server configuration tool voor Microsoft RMS-connector|Er is geen directe bewerken van het register. Dit wordt automatisch voor u met behulp van een script.<br /><br />Uitvoeren van een Windows PowerShell-cmdlet om te achterhalen van uw Microsoft RMS-URL is niet nodig.<br /><br />De vereiste onderdelen worden automatisch voor u dit selectievakje is ingeschakeld (maar niet automatisch opgelost) als u lokaal uitvoeren.|Wanneer u het programma uitvoert, moet u een verbinding met een server waarop al de RMS-connector wordt uitgevoerd.|
|Handmatig door het register bewerken|Er is geen verbinding met een server met de RMS-connector is vereist.|Meer administratieve overhead die fout gevoelig zijn.<br /><br />U moet uw Microsoft RMS-URL, waarvoor u een Windows PowerShell-opdracht wordt uitgevoerd.<br /><br />U moet altijd zelf alle vereisten controles maken.|
> [!IMPORTANT]
> In beide gevallen moet u handmatig alle vereiste software installeren en configureren van Exchange, SharePoint en bestand classificatie infrastructuur voor het gebruik van Rights Management.

Voor de meeste organisaties worden automatische configuratie met behulp van de server configuration tool voor Microsoft RMS-connector van de betere optie, omdat hiermee de grotere efficiëntie en betrouwbaarheid dan handmatig configureren.

Nadat u de wijzigingen in de configuratie op deze servers, moeten opnieuw als ze met Exchange of SharePoint en eerder geconfigureerd voor gebruik van AD RMS. Er is geen opnieuw moet worden deze servers als u deze voor Rights Management voor de eerste keer configureert. U moet altijd de bestandsserver die is geconfigureerd voor het bestand classificatie infrastructuur gebruiken nadat u deze wijzigingen in de configuratie opnieuw.

#### Het gebruik van de server configuration tool voor Microsoft RMS-connector

1.  Als u al het script voor de server configuration tool voor Microsoft RMS-connector (GenConnectorConfig.ps1) nog niet hebt gedownload, downloaden vanaf de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106).

2.  Sla het bestand GenConnectorConfig.ps1 op de computer waarop u het programma wordt uitgevoerd. Als u het hulpprogramma lokaal wordt uitgevoerd, moet de server die u wilt configureren om te communiceren met de RMS-connector. U kunt deze anders opslaan op elke computer.

3.  Opgeven hoe u het hulpprogramma uitvoeren:

    -   **Lokaal**: U kunt het hulpprogramma interactief uitvoeren van de server worden geconfigureerd om te communiceren met de RMS-connector. Dit is handig voor een eenmalige configuratie, zoals een testomgeving.

    -   **Software-implementatie**: U kunt het hulpprogramma Register-bestanden die u vervolgens op een of meer relevante servers implementeren met behulp van een toepassing voor systemen die software-implementatie, zoals System Center Configuration Manager ondersteunt produceren uitvoeren.

    -   **Groepsbeleid**: U kunt het hulpprogramma te maken van een script dat u een beheerder die Groepsbeleid objecten voor de servers die moeten worden geconfigureerd, kan maken geven uitvoeren. Dit script maakt een Group Policy object voor elk servertype te configureren, die de beheerder aan de relevante servers toewijzen kunt.

    > [!NOTE]
    > Dit hulpprogramma configureert u de servers die communiceert met de RMS-connector en die aan het begin van deze sectie worden weergegeven. Dit hulpprogramma niet uitgevoerd op de servers waarop de RMS-connector wordt uitgevoerd.

4.  Start van Windows PowerShell met de **uitvoeren als beheerder** de optie en gebruikt u de opdracht Get-help instructies lezen hoe u het gebruik van het hulpprogramma voor de methode gekozen configuratie:

    ```
    Get-help .\GenConnectorConfig.ps1 -detailed
    ```

Wanneer het programma wordt uitgevoerd, vraagt u de URL van de RMS-connector voor uw organisatie opgeven. Voer het voorvoegsel protocol (HTTP:// of HTTPS://) en de naam van de connector die u hebt gedefinieerd in de DNS voor de taakverdeling-adres van de connector. Bijvoorbeeld, https://connector.contoso.com. Het hulpprogramma vervolgens die URL maakt verbinding met de servers waarop de RMS-connector wordt uitgevoerd en andere parameters die worden gebruikt voor het maken van de vereiste configuraties verkrijgen.

> [!IMPORTANT]
> Als u dit programma uitvoert, moet u de naam van de connector RMS taakverdeling opgeven voor uw organisatie en niet de naam van één server waarop de RMS-connector-service wordt uitgevoerd.

Gebruik de volgende secties voor specifieke informatie voor elk servicetype:

-   [Configuring an Exchange server to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ExchangeServer)

-   [Configuring a SharePoint server to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringSharePoint)

-   [Configuring a file server for File Classification Infrastructure to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_FileServer)

> [!NOTE]
> Nadat deze servers zijn geconfigureerd voor gebruik van de connector, kan het zijn dat clienttoepassingen die lokaal zijn geïnstalleerd op deze servers niet werken met RMS. Wanneer dit gebeurt, is dit omdat de toepassingen probeert te gebruiken van de connector dan RMS rechtstreeks, wat niet wordt ondersteund gebruiken.
> 
> Bovendien als Office 2010 lokaal op een Exchange-server is geïnstalleerd, IRM-functies van de client-app werkt mogelijk van die computer nadat de server is geconfigureerd voor gebruik van de connector, maar dit wordt niet ondersteund.
> 
> In beide gevallen moet u de clienttoepassingen installeren op afzonderlijke computers die niet zijn geconfigureerd voor gebruik van de connector. Deze wordt vervolgens correct RMS rechtstreeks gebruiken.

### <a name="BKMK_ExchangeServer"></a>Configureren van een Exchange-server voor gebruik van de connector
De volgende Exchange-rollen communiceren met de RMS-connector:

-   Voor Exchange 2013: Client- en postvakserver

-   Voor Exchange 2010: Client- en hub Transportserver

Als u wilt de RMS-connector gebruiken, moeten u deze servers met Exchange uitgevoerd een van de volgende versies van software:

-   Exchange Server 2013 met Exchange 2013 cumulatieve Update 3

-   Exchange Server 2010 met Exchange 2010 Service Pack 3 Rollup Update 6

U moet ook installeren op deze servers, een versie van de RMS-client die ondersteuning biedt voor RMS cryptografische modus 2. De minimale versie die wordt ondersteund in Windows Server 2008 is opgenomen in de hotfix die u van downloaden kunt [lengte van de RSA-sleutel wordt verhoogd tot 2048 bits voor AD RMS in Windows Server 2008 R2 en in Windows Server 2008](http://support.microsoft.com/kb/2627272). De minimale versie voor Windows Server 2008 R2 kan worden gedownload van [lengte van de RSA-sleutel wordt verhoogd tot 2048 bits voor AD RMS in Windows 7 of Windows Server 2008 R2](http://support.microsoft.com/kb/2627273). Windows Server 2012 en Windows Server 2012 R2 ondersteuning native voor cryptografische modus 2.

> [!IMPORTANT]
> Als deze versies of nieuwere versies van Exchange en de RMS-client niet worden geïnstalleerd, wordt het niet mogelijk Exchange connector gebruiken voor het configureren. Controleer of deze versies zijn geïnstalleerd voordat u doorgaat.

##### Exchange-servers voor gebruik van de connector configureren

1.  Voer op de Exchange server-functies die met de RMS-connector communiceren, een van de volgende:

    -   De server configuration tool voor Microsoft RMS-connector uitvoeren. Zie voor meer informatie [How to use the server configuration tool for Microsoft RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_HowToRunTheTool) in dit onderwerp.

    -   Handmatige register wijzigingen aanbrengen met behulp van de tabellen in de volgende secties handmatig toe te voegen registerinstellingen op de servers.

2.  De functie IRM Exchange inschakelen. Zie voor meer informatie [Information Rights Management Procedures](https://technet.microsoft.com/library/dd351212%28v=exchg.150%29.aspx) in de Exchange-bibliotheek.

De tabellen in de volgende secties alleen gebruiken als u handmatig wilt toevoegen of Controleer registerinstellingen op deze servers de servers gebruik van de RMS-connector te configureren. Instructies voor het wanneer u deze tabellen gebruiken:

-   *MicrosoftRMSURL* van uw organisatie Microsoft RMS-service-URL is. Deze waarde zoeken:

    1.  Voer de [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) cmdlet voor Azure RMS. Als u hebt al de Windows PowerShell-module voor Azure RMS geïnstalleerd, Zie [Installatie van Windows PowerShell voor Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

    2.  Uit de uitvoer identificeren de **LicensingIntranetDistributionPointUrl** waarde.

        Bijvoorbeeld: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  Verwijderen van de waarde **_wmcs/licensing** van deze tekenreeks. De resterende tekenreeks is de URL van uw Microsoft RMS. De URL van Microsoft RMS zouden in ons voorbeeld de volgende waarde:

        **https://5c6bb73b-1038-4eec-863d-49bded473437.RMS.na.aadrm.com**

-   *ConnectorFQDN* is de load balancing-naam die u in DNS voor de connector gedefinieerd. Bijvoorbeeld, **rmsconnector.contoso.com**.

-   De HTTPS-voorvoegsel voor de URL van de connector te gebruiken als u de connector voor gebruik van HTTPS om te communiceren met uw lokale servers hebt geconfigureerd. Zie voor meer informatie de [Configuring the RMS connector to use HTTPS](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringHTTPS) in dit onderwerp. De URL's van Microsoft RMS altijd gebruiken HTTPS.

#### Tabel voor Exchange 2013 registerinstellingen

|Register-pad|Type|Waarde|Gegevens|
|----------------|--------|----------|------------|
|HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation|Reg_SZ|Standaardwaarde|https://*_wmcs-MicrosoftRMSURL-certificering*|
|HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing|Reg_SZ|Standaardwaarde|https://MicrosoftRMSURL/_wmcs/licensing|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\CertificationServerRedirection|Reg_SZ|https://*MicrosoftRMSURL*|Een van de volgende, afhankelijk van of u via HTTP- of HTTPS van de Exchange-server de RMS-connector:<br /><br />-   http://*ConnectorFQDN*<br />-   https://*ConnectorFQDN*|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://*MicrosoftRMSURL*|Een van de volgende, afhankelijk van of u via HTTP- of HTTPS van de Exchange-server de RMS-connector:<br /><br />-   http://*ConnectorFQDN*<br />-   https://*ConnectorFQDN*|

#### Tabel voor Exchange 2010 registerinstellingen

|Register-pad|Type|Waarde|Gegevens|
|----------------|--------|----------|------------|
|HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation|Reg_SZ|Standaardwaarde|https://*MicrosoftRMSURL*_wmcs/certification|
|HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing|Reg_SZ|Standaardwaarde|https://*MicrosoftRMSURL*_wmcs/Licensing|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\CertificationServerRedirection|Reg_SZ|https://*MicrosoftRMSURL*|Een van de volgende, afhankelijk van of u via HTTP- of HTTPS van de Exchange-server de RMS-connector:<br /><br />-   http://*ConnectorFQDN*<br />-   https://*ConnectorFQDN*|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://*MicrosoftRMSURL*|Een van de volgende, afhankelijk van of u via HTTP- of HTTPS van de Exchange-server de RMS-connector:<br /><br />-   http://*ConnectorFQDN*<br />-   https://*ConnectorFQDN*|

### <a name="BKMK_ConfiguringSharePoint"></a>Een SharePoint-server voor het gebruik van de connector configureren
De volgende SharePoint-rollen communiceren met de RMS-connector:

-   Front-end SharePoint webservers, met inbegrip van die als host fungeert voor de Centraal beheerserver

Als u wilt de RMS-connector gebruiken, moeten u deze servers met SharePoint uitgevoerd een van de volgende versies van software:

-   SharePoint Server 2013

-   SharePoint Server 2010

Een SharePoint 2013-server moet ook een versie van de client MSIPC 2.1 die from1.0.622.34 via 1.0.10907.0 wordt uitgevoerd.

> [!WARNING]
> Er zijn meerdere versies van de MSIPC 2.1-client, dus zorg ervoor dat een versie waarnaar wordt verwezen in dit artikel te installeren.
> 
> U kunt de clientversie controleren met het versienummer van MSIPC.dll, dat zich bevindt in **\Program Files\Active Directory Rights Management Services Client 2.1**. Het eigenschappendialoogvenster bevat het versienummer van de MSIPC 2.1-client.

Deze servers SharePoint 2010 uitvoeren, moeten een versie van de client MSDRM die ondersteuning biedt voor RMS cryptografische modus 2 hebt geïnstalleerd. De minimale versie die wordt ondersteund in Windows Server 2008 is opgenomen in de hotfix die u van downloaden kunt [lengte van de RSA-sleutel wordt verhoogd tot 2048 bits voor AD RMS in Windows Server 2008 R2 en in Windows Server 2008](http://support.microsoft.com/kb/2627272), en de minimale versie voor Windows Server 2008 R2 kan worden gedownload van [lengte van de RSA-sleutel wordt verhoogd tot 2048 bits voor AD RMS in Windows 7 of Windows Server 2008 R2](http://support.microsoft.com/kb/2627273). Windows Server 2012 en Windows Server 2012 R2 ondersteuning native voor cryptografische modus 2.

##### SharePoint-servers voor gebruik van de connector configureren

1.  Voer een van de volgende op de SharePoint-servers die met de RMS-connector communiceren:

    -   De server configuration tool voor Microsoft RMS-connector uitvoeren. Zie voor meer informatie [How to use the server configuration tool for Microsoft RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_HowToRunTheTool) in dit onderwerp.

    -   Als u SharePoint 2013 gebruikt, moet u wijzigingen in het register handmatig met behulp van de tabel in de volgende sectie handmatig toe te voegen registerinstellingen op de servers.

2.  Schakel IRM in SharePoint. Zie voor meer informatie [configureren Information Rights Management (SharePoint Server 2010)](https://technet.microsoft.com/library/hh545607%28v=office.14%29.aspx) in de SharePoint-documentbibliotheek.

    Als u deze instructies volgen, moet u SharePoint voor gebruik van de connector door te geven **Deze RMS-server**, en voer vervolgens de load balancing-connector URL die u hebt geconfigureerd. Voer het voorvoegsel protocol (HTTP:// of HTTPS://) en de naam van de connector die u hebt gedefinieerd in de DNS voor de taakverdeling-adres van de connector. Bijvoorbeeld als uw connectornaam https://connector.contoso.com, bekijken uw configuratie in de volgende afbeelding:

    ![](../Image/AzRMS_SharePointConnector.png)

    Nadat u IRM op een SharePoint-farm is ingeschakeld, kunt u IRM op afzonderlijke bibliotheken inschakelen met behulp van de **Information Rights Management** optie op de **Bibliotheekinstellingen** pagina voor elk van de bibliotheken.

    > [!IMPORTANT]
    > Voor SharePoint voor toegang tot RMS met behulp van de connector, moet u de bijbehorende accounts in het beheerprogramma voor RMS-connector machtigen. Als u nog niet hebt gedaan, raadpleegt u [Authorizing servers to use the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#AuthorizingServers) in dit onderwerp.

De tabel in de volgende sectie alleen gebruiken als u handmatig wilt toevoegen of Controleer registerinstellingen op een server met SharePoint 2013.

#### Tabel voor SharePoint 2013 registerinstellingen
Instructies voor het wanneer u deze tabel gebruiken:

-   *MicrosoftRMSURL* van uw organisatie Microsoft RMS-service-URL is. Deze waarde zoeken:

    1.  Voer de [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) cmdlet voor Azure RMS. Als u hebt al de Windows PowerShell-module voor Azure RMS geïnstalleerd, Zie [Installatie van Windows PowerShell voor Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

    2.  Uit de uitvoer identificeren de **LicensingIntranetDistributionPointUrl** waarde.

        Bijvoorbeeld: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  Verwijderen van de waarde **_wmcs/licensing** van deze tekenreeks. De resterende tekenreeks is de URL van uw Microsoft RMS. De URL van Microsoft RMS zouden in ons voorbeeld de volgende waarde:

        **https://5c6bb73b-1038-4eec-863d-49bded473437.RMS.na.aadrm.com**

-   *ConnectorFQDN* is de load balancing-naam die u in DNS voor de connector gedefinieerd. Bijvoorbeeld, **rmsconnector.contoso.com**.

-   De HTTPS-voorvoegsel voor de URL van de connector te gebruiken als u de connector voor gebruik van HTTPS om te communiceren met uw lokale servers hebt geconfigureerd. Zie voor meer informatie de [Configuring the RMS connector to use HTTPS](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringHTTPS) in dit onderwerp. De URL's van Microsoft RMS altijd gebruiken HTTPS.

|Register-pad|Type|Waarde|Gegevens|
|----------------|--------|----------|------------|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\LicensingRedirection|Reg_SZ|https://*MicrosoftRMSURL*_wmcs/licensing|Een van de volgende, afhankelijk van of u via HTTP- of HTTPS van uw SharePoint-server de RMS-connector:<br /><br />-   http://*ConnectorFQDN*_wmcs/licensing<br />-   https://*ConnectorFQDN*_wmcs/licensing|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification|Reg_SZ|Standaardwaarde|Een van de volgende, afhankelijk van of u via HTTP- of HTTPS van uw SharePoint-server de RMS-connector:<br /><br />-   http://*ConnectorFQDN*_wmcs/certification<br />-   https://*ConnectorFQDN*_wmcs/certification|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing|Reg_SZ|Standaardwaarde|Een van de volgende, afhankelijk van of u via HTTP- of HTTPS van uw SharePoint-server de RMS-connector:<br /><br />-   http://*ConnectorFQDN*_wmcs/licensing<br />-   https://*ConnectorFQDN*_wmcs/licensing|

### <a name="BKMK_FileServer"></a>Een bestandsserver voor bestand classificatie infrastructuur gebruik van de connector configureren
Als u de RMS-connector en bestand classificatie infrastructuur Office-documenten beveiligen, moet u de bestandsserver uitgevoerd een van de volgende besturingssystemen:

-   Windows Server 2012 R2

-   Windows Server 2012

##### Bestandsservers voor gebruik van de connector configureren

1.  Voer een van de volgende opties op het bestand servers die zijn geconfigureerd voor het bestand classificatie infrastructuur en die met de RMS-connector communiceert:

    -   De server configuration tool voor Microsoft RMS-connector uitvoeren. Zie voor meer informatie [How to use the server configuration tool for Microsoft RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_HowToRunTheTool) in dit onderwerp.

    -   Handmatige register wijzigingen aanbrengen op basis van de tabel in de volgende sectie handmatig toe te voegen registerinstellingen op de servers.

2.  Classificatieregels en bestandsbeheertaken beveiligen van documenten met RMS-versleuteling maken en geef vervolgens een sjabloon RMS automatisch RMS beleid toepassen. Zie voor meer informatie [Bestandsserverbronbeheer overzicht](http://technet.microsoft.com/library/hh831701.aspx) in de bibliotheek voor Windows Server-documentatie.

De tabel in de volgende sectie alleen gebruiken als u handmatig wilt toevoegen of Controleer registerinstellingen op een server die gebruikmaakt van de infrastructuur van de classificatie bestand beveiligen van documenten.

#### Tabel voor bestandsserver en registerinstellingen bestand classificatie infrastructuur
Instructies voor het wanneer u deze tabel gebruiken:

-   *ConnectorFQDN* is de load balancing-naam die u in DNS voor de connector gedefinieerd. Bijvoorbeeld, **rmsconnector.contoso.com**.

-   De HTTPS-voorvoegsel voor de URL van de connector te gebruiken als u de connector voor gebruik van HTTPS om te communiceren met uw lokale servers hebt geconfigureerd. Zie voor meer informatie de [Configuring the RMS connector to use HTTPS](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringHTTPS) in dit onderwerp. De URL's van Microsoft RMS altijd gebruiken HTTPS.

|Register-pad|Type|Waarde|Gegevens|
|----------------|--------|----------|------------|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing|Reg_SZ|Standaardwaarde|http://*ConnectorFQDN*_wmcs/licensing|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation|Reg_SZ|Standaardwaarde|http://*ConnectorFQDN*_wmcs/certification|

## <a name="BKMK_NextSteps"></a>Volgende stappen
De RMS-connector is geïnstalleerd en geconfigureerd en uw servers zijn geconfigureerd voor het gebruik, kunnen IT-beheerders en gebruikers worden beveiligd en e-mailbericht en documenten met behulp van Azure RMS in beslag neemt. Om dit toegankelijk maken voor gebruikers, de implementatie van de RMS sharing toepassing die een invoegtoepassing voor Office installeert en nieuwe met de rechtermuisknop opties worden toegevoegd aan bestand Explorer. Zie voor meer informatie de [delen toepassing Rights Management-beheerdershandleiding](http://technet.microsoft.com/library/%20dn339003%28v=ws.10%29.aspx).

Bovendien kunt u overwegen het volgende kunt u de RMS-connector en gebruik van uw organisatie van RMS bewaken:

-   Het ingebouwde **Microsoft Rights Management-connector** prestatiemeteritems

-   [Logboekregistratie en analyseren van Azure Rights Management-gebruik](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md)

U kunt de [Azure Rights Management-implementatieschema](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) om te controleren of er andere configuratiestappen die u kunt doen zijn voor de implementatie [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] gebruikers en beheerders. Als er geen andere configuratiestappen die u nodig hebt om te doen, Zie [Met behulp van Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) voor operationele richtlijnen ter ondersteuning van op een succesvolle implementatie voor uw organisatie.

## Zie ook
[Azure Rights Management configureren](../Topic/Configuring_Azure_Rights_Management.md)

