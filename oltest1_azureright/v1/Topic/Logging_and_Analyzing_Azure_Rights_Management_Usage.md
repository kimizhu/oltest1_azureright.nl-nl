---
description: na
keywords: na
title: Logging and Analyzing Azure Rights Management Usage
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
---
# Logboekregistratie en analyseren van Azure Rights Management-gebruik
Gebruik de informatie in dit onderwerp om te begrijpen hoe kunt u zich aanmeldt met Azure Rights Management (Azure RMS) gebruik. De Azure Rights Management-service kan zich aanmelden op elke aanvraag dat het maakt voor uw organisatie, inclusief aanvragen van gebruikers, acties die worden uitgevoerd door Rights Management-beheerders in uw organisatie en acties die worden uitgevoerd door Microsoft operators voor ondersteuning van uw Azure Rights Management-implementatie.

U kunt deze logboeken Azure Rights Management ondersteuning voor de volgende zakelijke scenario's:

-   Voor meer inzicht analyseren.

    Azure Rights Management schrijft Logboeken in W3C extended log-indeling naar een Azure-opslag-account dat u opgeeft. U kunt deze logboeken vervolgens verwijzen naar een bibliotheek van uw keuze (zoals een database, een systeem online analytical processing (OLAP) of een kaart verminderen system) voor het analyseren van gegevens en rapporten maken. Als u bijvoorbeeld kan u identificeren die toegang heeft tot de RMS beveiligde gegevens. U kunt bepalen wat RMS beveiligde gegevens mensen zijn openen, en welke apparaten en van waar. U kunt vindt of mensen beveiligde inhoud met succes kan lezen. U kunt ook aangeven welke gebruikers een belangrijk document die is beveiligd hebt gelezen.

-   Monitor voor misbruik.

    Azure logboekgegevens Rights Management is beschikbaar in near-realtime, zodat u kunt het gebruik van uw bedrijf van Rights Management continu bewaken. 99,9% aan logboeken zijn beschikbaar binnen 15 minuten van een actie RMS gestart.

    U wilt worden gewaarschuwd als er is een onverwachte toename van mensen lezen RMS beveiligde gegevens buiten de standaard werkuren dit kunnen duiden op een kwaadwillende gebruiker verzamelen van informatie aan concurrenten te verkopen. Of als dezelfde gebruiker blijkbaar werkt met gegevens uit twee verschillende IP-adressen binnen een korte periode, dit kan erop duiden dat een gebruikersaccount is ontdekt.

-   Forensische analyse uitvoeren.

    Als er een informatie-geheugenlek, bent u waarschijnlijk te worden gesteld die onlangs toegang krijgen tot specifieke documenten en welke informatie een mogelijke persoon toegang tot onlangs. Wanneer u Azure Rights Management en logboekregistratie omdat gebruikers van inhoud beveiligde altijd over een licentie Rights Management documenten en afbeeldingen die worden beschermd door Azure Rights Management beschikt moet, zelfs als deze bestanden worden door de e-mailbericht verplaatst of gekopieerd naar een USB-station of andere opslagapparaten openen, kunt u dit type vragen beantwoorden. Dit betekent dat als kunt u Azure Rights Management logboeken een definitieve bron van informatie voor forensische analyse wanneer u uw gegevens beveiligt met Azure Rights Management.

> [!NOTE]
> Als u geïnteresseerd bent alleen in de registratie van administratieve taken voor Azure Rights Management en komen niet wilt bijhouden hoe gebruikers Rights Management gebruiken, kunt u de [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) Windows PowerShell-cmdlet voor Azure Rights Management.
> 
> U kunt ook de Azure-portal gebruiken voor op hoog niveau gebruiksrapporten met **RMS gebruik**, **meest actieve RMS gebruikers**, **gebruik van het apparaat RMS**, en **RMS gebruik van toepassingen ingeschakeld**. Toegang tot deze rapporten uit de Azure-portal, klikt u op **Active Directory**, selecteer een map te openen en klik vervolgens op **rapporten**,

Gebruik de volgende secties voor meer informatie over Azure Rights Management-gebruikslogboekregistratie.

-   [Azure Rights Management-gebruikslogboekregistratie inschakelen](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_EnableRMSLogging)

-   [Toegang krijgen tot uw gebruik van Azure Rights Management gebeurtenislogboeken](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs)

