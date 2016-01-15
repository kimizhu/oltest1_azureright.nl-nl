---
description: na
keywords: na
title: RMS for Individuals and Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2efcb440-fefd-45e9-872b-f471573aadf2
---
# RMS voor personen en Azure Rights Management
RMS voor personen is een gratis abonnement Self-service voor gebruikers in een organisatie die gevoelige bestanden die zijn beveiligd door Microsoft Azure Rights Management (Azure RMS) zijn verzonden, maar kan niet worden geverifieerd omdat hun IT-afdeling niet wordt beheerd een account voor hen in Azure. Bijvoorbeeld, niet de IT-afdeling Office 365 hebben of Azure-services gebruiken.

Deze gebruikers kunnen aanmelden voor een gratis werk of opleiding account te gebruiken met Azure RMS en download en installeer de Rights Management-toepassing delen. Deze gebruikers kunnen als gevolg hiervan nu verifiëren om te laten zien dat zij de persoon die de beveiligde bestanden zijn verzonden naar en u de beveiligde bestanden op computers of mobiele apparaten leest zijn.

Met de Rights Management-toepassing op Windows-computers delen, deze gebruikers zouden kunnen ook bestanden in plaats beveiligen of beveiligde bestanden per e-mail verzenden naar personen binnen of buiten de organisatie. Als de ontvangers van het e-mailbericht dat ze verzenden in een organisatie die ook niet van gebruikersaccounts in Azure beheren, kunnen ze te aanmelden voor een RMS voor personen account lezen van de beveiligde e-mailbijlage.

