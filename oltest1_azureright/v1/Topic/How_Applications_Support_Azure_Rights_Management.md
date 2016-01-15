---
description: na
keywords: na
title: How Applications Support Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
---
# Hoe toepassingen ondersteunen Azure Rights Management
Gebruik de volgende informatie om te zien hoe de eindgebruiker toepassingen (zoals de Office-toepassingen, Word, Excel, PowerPoint en Outlook) en services (zoals Exchange en SharePoint) met de Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] om u te helpen bij het beschermen van uw organisatie:

-   [RMS delen van de toepassing voor Windows en mobiele platforms](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharingAppIntro)

-   [Office-toepassingen: Word, Excel en PowerPoint, Outlook](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_OfficeAppsIntro)

    -   [Exchange Online en Exchange Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_ExchangeIntro)

    -   [SharePoint Online en SharePoint Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharePointIntro)

-   [Bestandsservers waarop Windows Server wordt uitgevoerd en gebruiken van bestand classificatie infrastructuur (FCI)](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_FCIIntro)

-   [Andere toepassingen die ondersteuning voor de RMS APIs](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_APIAppsIntro)

> [!NOTE]
> Om te controleren of de toepassingen en versies die [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) ondersteunt, Zie [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

In sommige gevallen informatiebeveiliging wordt automatisch toegepast, volgens de beleidsregels die u configureert. Dit is bijvoorbeeld het geval met SharePoint-bibliotheken, geclassificeerde bestanden en regels voor het transport van Exchange. In andere gevallen moeten gebruikers toepassen informatie protection zelf van hun toepassingen door een sjabloon te selecteren of door specifieke opties te selecteren. Dit is bijvoorbeeld het geval wanneer gebruikers een bestand via e-mail delen of een bestand ter plekke door beperken van toegang of gebruik voor de geselecteerde gebruikers of gebruikers buiten de organisatie worden beveiligd.

Sjablonen maken het gemakkelijker voor gebruikers (en beheerders die beleid configureren) toe te passen van het juiste niveau van bescherming en beperken van toegang tot de mensen binnen uw organisatie. Hoewel [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] wordt geleverd met twee standaardsjablonen u wilt waarschijnlijk maken van aangepaste sjablonen te verminderen de tijden waarop ze moeten afzonderlijke opgeven. Zie voor meer informatie [Aangepaste sjablonen configureren voor Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

Voor de gevallen waarin gebruikers moeten toepassing informatie protection zelf, moet u te voorzien van deze instructies en richtlijnen hoe en wanneer om dit te doen. De instructies moet specifiek voor de toepassing en versies die worden gebruikt en hoe ze gebruiken en de aanwijzingen voor het wanneer en hoe de toepassing gegevens beveiliging moet worden geschikt voor uw bedrijf. Zie voor meer informatie [Waardoor gebruikers kunnen bestanden beveiligen met Azure Rights Management](../Topic/Helping_Users_to_Protect_Files_by_Using_Azure_Rights_Management.md).

Zie voor meer informatie over het configureren van deze toepassingen voor Azure RMS [Toepassingen voor Azure Rights Management configureren](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

> [!TIP]
> Zie voor voorbeelden en schermafdrukken van toepassingen met Azure RMS het [Azure RMS in actie: Zie welke beheerders en gebruikers](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMSpictures) gedeelte van de [Wat is Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) onderwerp.

## <a name="BKMK_SharingAppIntro"></a>RMS delen van de toepassing voor Windows en mobiele platforms
De RMS-toepassing voor delen is een gratis downloadbare toepassing die is vereist voor de ondersteuning van Office 2010, maar ook aanbevolen voor Windows-computers, Mac-computers en mobiele apparatuur. Een van de voordelen die het algemene beveiliging voor toepassingen en bestanden die geen systeemeigen ondersteuning kunt toepassen is [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], hetgeen betekent dat alle bestanden kunnen worden beveiligd. Zie voor meer informatie over de verschillende protection niveaus, de [niveau van bescherming – systeemeigen en algemene](http://technet.microsoft.com/library/dn339003.aspx) gedeelte van de [delen toepassing Rights Management-beheerdershandleiding](http://technet.microsoft.com/library/dn339003.aspx).

Wanneer gebruikers hun bestanden beveiligen met behulp van de RMS kunnen delen van de toepassing, ze de documenten die ze beschermd bijhouden, en indien nodig, toegang tot deze intrekken. Ze dit doen door de [document bijhouden site](http://go.microsoft.com/fwlink/?LinkId=529562).

Voor Windows-computers, de RMS sharing toepassing onopvallend is geïntegreerd met en verbetert de toepassingen die gebruikers al gebruiken:

-   Een Office-invoegtoepassing voor Word, Excel, PowerPoint en Outlook is geïnstalleerd. Deze manier kunt u gebruikers met een **beveiligd delen** klikt in het lint, dat een eenvoudig te gebruiken dialoogvenster instellingen die het meest worden gebruikt om bestanden wordt te worden gestuurd te beschermen. Deze knop ook kunt u snel toegang tot het document site bijhouden.

-   Een nieuwe met de rechtermuisknop op de optie voor bestand Explorer. Deze manier kunt u gebruikers met een **beveiligen** optie, wordt een eenvoudig te gebruiken dialoogvenster instellingen die het meest worden gebruikt om bestanden opgeslagen op een schijf te beschermen.

-   Een viewer bestanden te openen die zijn beveiligd [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. Deze viewer automatisch wordt aangeroepen als er geen andere toepassing geïnstalleerd waarmee het beveiligde bestand kan worden geopend.

-   Back-end-configuratie voor Office 2010 waarmee Word, Excel, PowerPoint en Outlook van dit pakket naadloos werken met [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Hoewel de RMS-toepassing voor Windows sharing kan worden gedownload en geïnstalleerd voor een computer met behulp van de [pagina Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970), ondersteunt ook een enterprise-implementatie voor een stille installatie en aangepaste configuratie. Voor meer informatie, Zie de volgende bronnen:

-   [Rights Management delen toepassing beheerdershandleiding](http://technet.microsoft.com/library/dn339003.aspx)

-   [Rights Management delen toepassing handleiding](http://technet.microsoft.com/library/dn339006.aspx)

De RMS sharing toepassing voor mobiele apparaten biedt ondersteuning voor de meest gebruikte mobiele apparaten, zoals iPad en iPhone, Android, Windows Phone en Windows Rechth. Gebruikers kunnen deze app downloaden uit de relevante store, en er koppelingen naar deze van de [pagina Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970).

## <a name="BKMK_OfficeAppsIntro"></a>Office-toepassingen: Word, Excel en PowerPoint, Outlook
Deze toepassingen systeemeigen ondersteuning voor Rights Management met information rights management (IRM) en kunnen gebruikers beveiliging toepassen op een opgeslagen document of op een e-mailbericht moet worden verzonden. Gebruikers kunnen sjablonen toepassen of kies zeer aangepaste instellingen voor beperkingen, rechten, en -gebruik. Gebruikers kunnen bijvoorbeeld een bestand configureren zodat deze alleen door mensen in uw organisatie of besturingselement worden geopend of het bestand kan worden bewerkt, tot de alleen-lezen beperkt of voorkomen dat wordt afgedrukt. Voor tijdgebonden bestanden, een verlooptijd kan worden geconfigureerd (rechtstreeks door gebruikers of door een sjabloon) voor wanneer het bestand niet meer toegankelijk zijn. Voor Outlook, gebruikers kunt ook de **niet doorsturen** optie om te voorkomen dat gegevens lekken.

### <a name="BKMK_ExchangeIntro"></a>Exchange Online en Exchange Server
Wanneer u Exchange Online of Exchange Server gebruikt, kunt u informatie rights management (IRM) integratie, met extra informatie protection oplossingen:

-   **Exchange ActiveSync IRM** zodat mobiele apparaten kunnen beveiligen en verbruiken beveiligd e-mailberichten.

-   RMS-ondersteuning voor de **Outlook Web-App**, volgens de Outlook-client op deze manier is geïmplementeerd, zodat gebruikers e-mailberichten beveiligen kunnen door sjablonen of door op te geven van afzonderlijke opties en gebruikers kunnen lezen en gebruiken beveiligd e-mailberichten die aan hen zijn verzonden.

-   **Beveiliging regels** voor Outlook-clients dat een beheerder configureert om toe te passen automatisch RMS-sjablonen voor e-mailberichten voor de opgegeven geadresseerden. Bijvoorbeeld, wanneer interne e-mailberichten worden verzonden naar uw juridische afdeling, ze kunnen alleen worden gelezen door leden van de juridische afdeling en kunnen niet worden doorgestuurd. Gebruikers zien de beveiliging toegepast op de e-mailbericht voordat u deze en standaard ze kunnen verwijderen als ze besluit is niet nodig. E-mailberichten worden versleuteld voordat ze worden verzonden. Zie voor meer informatie [Outlook beveiliging regels](http://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) en [maken van een regel voor de beveiliging Outlook](http://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) in de Exchange-bibliotheek.

-   **Regels transport** dat een beheerder configureert om automatisch RMS sjablonen toepassen op e-mailbericht berichten op basis van eigenschappen zoals afzender, geadresseerde berichtonderwerp en inhoud. Deze lijken in concept aan beveiliging regels, maar kunnen gebruikers geen verwijderen van de beveiliging, kunnen worden toegepast op de Outlook Web Access en e-mailberichten verzonden door de mobiele apparaten en e-mailberichten niet coderen voordat deze worden verzonden vanaf de client. Zie voor meer informatie [Maak een regel Transport beveiliging](http://technet.microsoft.com/library/dd302432.aspx) in de Exchange-bibliotheek.

-   **Beleid voor gegevensverlies te voorkomen (DLP)** die sets voorwaarden voor het filteren van e-mailberichten bevatten en actie ondernemen om te voorkomen dat verlies van gegevens voor vertrouwelijke of gevoelige inhoud (bijvoorbeeld persoonlijke gegevens of creditcardgegevens). Tips beleid kunnen worden gebruikt wanneer gevoelige gegevens aan gebruikers die ze nodig hebben mogelijk om toe te passen van de beveiliging van gegevens, op basis van de informatie in het e-mailbericht wordt gedetecteerd. Zie voor meer informatie [gegevensverlies voorkomen](http://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) in de Exchange-bibliotheek.

-   **Office 365 codering** dat gebruikt regels transport voor het versleutelde e-mailberichten verzenden naar mensen buiten uw bedrijf en het e-mailbericht in een browser met een interface lijkt op de Outlook Web-App wordt gelezen. U kunt aanpassen van de afwijzing tekst en koptekst in uw bedrijf versleutelde e-mailberichten en zelfs uw bedrijfslogo toevoegen. Zie voor meer informatie [Office 365 codering](http://office.microsoft.com/o365-message-encryption-FX104179182.aspx) van de Office-website.

Als u Exchange Server gebruikt, kunt u de functies van de beveiliging information met [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] door het implementeren van de RMS-connector die fungeert als een relay tussen uw lokale servers en de cloud-RMS-service. Zie voor meer informatie [Implementatie van de Connector van de Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

### <a name="BKMK_SharePointIntro"></a>SharePoint Online en SharePoint Server
Wanneer u SharePoint Online- of SharePoint Server gebruikt, kunt u informatie over integratie rights management (IRM) waarmee beheerders beveiligen lijsten of bibliotheken zodat wanneer een gebruiker controles uit een document, het bestand is beveiligd zodat alleen gemachtigde personen kunt weergeven en gebruiken van het bestand op basis van het beleid voor documentbeheer beveiliging die u opgeeft. Bijvoorbeeld, kan het bestand alleen-lezen, het kopiëren van tekst uitschakelen te voorkomen dat een lokale kopie en te voorkomen dat het bestand afdrukken.

Beveiliging van gegevens wordt altijd voor lijsten en bibliotheken toegepast door een beheerder nooit een eindgebruiker. En wordt toegepast op het niveau van de lijst of bibliotheek voor alle documenten in die container in plaats van op afzonderlijke bestanden.  Als u SharePoint Online, kunnen gebruikers ook IRM toepassen op hun OneDrive voor Business-bibliotheek.

De IRM-service moet eerst worden ingeschakeld voor SharePoint. Geef vervolgens Information Rights Management voor een bibliotheek. In het geval van SharePoint Online en OneDrive voor zakelijke kunnen gebruikers ook opgeven Information Rights Management voor hun OneDrive voor Business-bibliotheek. SharePoint gebruikt geen rechtenbeleidssjablonen, maar er zijn SharePoint configuratie-instellingen die u kunt selecteren die nauw overeenkomen met de instellingen die u kunt in sjablonen opgeven.

Als u SharePoint-Server gebruikt, kunt u de functies van de beveiliging information met [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] door het implementeren van de RMS-connector die fungeert als een relay tussen uw lokale servers en de cloud-RMS-service. Zie voor meer informatie [Implementatie van de Connector van de Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

> [!NOTE]
> Er zijn enkele beperkingen wanneer u IRM met SharePoint gebruiken:
> 
> -   U kunt de standaard of aangepaste sjablonen die u in de Azure-portal beheren niet gebruiken.
> -   Bestanden met een. De bestandsnaamextensie PPDF voor beveiligde PDF-bestanden worden niet ondersteund. Bestanden die zijn. PDF-bestandsextensie en die zijn standaard beveiligd door RMS worden ondersteund wanneer u een PDF-reader die RMS ondersteunt.
> -   Omdat Office op mobiele apparaten biedt nog geen ondersteuning voor RMS, moeten deze apparaten een browser gebruiken die zijn beveiligd met RMS-bestanden bekijken en de bestanden zijn alleen-lezen.

Azure RMS past gebruiksbeperkingen en gegevensversleuteling voor documenten wanneer ze worden gedownload van SharePoint en niet wanneer het document eerst gemaakt in de SharePoint- of geüpload naar de bibliotheek. Zie voor meer informatie over hoe documenten worden beschermd voordat ze worden gedownload [gegevensversleuteling in OneDrive voor bedrijfs- en SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) uit de SharePoint-documentatie.

Zie het volgende bericht van de Office-blog voor meer informatie over het gebruik van Azure met SharePoint: [Wat is er nieuw met Information Rights Management in SharePoint en SharePoint Online](http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

## <a name="BKMK_FCIIntro"></a>Bestandsservers waarop Windows Server wordt uitgevoerd en gebruiken van bestand classificatie infrastructuur (FCI)
Bij het configureren van Windows Server-bestand classificatie infrastructuur gebruiken, kan deze functie Bestandsserverbronbeheer scan van lokale bestanden en bepalen of ze gevoelige gegevens bevatten. Om de bestanden die voldoen aan deze criteria, worden ze gemarkeerd met classificatie-eigenschappen waarmee een beheerder worden gedefinieerd. Het bestand classificatie-infrastructuur kunnen dan automatische actie ondernemen volgens de indeling. Een van deze acties bevatten informatie over beveiliging toepassen met behulp van [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] en de implementatie van de connector Rights Management (ook wel bekend als de RMS-connector). Office-bestanden worden vervolgens automatisch door Azure RMS beveiligde.

Ter bescherming van alle bestandstypen u zou niet worden gebruikt voor de RMS-connector, maar in plaats daarvan een Windows PowerShell-script uitvoeren, met cmdlets van de [RMS Protection hulpprogramma](https://www.microsoft.com/en-us/download/details.aspx?id=47256).

Het beleid classificatie zijn volledig worden geconfigureerd en sterk uitbreidbare zodat u voorkomen potentiële gegevens het lekken van niet-geautoriseerde en gemachtigde gebruikers dat kunt. Dit kan zelfs helpen te verminderen het risico van het lekken van gegevens door netwerkbeheerders omdat u kunt beleidsregels waarvoor deze beheerders hebben toegang tot de bestanden niet configureren.

Zie voor instructies voor het implementeren en configureren van de RMS-connector voor Office-bestanden [Implementatie van de Connector van de Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

Zie voor instructies voor het Windows PowerShell-script gebruikt voor alle bestandstypen, [RMS-beveiliging met Windows Server-bestand classificatie netwerkinfrastructuur &#40;FCI&#41;](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

## <a name="BKMK_APIAppsIntro"></a>Andere toepassingen die ondersteuning voor de RMS APIs
Met behulp van de RMS SDK uw interne kunnen ontwikkelaars line-of-business-toepassingen standaard ondersteund [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Hoe de beveiliging van gegevens is geïntegreerd met deze toepassingen is afhankelijk van hoe ze worden geschreven. Bijvoorbeeld, de integratie mogelijk automatisch worden toegepast met minimale gebruikersinteractie vereist of voor een meer aangepaste ervaring gebruikers mogelijk gevraagd om te configureren voor beveiliging van gegevens van toepassing op bestanden. Zie voor meer informatie over de SDK, de [Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

Veel leveranciers bieden op deze manier toepassingen om informatie te verstrekken oplossingen voor beveiliging, ook wel bekend als enterprise rights management (ERM) producten. Een populaire voorbeeld is een PDF-reader ondersteunt [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] voor specifieke platforms. U kunt de tabel in de [Client-apparaatmogelijkheden](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities) sectie van de [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) onderwerp toepassingen identificeren die ondersteuning voor RMS (toepassingen RMS enlightened) en vervolgens met een zoekactie aanschaffen of downloaden van de toepassing.

> [!TIP]
> Raadpleeg voor recent uitgebrachte toepassingen RMS community kanalen, zoals vermeld in [Informatie en ondersteuning voor Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## Zie ook
[Aan de slag met Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