-   [Over het beheren van de opslag van uw Azure Rights Management-logboek](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_ManageStorage)

-   [Het overdragen van toegang tot uw gebruik van Azure Rights Management Logboeken](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate)

-   [Het gebruik van uw Azure Rights Management interpreteren gebeurtenislogboeken](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret)

-   [Windows PowerShell-verwijzing](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_PowerShell)

## <a name="BKMK_EnableRMSLogging"></a>Azure Rights Management-gebruikslogboekregistratie inschakelen
Logboekregistratie van het gebruik Azure Rights Management is optioneel, dus als u gebruiken wilt, moet u specifieke stappen uitvoeren. Wanneer u Azure Rights Management-gebruikslogboekregistratie gebruikt, is er geen wijziging in de werking van Rights Management en het registratieproces zelf is gratis. Echter, moet u een Azure-opslag-account voor de logboeken en brengt voor deze opslag.

Voordat u begint, moet u de volgende vereisten voor gebruik van Azure Rights Management-gebruikslogboekregistratie voldoen:

|Vereiste|Meer informatie|
|------------|-------------------|
|Een IT-beheerde abonnement met Azure Rights Management|U moet een Microsoft Azure Rights Management-abonnement wordt beheerd door uw organisatie hebben. Organisaties die gebruikmaken van RMS voor personen Azure Rights Management-gebruikslogboekregistratie niet gebruiken.<br /><br />Als uw organisatie gebruikers die met RMS personen heeft, bevat Azure Rights Management-gebruikslogboekregistratie zeer belangrijke zakelijke redenen RMS voor personen converteren naar een Microsoft Azure Rights Management-abonnement.<br /><br />Zie voor meer informatie over de abonnementen Azure RMS, zoals de [Cloud-abonnementen die ondersteuning van Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) sectie de [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) onderwerp.<br /><br />Zie voor meer informatie over RMS voor personen [RMS voor personen en Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md)|
|Azure-abonnement|U moet een abonnement op Azure en voldoende opslag op Azure hebt voor uw Azure Rights Management-Logboeken.|
|Windows PowerShell voor Azure Rights Management|Als u nog niet hebt gedaan downloaden en installeren van de Windows PowerShell-module voor Azure Rights Management. U kunt Windows PowerShell-cmdlets configureren en beheren van uw Azure Rights Management-Gebruik-Logboeken.<br /><br />Zie voor meer informatie [Installatie van Windows PowerShell voor Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).|
De volgende procedure gebruiken om u te logboekregistratie Azure Rights Management-gebruik, inclusief stappen om een Azure-opslagaccount maken en vervolgens configureren Azure voor gebruik van dit opslagaccount voor uw Rights Management-Logboeken.