> [!IMPORTANT]
> Met deze gratis abonnement zorgt ervoor dat geautoriseerde altijd leesbare bestanden die zijn beveiligd. Op dit moment ook kunt u dit gratis abonnement voor het beveiligen van documenten en nieuwe beveiligde e-mailberichten maken, maar de mogelijkheid om nieuwe beveiligde inhoud is bedoeld voor alleen proef gebruik en in de toekomst kan worden verwijderd. Zie voor meer informatie en eventuele wijzigingen voor het gebruik van RMS voor personen om inhoud te beschermen, de [Microsoft Rights Management servicevoorwaarden](https://portal.aadrm.com/Legal/Service).

Zie voor meer informatie over hoe u bestanden beveiligen kunt met behulp van de beschikbare Rights Management-toepassing delen, de [Rights Management delen handleiding voor gebruikers](http://technet.microsoft.com/library/dn339006.aspx).

RMS voor personen is een voorbeeld van een self-service aanmelding die wordt ondersteund door de Azure Active Directory. Zie voor meer informatie over hoe dit werkt, [Wat Self-Service aanmelding voor Azure is?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/) in de documentatie van Microsoft Azure. Gebruik de volgende secties voor meer informatie die specifiek is voor RMS voor personen:

-   [Hoe gebruikers aanmelden voor RMS voor personen](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_SignUp)

    -   [Technisch overzicht](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TechnicalOverview)

-   [Hoe kunnen beheerders de accounts voor RMS gemaakt voor personen](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TakeControlofAccounts)

-   [Als uw gebruikers hebt aangemeld voor RMS voor personen bepalen](#BKMK_Detect)

## <a name="BKMK_SignUp"></a>Hoe gebruikers aanmelden voor RMS voor personen
Als u wilt aanmelden voor deze gratis account, u vragen door naar de pagina de [pagina Microsoft Rights Management](https://portal.aadrm.com/), en om uw werk of opleiding e-mailadres. De meest voorkomende manier dat u zult worden doorgestuurd naar deze pagina is als u een e-mailbericht met een beveiligde bijlage die instructies hoe bevat ontvangen voor registratie. U ontvangt een e-mailbericht in antwoord van Microsoft en kunt Voltooi het registratieproces door te voeren informatie om uw account te maken. Wanneer u een e-mail ter bevestiging van Microsoft krijgen, ontvangt dit laatste e-mailbericht u op een pagina waar u de toepassing delen voor verschillende apparaten en een koppeling naar de handleiding kunt downloaden.

#### Aanmelden voor RMS voor personen

1.  Met behulp van een Windows- of Mac-computer, gaat u naar de [pagina Microsoft Rights Management](https://portal.aadrm.com).

2.  Type in het e-mailadres dat u voor uw organisatie, zoals gebruikt **janetm@contoso.com** of **p.dover@fabrikam.com**.

    > [!IMPORTANT]
    > Persoonlijke e-mailaccounts worden niet ondersteund, geef geen een Microsoft-account (voorheen bekend als Microsoft Live ID-account) of een andere persoonlijke account die u van uw internetprovider thuis kunt gebruiken.

3.  Klik op **aan de slag**.

    Microsoft gebruikt uw e-mailadres om te controleren of uw organisatie al heeft een [betaald abonnement met Azure RMS](https://technet.microsoft.com/library/dn655136.aspx). Als dit het geval is, hoeft u geen RMS voor personen zodat u direct moet worden aangemeld en de self-service Meld u aan voor RMS voor personen is geannuleerd. Als een betaald abonnement voor Azure RMS niet wordt gevonden, zult u doorgaat met de volgende stap.

4.  Wachten op een bevestiging e-mailbericht moet worden verzonden naar het adres dat u hebt opgegeven. Er wordt van Microsoft (DoNotReply@microsoft.com) en het onderwerp heeft **Microsoft RMS**.

5.  Wanneer u het e-mailbericht ontvangt, klikt u op de koppeling in de aanwijzingen voor het aanmeldingsproces voltooien.

6.  Koppeling gaat u een nieuwe **Microsoft Rights Management** details over de pagina voor op te geven voor uw account. Typ in uw voornaam, uw achternaam in, voer een wachtwoord van uw keuze bevestigen, selecteer uw land (of de dichtstbijzijnde met uw vraag als uw land niet wordt vermeld) in de vervolgkeuzelijst en klik vervolgens op **Create**.

7.  Wachten op een ander e-mailbericht van Microsoft die nu bevestigt u dat uw account klaar is voor gebruik.

8.  Wanneer u het e-mailbericht ontvangt, klikt u op de koppeling voor aanmelden en lezen van de instructies voor het downloaden en installeren van de toepassing voor delen of klik op de koppeling Help voor het lezen van de delen application user guide.

Nu uw account is gemaakt, bent u klaar om te beginnen bestanden beveiligen en lezen van bestanden die anderen zijn beveiligd. Als u wordt gevraagd voor aanmelding bij beveiligen of beveiligde bestanden lezen, Voer uw e-mailadres en wachtwoord die u gebruikt voor het maken van het account voor RMS voor de personen.

### <a name="BKMK_TechnicalOverview"></a>Technisch overzicht
RMS voor personen maakt gebruik van een self-service aanmeldingsprocedure die ook wordt gebruikt door andere services die gebruikmaken van Microsoft op basis van een cloud-technologie om gebruikers te verifiëren.

Dit is wat er gebeurt in de achtergrond wanneer een gebruiker zich voor RMS voor personen aanmeldt en hun organisatie geen heeft een Office 365-abonnement of Azure-abonnement en daarom geen map in Azure om gebruikers te verifiëren:

1.  Wanneer de eerste gebruiker van een organisatie die een abonnement voor RMS voor personen, wordt de domeinnaam in hun e-mailadres hebt opgegeven gecontroleerd om te zien of deze al gekoppeld aan een Azure-tenant is. Als er geen bestaande tenant is, wordt automatisch een nieuwe tenant en Azure map gemaakt voor de organisatie die een account voor deze eerste gebruiker bevat. In tegenstelling tot met een betaald abonnement voor Azure, is dit eerste account niet een globale beheerder, maar een standard-gebruiker. De nieuwe account wordt gebruikt voor het e-mailadres en wachtwoord dat de gebruiker opgegeven.

    > [!NOTE]
    > Sommige domeinnamen kunnen niet worden gebruikt voor het maken van de map en daarom niet worden gebruikt voor RMS voor personen. De lijst met geblokkeerde domeinnamen kan worden bekeken van dit bestand JavaScript-Object notatie: [http://portal.aadrm.com/content/blocked_domains.json](http://portal.aadrm.com/content/blocked_domains.json)

    Als een bestaande tenant wordt gevonden, wordt deze gecontroleerd om te zien of er al een abonnement voor Azure RMS. Als u geen abonnement wordt gevonden, kan de beschikbare RMS voor personen abonnement worden toegevoegd.

2.  De organisatie krijgt de RMS voor personen-abonnement. Nu kunt deze gebruiker kunnen worden geverifieerd door Azure bestanden beveiligen en lezen van bestanden die anderen met Azure Rights Management zijn beveiligd. Als u beveiligde bestanden lezen wilt beveiligen, moet de gebruiker een toepassing RMS enlightened, zoals de gratis hebben [Rights Management-toepassing voor delen](https://technet.microsoft.com/library/dn919648.aspx).

3.  Wanneer de tweede gebruiker van dezelfde organisatie een RMS voor personen abonnement, wordt een nieuwe gebruikersaccount toegevoegd aan de eerder gemaakte Azure map met behulp van de organisatie RMS voor personen-abonnement. Deze tweede gebruiker kan doen alles wat de eerste gebruiker kan doen (beveiligde bestanden lezen en bestanden beveiligen), maar ook de twee gebruikers kunnen nu meer gemakkelijk veilig samenwerken omdat ze standaardsjablonen snel kunnen toepassen op bestanden met toegang tot accounts in Azure map van hun organisatie beperkte.

4.  Toekomstige gebruikers van dezelfde organisatie volgen hetzelfde patroon toe te voegen gebruikersaccounts (wanneer nieuwe gebruikers zich aanmelden) naar de organisatie Azure map. Meer accounts die zijn toegevoegd aan de map en meer gebruikers kunnen veilig samenwerken met collega's en partners en meer eenvoudig te voorkomen dat niet-geautoriseerde mensen hun bestanden te lezen wanneer ze mogen geen toegang tot deze.

Tijdens dit proces is gratis voor de organisatie en geen werk van de IT-afdeling vereist. De IT-afdeling kan echter kiezen het volgende doen:

-   **Beheren van accounts en het aanmeldingsproces**: IT-beheerders kunnen eigenaar van de automatisch gemaakte map en accounts in Azure. Vervolgens kunnen ze de accounts beheren door directory-integratie-oplossingen zoals Wachtwoordsynchronisatie en eenmalige aanmelding te implementeren. Of ze kunnen voorkomen dat gebruikers accounts maken of zich aanmeldt voor RMS voor personen.

    Voor meer informatie raadpleegt u de volgende sectie [Hoe kunnen beheerders de accounts voor RMS gemaakt voor personen](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TakeControlofAccounts).

-   **Beheren Rights Management**: IT-beheerders kunnen de RMS voor personen abonnement voor de organisatie in een betaald abonnement met Azure Rights Management worden geconverteerd. Wanneer ze dit doet, worden de bestaande Azure map en accounts behouden voor een naadloze overgang voor bestaande gebruikers die RMS voor personen. Alle bestanden die gebruikers beschermd eerder wordt nog steeds worden beveiligd met dezelfde beleid en de mensen die ze gemachtigd bent om de bestanden te gebruiken nog wel de bestanden op dezelfde manier gebruiken.

    Wanneer u houden met deze cursus komen, de voordelen van uw organisatie door te Rights Management integreert in de werkstromen, services en opgeslagen gegevens. Bovendien kunt u nu Rights Management beheren omdat u over de controle over uw organisatie tenant sleutel voor Azure Rights Management. U kunt nu het volgende doen:

    -   Configureer Exchange en SharePoint ter ondersteuning van Azure Rights Management, zelfs als deze lokaal worden uitgevoerd. Exchange en SharePoint worden ondersteund voor de online services en ze worden ondersteund door een connector voor de lokale servers. Voor meer informatie, Zie de volgende:

        -   De Exchange Online en SharePoint Online-secties van [Office 365: Configuratie voor clients en online services](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_O365) in de [Toepassingen voor Azure Rights Management configureren](../Topic/Configuring_Applications_for_Azure_Rights_Management.md) onderwerp

        -   [Implementatie van de Connector van de Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md)

    -   E-detectie uitvoeren op gegevens bedrijf eigendom, zodat u kunt, indien nodig, bestanden die zijn beveiligd decoderen met Rights Management. Zie voor meer informatie [Supergebruikers configureren voor Azure Rights Management en van detectieservices of gegevens te herstellen](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

    -   Meld u alle activiteiten voor Rights Management die gebruikt is in uw organisatie. Dit is zeer krachtige omdat u niet alleen u controleren kunt welke bestanden zijn beveiligd en die met succes toegang heeft tot de beveiligde bestanden, maar u kunt ook mogelijk verdacht gedrag van niet-geautoriseerde personen die probeert toegang tot beveiligde bestanden identificeren. Zie voor meer informatie [Logboekregistratie en analyseren van Azure Rights Management-gebruik](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

    -   Gebruikers bieden de mogelijkheid om te volgen en hun beveiligde documenten intrekken als deze functies worden ondersteund door uw [Azure RMS abonnement](https://technet.microsoft.com/dn858608). Zie voor meer informatie  [bijhouden en uw bestanden intrekken](https://technet.microsoft.com/library/dn986611.aspx) van de [RMS delen toepassing handleiding](https://technet.microsoft.com/library/dn339006.aspx).

    -   Implementeren van een Breng uw eigen sleutel oplossing (BYOK) zodat uw tenant sleutel voor Azure Rights Management gegenereerd op locatie volgens uw IT-beleid is en veilig overgedragen naar Microsoft via een Hardware Security Module HSM (). Zie voor meer informatie [Plannen en implementeren van uw Azure Rights Management Tenant-sleutel](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

## <a name="BKMK_TakeControlofAccounts"></a>Hoe kunnen beheerders de accounts voor RMS gemaakt voor personen
Als u niet converteren van uw organisatie RMS voor personen-abonnement in een betaald abonnement wilt, kunt u bepalen de gebruikersaccounts in de Azure map die is gemaakt voor uw organisatie in de volgende manieren:

-   Directory-integratieoplossingen implementeren voor Azure Active Directory en de Active Directory Domain Services-infrastructuur. U kunt de accounts en wachtwoorden synchroniseren zodat gebruikers geen nieuwe accounts voor Rights Management gebruik te maken en uw lokale wachtwoordbeleid worden toegepast op de nieuwe Azure gebruikersaccounts. U kunt ook wachtwoorden synchroniseren zodat gebruikers niet hoeven te onthouden van een ander wachtwoord voor het gebruik van Rights Management.

-   U kan voorkomen dat gebruikers zich aanmeldt Azure Rights Management gebruiken met de RMS voor personen-abonnement. In de meeste gevallen is er weinig voordeel doet dit omdat gebruikers ofwel van bestanden zonder protection delen wordt (dat kan risico voor uw bedrijf) of een ander bestand protection mechanisme waarvoor de IT-afdeling met de optie voor toegang tot de gegevens niet worden gebruikt. Echter als u dat gebruikers zich wilt aanmeldt voor RMS personen gebruik, voert u een van de volgende nadat u de eigenaar van de map van uw organisatie in Azure hebben getroffen:

    -   Voorkomen dat alle gebruikers zich aanmeldt voor selfservice-abonnementen met RMS voor personen.  Op dit moment instellen u dit door de service; niet de instelling geldt voor alle Azure abonnementen die gebruikmaken van het proces Self-service. Stel hiervoor de **AllowAdHocSubscriptions** parameter op false met de [Set MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) cmdlet uit de Windows PowerShell-module voor Azure Active Directory. Bijvoorbeeld: **Set-MsolCompanySettings -AllowAdHocSubscriptions $false**

    -   Voorkomen dat gebruikers een nieuw account maken in Azure, wat betekent dat alleen gebruikers die al een account in Azure kunnen aanmelden voor selfservice-abonnementen, waaronder RMS voor personen.  Stel hiervoor de **AllowEmailVerifiedUsers** parameter op false met de [Set MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) cmdlet uit de Windows PowerShell-module voor Azure Active Directory. Bijvoorbeeld: **Set-MsolCompanySettings -AllowEmailVerifiedUsers $false -AllowAdHocSubscriptions $true**

    -   De Active Directory Domain Services-infrastructuur worden gesynchroniseerd met Azure Active Directory. Deze actie geen nieuwe accounts kunnen worden gemaakt wanneer gebruikers zich voor selfservice-abonnementen aanmelden, zoals RMS voor personen en u kunt verwijderen of uitschakelen van accounts die eerder in Azure Active directory zijn gemaakt.

Om te bepalen van de gebruikersaccounts in Azure Active directory, of om te voorkomen dat gebruikers zich aanmeldt voor RMS voor personen, moet u een Azure-abonnement hebt en eigenaar van de map. Als u nog geen Azure-abonnement hebt, kunt u een gratis. Als een map automatisch tijdens de self-service gemaakt is, eigenaar van het domein dat is gemaakt. Als u al een map in Azure eigenaar, maar gebruikers opgegeven een nieuw domein dat u in uw organisatie, samenvoegen met domein uw bestaande map. Voor meer informatie, Zie de instructies in [Wat Self-Service aanmelding voor Azure is?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/)

## <a name="BKMK_Detect"></a>Als uw gebruikers hebt aangemeld voor RMS voor personen bepalen
Als een beheerder hoe wist u dat als uw gebruikers hebt aangemeld voor RMS voor personen? U kunt gebruiken of een combinatie van de volgende methoden:

-   Gebruikers vragen hoe ze uiterst vertrouwelijk bestanden beveiligen met name wanneer het samenwerken met anderen buiten de organisatie.

-   Als u geen Azure-abonnement voor uw organisatie hebt, gebruikt u de [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) cmdlet om te zien of **RIGHTSMANAGEMENT_ADHOC** wordt geretourneerd als een van de abonnementen. Als het, is dit de RMS voor personen-abonnement is verleend voor de organisatie, met een groep van actieve eenheden beschikbaar voor gebruikers het aanmeldingsproces Self-service gebruiken.

-   Gebruik een system management-oplossing, zoals System Center Configuration Manager inventarisatie software is geïnstalleerd en software in gebruik. De Rights Management delen van de toepassing wordt uitgevoerd met behulp van de **ipviewer.exe** programma en u kunt [download en installeer de toepassing](http://go.microsoft.com/fwlink/?LinkId=303970) gratis voor andere kenmerken over deze toepassing die u vervolgens voor software-inventarisatie gebruiken.

-   Worden op zoek naar bestandsextensies die zijn gemaakt door de delen Rights Management-toepassing. De .pfile en .ppdf bestandsextensies zijn de meest duidelijke voorbeelden, maar er zijn andere bestanden die de bestandsnaamextensie wijzigen wanneer ze systeemeigen worden beschermd door Rights Management. Zie voor meer informatie de [ondersteunde bestandstypen en extensies](http://technet.microsoft.com/library/dn339003.aspx) sectie de [delen toepassing Rights Management-beheerdershandleiding](http://technet.microsoft.com/library/dn339003.aspx).

## Zie ook
[Aan de slag met Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