> [!NOTE]
> Deze procedure wordt ervan uitgegaan dat u een Azure-account hebt. Logboekregistratie van het gebruik Azure Rights Management ondersteunt afzonderlijke accounts, maar wordt aangeraden, werk gebruikt of opleiding accounts. Wij raden bovendien te maken van een account toegewezen opslag voor uw Rights Management-Logboeken. U moet de sleutels opslag toegang delen met Azure Rights Management en mogelijk met andere mensen als ze ook de logboekbestanden gebruiken.
> 
> Zie voor meer informatie over Azure-opslag, de [Azure documentatie voor opslag](http://azure.microsoft.com/documentation/services/storage/).

#### Het maken van uw opslagaccount en Azure Rights Management-gebruikslogboekregistratie inschakelen

1.  Meld u aan bij de [Azure-portal](https://manage.windowsazure.com/).

2.  Selecteer **opslag**.

    > [!TIP]
    > Als u deze optie niet ziet, Controleer of u geen Azure-abonnement naast uw abonnement voor Rights Management.

3.  Klik op **een OPSLAGACCOUNT maken** en voor de **URL**, Geef een unieke naam voor opslagaccount en zo nodig wijzigen de **locatie/AFFINITEIT groep** zodat deze overeenkomt met uw regio.

4.  Klik op **OK**, en wacht totdat de naam van uw opslag die de status van **Online**.

5.  Klik op **toegang sleutels beheren**.

6.  Uit de **sleutels beheren van toegang** dialoogvenster met daarin de sleutels de primaire en secundaire toegang tot de van primaire toegangssleutel naar het Klembord kopiëren en sluit het dialoogvenster.

7.  Start van Windows PowerShell met de **Als administrator uitvoeren** optie. Voer de [Connect AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx) opdracht verbinding maken met de Azure Rights Management-service:

    ```
    Connect-AadrmService
    ```

8.  Gebruik de [Set AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) opdracht om op te geven waar u wilt behouden de logboekbestanden van het gebruik van Azure Rights Management vervangt *&lt; Access_Key &gt;* met access primaire sleutel die u in stap 6 gekopieerd en *&lt; StorageAccount &gt;* met de naam van het opslagaccount dat u hebt gemaakt in stap 3:

    ```
    $accesskey = convertto-securestring -asplaintext -force –string <Access_Key> Set-AadrmUsageLogStorageAccount -AccessKey $accesskey -StorageAccount <StorageAccount>
    ```

9. Gebruik de [Enable AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx) opdracht Azure Rights Management-gebruikslogboekregistratie inschakelen:

    ```
    Enable-AadrmUsageLogFeature
    ```
    Hier ziet u het bericht: **De functie gebruik logboek is ingeschakeld voor de Rights management-service.**

Gebruikslogboekregistratie is ingeschakeld, Azure Rights Management begint af te melden alle acties voor uw organisatie en deze gegevens worden opgeslagen met het opslagaccount. Logboekgegevens is niet beschikbaar voor dit punt.

## <a name="BKMK_AccesAndUseLogs"></a>Toegang krijgen tot uw gebruik van Azure Rights Management gebeurtenislogboeken
Azure Rights Management schrijft logboeken naar uw Azure-opslagaccount als een reeks van BLOB's. Elke blob bevat een of meer records in het logboek, W3C uitgebreide indeling. De blob-namen zijn getallen in de volgorde waarin ze zijn gemaakt. De [Het gebruik van uw Azure Rights Management interpreteren gebeurtenislogboeken](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret) verderop in dit document bevat meer informatie over de inhoud van het logboek en hun maken.

Dit kan even duren voor logboeken worden weergegeven in uw opslagaccount na een Azure Rights Management-actie. De meeste logboeken weergegeven binnen 15 minuten.

Het opslagaccount dat u hebt gemaakt voor uw gebruik van Azure Rights Management logboeken lijkt op een postvak en ondersteunt lezen rechtstreeks vanuit het opslagaccount, maar niet is geoptimaliseerd op deze manier worden gebruikt. In plaats daarvan voor de beste prestaties en bespaar kosten, wordt aangeraden de logboeken te downloaden naar de lokale opslag, zoals een lokale map, een database, of een opslagplaats kaart beperken.

U kunt uw van Gebruikslogboeken op twee manieren downloaden:

-   Gebruik de Windows PowerShell-cmdlet [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx).

    Dit is de meest eenvoudige manier voor toegang tot uw van Gebruikslogboeken. Deze cmdlet downloads logboeken op uw computer, elke blob downloaden als een bestand naar een locatie die u opgeeft.

-   Gebruik de [Azure opslag SDK](http://www.windowsazure.com/en-us/develop/net/) schrijven van uw eigen aangepaste toepassing voor het downloaden van de logboeken.

    Een aangepaste toepassing kunt bieden meer flexibiliteit dan de cmdlet Get-AadrmUsageLogs. U kunt het downloaden van Logboeken delegeren aan iemand of een proces dat uw Azure Rights Management-beheerdersreferenties moet niet te gebruiken. Of u kunt de logboeken in realtime navraag omdat u wilt bewaken voor misbruik.

#### Uw van Gebruikslogboeken kan worden gedownload via de PowerShell

-   Start van Windows PowerShell met de **Als administrator uitvoeren** optie en voer **Get-AadrmUsageLog –Path &lt;location&gt;**. Bijvoorbeeld, na het maken van een map met de naam **logs** op uw E-station:

    -   Alle beschikbare logboeken downloaden naar de map E:\Logs: `Get-AadrmUsageLog -Path "e:\logs"`

    -   Voor het downloaden van een specifiek bereik van BLOB's: `Get-AadrmUsageLog –Path "e:\logs" –FromCounter 1024 –ToCounter 2047`

Als u deze cmdlets uitvoert, wordt Windows PowerShell de naam van de laatste blob dat is gedownload. U kunt deze naam toewijzen aan een variabele, waarmee u Get-AadrmUsageLog uitgevoerd in een lus of een taak plannen, alleen de incrementele logboeken elke keer downloaden.

Bijvoorbeeld:

**PS C:\ &gt; $LastBlobName = Get-AadrmUsageLog – pad "e:\logs"**

**1527**

**PS C:\ &gt; $LastBlobName**

**1527**

> [!TIP]
> U kunt uw gedownloade logboekbestanden naar een CSV-indeling samenvoegen met behulp van [van Microsoft logboek Parser](http://www.microsoft.com/download/details.aspx?id=24659), die is een hulpprogramma converteren tussen verschillende indelingen voor bekende logboekbestanden. U kunt ook dit hulpprogramma gebruiken gegevens te converteren naar SYSLOG-indeling of in een database importeren. Nadat u het programma hebt geïnstalleerd, voert u **LogParser.exe /?** voor help en informatie over dit hulpprogramma gebruiken. Bijvoorbeeld de volgende opdracht om alle gegevens importeren in een bestandsindeling .log kan worden uitgevoerd: **logparser –i:w3c –o:csv “SELECT &#42; INTO AllLogs.csv FROM &#42;.log”**.

U kunt onderbreken en hervatten logboekregistratie van het gebruik. Wanneer u logboekregistratie onderbreekt, behoudt Azure Rights Management opslag gegevens over uw account, zodat u kunt eenvoudig hervatten zich opnieuw aanmeldt.

#### Onderbreken en hervatten gebruikslogboekregistratie

-   Als u wilt onderbreken logboekregistratie, gebruikt u de volgende cmdlet: [Disable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   Als u wilt doorgaan met logboekregistratie, gebruikt u de volgende cmdlet: [Inschakelen AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   Als u wilt controleren of logboekregistratie is ingeschakeld of uitgeschakeld, gebruikt u de volgende cmdlet: [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

    Een waarde van **waar** betekent dat gebruikslogboekregistratie is ingeschakeld voor Azure Rights Management en een waarde van **False** betekent dat gebruikslogboekregistratie is uitgeschakeld.

## <a name="BKMK_ManageStorage"></a>Over het beheren van de opslag van uw Azure Rights Management-logboek
U in rekening worden gebracht voor de opslagruimte die wordt gebruikt om te zorgen dat uw Azure Rights Management-Logboeken.

Azure Rights Management heeft geen automatisch beheer van uw gebruik van logboekbestanden. Als u geen actie ondernemen, blijven ze in uw opslagaccount. Echter om meer ruimte en opslag verlagen, kunt u deze verwijderen nadat u deze hebt gedownload. Of u kunt kiezen welke bestanden verwijderen. Met één uitzondering Azure Rights Management niet gebruikt deze logboekbestanden zodat er geen beperkingen over als u deze kunt verwijderen.

Naam van het bestand dat u moet niet verwijderen (of wijzigen) **metagegevens** die zich in de **rms-metagegevens** container. Deze blob Azure Rights Management gebruikt voor het bijhouden van de laatste blob getal dat deze worden gebruikt. Als dit bestand wordt verwijderd, Azure Rights Management een nieuwe container voor logboeken begint met een blob-getal dat bij 1 begint en alle toekomstige downloads die gebruikmaken van de cmdlet Get-AadrmUsageLog gebruiken deze nieuwe container voor het downloaden van logboekbestanden. Alle logboeken in de oorspronkelijke container zijn als gevolg hiervan behouden, maar losgekoppeld. De enige manier om deze zwevende logboeken downloaden is de Azure-opslag SDK gebruiken.

> [!TIP]
> In plaats van het beheer van uw Azure Rights Management logboek opslagruimte uzelf, kunt u deze functie management delegeren aan een ander bedrijf door uw opslag naam en toegang accountcode delen. Zie voor meer informatie de [Het overdragen van toegang tot uw gebruik van Azure Rights Management Logboeken](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate) verderop in dit onderwerp.

U kunt in sommige gevallen kunnen uw toegang tot opslag sleutels genereren. Bijvoorbeeld:

-   U kunt het bedrijf dat uw Azure Rights Management-Gebruikslogboeken beheert wijzigen.

-   U vermoedt dat uw opslag toegangssleutel is ingebroken.

Als dit aan u gebeurt, is dit wanneer u de sleutel secundaire toegang (op de veronderstelling dat u de van primaire toegangssleutel eerder gebruikte) om te controleren of de continuïteit van de service. Wanneer u de toegang tot sleutel die u niet eerder gebruikte opnieuw genereren, configureert u vervolgens Azure Rights Management om de nieuwe sleutel te gebruiken. Gebruik de volgende procedure de secundaire toegangssleutel opnieuw genereren en configureren van Azure Rights Management wilt gebruiken:

#### Naar de secundaire toegangssleutel opnieuw genereren

1.  Meld u aan bij de [Azure-portal](https://manage.windowsazure.com/).

2.  Selecteer **opslag**.

3.  Klik op **toegang sleutels beheren**.

4.  In de **sleutels beheren van toegang** in het dialoogvenster, klikt u op **genereren** naast de secundaire toegangssleutel en de nieuwe sleutel secundaire toegang naar het Klembord kopiëren.

5.  Start van Windows PowerShell met de **Als administrator uitvoeren** optie en gebruiken de [Set AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) Azure Rights Management voor gebruik van deze nieuwe sneltoets, configureren met de cmdlet vervangt *&lt; StorageAccount &gt;* met de naam van uw opslagaccount en *&lt; Access_Key &gt;* met de sleutel geregenereerde secundaire toegang die u zojuist hebt gekopieerd:

    ```
    Set-AadrmUsageLogStorageAccount -StorageAccount <StorageAccount>-AccessKey <Access_Key>
    ```
    > [!WARNING]
    > U kunt activeren met een andere opslagaccount wanneer u deze opdracht uitvoert, deze actie orphans de vorige logboeken en ze niet langer toegankelijk is voor de cmdlet Set-AadrmUsageLogStorageAccount of vergelijkbare opdrachten voor het beheer en functies.

6.  Terug in de **sleutels beheren van toegang** dialoogvenster vak, uw primaire toegangssleutel genereren.

## <a name="BKMK_Delegate"></a>Het overdragen van toegang tot uw gebruik van Azure Rights Management Logboeken
U kunt toegang delegeren aan uw RMS-Logboeken door uw opslag naam en toegang accountcode delen. U kunt overdragen toegang tot een andere beheerder, een ontwikkelaar binnen uw organisatie of onafhankelijke softwareleverancier (ISV). Omdat zij geen uw referenties RMS-beheerder hebben, kunnen ze de cmdlet Get-AardrmUsageLog gebruiken voor het downloaden van de RMS-Logboeken. Ze moeten in plaats daarvan de opslag Windows SDK gebruiken om de logboeken downloaden. Ze kunnen ook een toepassing de logboeken rechtstreeks uit Azure-opslag lezen schrijven.

Is het veilig delen van uw opslag naam en toegang accountcode op deze manier als het opslagaccount is gekoppeld aan de RMS-Logboeken. Hoewel anderen uw toegangssleutel hebben, kunnen ze dit gebruiken voor toegang tot een andere opslagaccount of het gebruik van uw account RMS-tenant.

## <a name="BKMK_Interpret"></a>Het gebruik van uw Azure Rights Management interpreteren gebeurtenislogboeken
Gebruik de volgende informatie kunt u het gebruik van de Azure Rights Management worden geïnterpreteerd.

### De indeling van de account opslag
De eerste keer die Azure Rights Management logboeken naar uw opslagaccount schrijft Hiermee de volgende twee containers:

-   **Rms-metagegevens**: Deze container is gereserveerd voor Azure Rights Management. Wijzig of verwijder deze container niet.

-   **Rms - logboeken - &lt; guid &gt;**: Deze container is waar Azure Rights Management wordt gemaakt en opgeslagen van de logboeken. U kunt geen bestanden in deze container veilig verwijderen als u niet langer de logboekregistratie voor de informatie die ze bevatten.

Gedurende een periode, Azure Rights Management kan opleveren aanvullende **Rms - logboeken - &lt; guid &gt;** containers. Bijvoorbeeld als de **Rms-metagegevens** container is beschadigd of het per ongeluk is verwijderd, Azure Rights Management wordt de inhoud en wordt een nieuw **Rms - logboeken - &lt; guid &gt;** container voor alle toekomstige Logboeken. De oude logboekbestanden in de oude container niet worden verwijderd, maar worden losgekoppeld.

### Een reeks van het logboek
Azure Rights Management worden de logboeken geschreven als een reeks van BLOB's. Elke blob bevat een of meer records in het logboek, uitgebreide W3C-logboek indeling.

De naam van elke blob is een getal. De eerste blob heet in elke container logboek 000000001. Elke blob heet opeenvolgend in de volgorde waarin deze is gemaakt. Elke blob bevat een of meer records in het logboek. Elke logboekrecord heeft een UTC-tijdstempel dat aangeeft wanneer de bijbehorende aanvraag is verzonden door Azure Rights Management.

> [!IMPORTANT]
> De logboekregistratie voor Azure Rights Management system is waarmee u zich aanmeldt snel plaats in de juiste volgorde strikt geoptimaliseerd. De volgorde van de BLOB's, evenals de volgorde van de records binnen een blob wordt mogelijk niet op chronologische volgorde. De enige reden die de BLOB's opeenvolgende naam is waarmee u efficiënt stapsgewijs downloaden.
> 
> Twee voorbeelden van mogelijke logboek reeks resultaten:
> 
> -   De records in het logboek in de blob 000000004 kunnen chronologische volgorde met de records in het logboek in de blob 000000003 overlappen. In uitzonderlijke gevallen, alle records in het logboek in de blob 000000004 mogelijk zijn gegenereerd voordat alle records in het logboek in de blob 000000003.
> -   De tweede logboekrecord in een blob mogelijk zijn gegenereerd voor de eerste aanmelding record, maar in omgekeerde volgorde naar opslag zijn geschreven.

Voordat u uw Azure Rights Management-Gebruikslogboeken analyseert, wordt aangeraden te downloaden en het logboek importeren in een opslagplaats waar u de logboeken op basis van hun tijdstempel kunt sorteren. Zie voor meer informatie over de logboeken downloaden, de [Toegang krijgen tot uw gebruik van Azure Rights Management gebeurtenislogboeken](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs) in dit onderwerp.

Omdat de logboeken niet noodzakelijkerwijs chronologische maar het merendeel van deze zijn geschreven binnen 15 minuten van de aanvraag bij het identificeren van de logboeken die u wilt met behulp van de tijdstempel, toevoegen 15 minuten de tijd waarin u geïnteresseerd bent. Download deze logboeken. Deze strategie Zorg ervoor dat u bijna alle logboeken ophalen.

Één ding te weten is dat de tijdstempel voor elke logboekrecord de lokale tijd van de Azure Rights Management-service die de aanvraag is verwerkt. Aangezien Azure Rights Management wordt uitgevoerd op meerdere servers over meerdere datacentrum, lijken soms de logboeken worden buiten de reeks, zelfs wanneer ze hun tijdstempel gesorteerd. De verschillende is echter klein en meestal binnen een minuut. In de meeste gevallen is dit niet een probleem dat een probleem voor logboekanalyse is.

### De indeling van de blob
Elke blob heeft W3C uitgebreide indeling. Begint met de volgende twee regels:

**#Software: RMS**

**#Version 1.1**

De eerste regel geeft aan dat dit Azure Rights Management logboeken zijn. De tweede regel geeft aan dat de rest van de blob de versie 1.1-specificatie volgt. Wij raden u aan dat alle toepassingen die deze logboeken parseren deze twee regels controleren voordat u doorgaat met de rest van de blob parseren.

De derde regel servernetwerkprotocollen wordt een lijst met veldnamen die worden gescheiden door tabs:

**#Fields: datum tijd rij-id type aanvraag gebruikers-id resultaat correlatie-id inhoud-id eigenaar e-verlener sjabloon-id-bestandsnaam publicatiedatum c-info c-ip**

Elk van de volgende regels is een logboekrecord. De waarden van de velden zijn in dezelfde volgorde als de vorige regel en worden gescheiden door tabs. Gebruik de volgende tabel worden de velden geïnterpreteerd.

|Veldnaam|W3C-gegevenstype|Beschrijving|Voorbeeldwaarde|
|------------|--------------------|----------------|-------------------|
|datum|Datum|UTC-datum wanneer de aanvraag is verzonden.<br /><br />De bron is de lokale klok op de server die de aanvraag.|2013-06-25|
|tijd|Tijd|UTC-tijd in 24 uur indeling bij de aanvraag is verzonden.<br /><br />De bron is de lokale klok op de server die de aanvraag.|21:59:28|
|rij-id|Tekst|De unieke GUID voor deze logboekrecord.<br /><br />Deze waarde is handig als u cumulatieve Logboeken of Logboeken kopiëren naar een andere indeling.|1c3fe7a9-d9e0-4654-97b7-14fafa72ea63|
|type aanvraag|Naam|Naam van de RMS-API die is aangevraagd.|AcquireLicense|
|gebruikers-id|Tekenreeks|De gebruiker die de aanvraag ingediend.<br /><br />De waarde is ingesloten in enkele aanhalingstekens. Sommige aanvraagtypen zijn anoniem, in dit geval de waarde is '.|'joe@contoso.com'|
|resultaat|Tekenreeks|'Geslaagd' als de aanvraag is geslaagd aangeboden.<br /><br />Het fouttype in enkele aanhalingstekens als de aanvraag is mislukt.|"Geslaagd"|
|correlatie-id|Tekst|GUID die wordt gedeeld tussen de RMS-client-logboekbestand en het logboek voor server voor een bepaalde aanvraag.<br /><br />Deze waarde kan nuttig zijn bij het oplossen van problemen met client zijn.|cab52088-8925-4371-be34-4b71a3112356|
|inhoud-id|Tekst|GUID tussen accolades waaraan de beveiligde inhoud (bijvoorbeeld een document).<br /><br />Dit veld heeft een waarde alleen als type aanvraag AcquireLicense en voor andere aanvraagtypen leeg is.|{bb4af47b-cfed-4719-831d-71b98191a4f2}|
|e-eigenaar|Tekenreeks|E-mailadres van de eigenaar van het document.|Alice@contoso.com|
|verlener|Tekenreeks|E-mailadres van de verlener van het document.|Alice@contoso.com (of) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com'|
|Sjabloon-id|Tekenreeks|ID van de sjabloon die wordt gebruikt om het document te beveiligen.|{6d9371a6-4e2d-4e97-9a38-202233fed26e}|
|Bestandsnaam|Tekenreeks|Bestandsnaam van het document dat is beveiligd.|TopSecretDocument.docx|
|Datum gepubliceerd|Datum|Datum waarop het document is beveiligd.|2015-10-15T21:37:00|
|c-info|Tekenreeks|Informatie over het clientplatform die de aanvraag maakt.<br /><br />De specifieke tekenreeks is afhankelijk van de toepassing (bijvoorbeeld het besturingssysteem of de browser).|' MSIPC; versie = 1.0.623.47; Toepassingsnaam = WINWORD. EXE; AppVersion = 15.0.4753.1000; AppArch x 86; = OSName = Windows; Versie_besturing = 6.1.7601; OSArch amd64 ='|
|c-ip|Adres|IP-adres van de client die de aanvraag indient.|64.51.202.144|

#### Uitzonderingen voor het veld gebruikers-id
Hoewel het veld gebruikers-id geeft meestal aan de gebruiker aan wie de aanvraag ingediend, zijn er twee uitzonderingen waar de waarde niet is toegewezen aan een echte gebruiker:

-   De waarde **' microsoftrmsonline @&lt; YourTenantID &gt;. &lt; regio &gt; rms.. aadrm.com'**.

    Dit geeft aan dat een Office 365-service, zoals Exchange Online of Sharepoint Online is die de aanvraag verzendt. In de tekenreeks *&lt; YourTenantID &gt;* is de GUID voor uw tenant en *&lt; regio &gt;* de regio waar uw tenant is geregistreerd. Bijvoorbeeld, **na** Noord-Amerika vertegenwoordigt **eu** vertegenwoordigt Europa, en **Azië** Asia vertegenwoordigt.

-   Als u de RMS-connector worden gebruikt.

    Aanvragen van deze connector bent aangemeld met de service principal name die RMS wordt automatisch gegenereerd als de RMS-connector te installeren.

#### Standaard aanvraagtypen
Er zijn veel aanvraagtypen voor Azure Rights Management, maar de volgende tabel vindt u enkele van de meest veelgebruikte aanvraagtypen.

|Aanvraagtype|Beschrijving|
|----------------|----------------|
|AcquireLicense|een client van een computer met Windows op basis van een licentie voor RMS beveiligde inhoud aanvraagt.|
|AcquirePreLicense|een client namens de gebruiker vraagt om een licentie voor RMS beveiligde inhoud.|
|AcquireTemplates|is aangeroepen op verwerft sjablonen op basis van de sjabloon-id's|
|AcquireTemplateInformation|een aanroep van de id's van de sjabloon voor het ophalen van de service is gemaakt.|
|AddTemplate|een oproep uitgaat van de Azure-portal op een sjabloon toevoegen.|
|BECreateEndUserLicenseV1|een oproep uitgaat van een mobiel apparaat te maken van een gebruiksrechtovereenkomst.|
|BEGetAllTemplatesV1|een oproep uitgaat van een mobiel apparaat (back-end) om alle sjablonen.|
|Certificeren|de client is waaruit de inhoud voor beveiliging.|
|Decoderen|de client probeert de RMS beveiligde inhoud ontsleutelen.|
|DeleteTemplateById|een aanroep van de Azure-portal verwijderen van een sjabloon door de sjabloon-id|
|ExportTemplateById|een oproep uitgaat exporteren van een sjabloon op basis van een sjabloon-id van de Azure-portal|
|FECreateEndUserLicenseV1|lijkt op de AcquireLicense-aanvraag, maar van mobiele apparaten.|
|FECreatePublishingLicenseV1|hetzelfde als certificeren en GetClientLicensorCert gecombineerd van mobiele clients.|
|FEGetAllTemplates|een oproep uitgaat, van een mobiel apparaat (front-end) voor het ophalen van de sjablonen.|
|GetAllTemplates|een oproep uitgaat alle sjablonen ophalen uit de Azure-portal.|
|GetClientLicensorCert|de client een publicatie certificaat (dat verderop wordt gebruikt om inhoud te beschermen) opgevraagd van een Windows-computer.|
|GetConfiguration|een Azure PowerShell-cmdlet wordt aangeroepen als u de configuratie van de tenant Azure RMS.|
|GetConnectorAuthorizations|een aanroep van de RMS-connectors bij het ophalen van de configuratie van de cloud.|
|GetTenantFunctionalState|de Azure-portal wordt gecontroleerd of Azure RMS is geactiveerd.|
|GetTemplateById|een aanroep van de Azure-portal een sjabloon-id opgeven voor het ophalen van een sjabloon|
|ExportTemplateById|een aanroep wordt gemaakt van de Azure-portal een sjabloon exporteren door te geven van een sjabloon-id|
|FindServiceLocationsForUser|een oproep uitgaat query voor URL's die wordt gebruikt om aan te roepen certificeren of AcquireLicense.|
|ImportTemplate|een oproep uitgaat van de Azure-portal op een sjabloon importeren.|
|ServerCertify|een oproep uitgaat van een RMS-clients (zoals SharePoint) om te certificeren van de server.|
|SetUsageLogFeatureState|een oproep uitgaat gebruikslogboekregistratie inschakelen.|
|SetUsageLogStorageAccount|een aanroep naar de locatie van de Azure RMS-Logboeken.|
|SignDigest|een oproep uitgaat als een sleutel wordt gebruikt voor het ondertekenen van toepassing. Dit heet doorgaans eenmaal per AcquireLicence (of FECreateEndUserLicenseV1) certificeren, en GetClientLicensorCert (of FECreatePublishingLicenseV1).|
|UpdateTemplate|een aanroep van de Azure-portal bijwerken van een bestaande sjabloon.|

## <a name="BKMK_PowerShell"></a>Windows PowerShell-verwijzing
Gebruik de volgende Windows PowerShell-cmdlets om te configureren en gebruiken van Azure Rights Management-gebruikslogboekregistratie:

-   [Disable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   [Inschakelen AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx)

-   [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

-   [Get-AadrmUsageLogLastCounterValue](https://msdn.microsoft.com/library/azure/dn629423.aspx)

-   [Get-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629419.aspx)

-   [Set AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx)

Zie voor meer informatie over het gebruik van Windows PowerShell voor Azure Rights Management [Azure Rights Management beheren met behulp van Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Zie ook
[Met behulp van Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

