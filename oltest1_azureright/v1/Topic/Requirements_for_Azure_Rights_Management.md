---
description: na
keywords: na
title: Requirements for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
---
# Vereisten voor Azure Rights Management
Zorg ervoor dat u de volgende vereisten hebt voor de implementatie van Microsoft Azure Rights Management (Azure RMS) in uw organisatie. U kunt de [Azure Rights Management-implementatieschema](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) Rights Management implementeren voor uw organisatie.

|Vereiste|Meer informatie|
|------------|-------------------|
|Een cloud-abonnement voor RMS|Uw organisatie moet een cloud-abonnement biedt ondersteuning voor RMS hebben.<br /><br />Voor informatie over licenties, Zie de [Cloud-abonnementen die ondersteuning van Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) in dit onderwerp.|
|Azure AD-map|Uw organisatie moet een Azure AD-map voor de verificatie van de gebruiker ondersteuning voor RMS hebben. Als u uw gebruikersaccounts van uw on-premises directory (AD DS) gebruiken wilt, moet u bovendien ook Active directory-integratie configureren.<br /><br />Multi-factorauthenticatie (MFA) wordt ondersteund met Azure RMS wanneer u de vereiste clientsoftware en correct geconfigureerde ondersteunende MFA-infrastructuur hebt.<br /><br />Zie voor meer informatie de [Azure AD-map](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_AzureADTenant) in dit onderwerp.|
|Clientapparaten|Gebruikers hebben een clientapparaten (computer of een mobiel apparaat) met een besturingssysteem dat RMS ondersteunt.<br /><br />Zie voor meer informatie de [Clientapparaten die ondersteuning van Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices) in dit onderwerp.|
|Toepassingen|Gebruikers moeten toepassingen die ondersteuning bieden voor RMS uitvoeren.<br /><br />Zie voor meer informatie de [Toepassingen die ondersteuning van Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) in dit onderwerp.|
|Infrastructuur die verbinding met het Internet en afhankelijke cloudservices ondersteunt|Als er een firewall of een vergelijkbare betrokken zijn netwerkapparaten die moeten worden geconfigureerd om te zien, specifieke verbindingen toe [Office 356 URL's en IP-adresbereiken](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />De lijst met URL's en IP-adressen in het **Office 356 portal en identiteit** sectie van toepassing op de Office 365-portal, Azure Active Directory-bronnen en Azure Rights Management. Volg de instructies in dit artikel om up-to-date te houden met wijzigingen in deze informatie met een abonnement op een RSS-feed.<br /><br />Naast de gegevens in het Office-artikel specifiek voor Azure RMS:<br /><br />-   Eindigt niet het TLS-clientservice-verbinding (bijvoorbeeld te doen pakket niveau controle). Hierdoor kunt u het certificaat dat clients met RMS met Microsoft beheerde CA's gebruiken te beveiligen de communicatie met Azure RMS vastzetten.<br />-   Gebruik een webproxyconfiguratie waarmee wordt geverifieerd namens een gebruiker niet.|

Als u gebruiken Azure RMS met lokale servers wilt, worden de volgende producten worden ondersteund:

-   Exchange-Server

-   SharePoint-Server

-   Windows Server-bestandsservers die ondersteuning bieden voor bestand classificatie infrastructuur

Zie voor meer informatie over de aanvullende Azure RMS-vereisten voor dit scenario de [Servers die ondersteuning van Azure RMS lokaal](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedServers) in dit onderwerp.

> [!IMPORTANT]
> Het volgende scenario wordt niet ondersteund:
> 
> -   AD RMS en Azure RMS naast elkaar in dezelfde organisatie, met uitzondering van tijdens de migratie wordt uitgevoerd zoals beschreven in [Migratie van AD RMS naar Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).
> 
> Er is een migratiepad ondersteunde [van AD RMS naar Azure RMS](http://technet.microsoft.com/library/Dn858447.aspx), en uit [Azure RMS naar AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Als u Azure RMS implementeren en vervolgens besluit dat u niet meer wilt gebruiken deze cloudservice, raadpleegt u [Buiten gebruik stellen en Azure Rights Management deactiveren](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

Gebruik de volgende secties voor meer informatie over de Azure RMS-vereisten.

## <a name="BKMK_SupportedSubscriptions"></a>Cloud-abonnementen die ondersteuning van Azure RMS
Voor gebruik van Azure RMS moet van uw organisatie ten minste één van de volgende abonnementen met een voldoende aantal licenties voor gebruikers en services die bestanden beveiligen en e-mailberichten. Als u een service die van toepassing zijn beveiliging voor gebruikers (eigenaars van de bestanden of e-mailberichten), moeten deze gebruikers een van deze licenties. Gebruikers die alleen wordt gebruiken (bijvoorbeeld lezen en bewerken) deze beveiligde gegevens niet een licentie nodig.

-   Office 365

-   Azure Rights Management Premium (voorheen Azure RMS zelfstandig)

-   Enterprise mobiliteit Suite

-   RMS voor personen

Gebruik de volgende secties voor meer informatie en meld u aan opties.

Zie voor een licentie vergelijking van de Azure RMS-mogelijkheden voor de betaalde abonnementen [aanbiedingen voor vergelijking van Rights Management Services (RMS)](http://technet.microsoft.com/dn858608).

### Office 365-abonnement
[Gratis proefversie van 30 dagen: Enterprise E3](http://go.microsoft.com/fwlink/p/?LinkID=403802)

Dit abonnement is ontworpen voor organisaties die u wilt gebruiken de Office online services en hun Information Rights Management-functie die gebruikmaakt van Azure RMS te gebruiken. Niet alle Office 365-abonnementen bevatten echter Azure RMS.

|Optie-Licentieverlening|Office 365-bedrijfsfuncties|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 onderwijs A1|Office 365 Enterprise E3<br /><br />Office 365 onderwijs A3<br /><br />Office 365 overheid G3|Office 365 Enterprise e 4<br /><br />Office 365 onderwijs A4<br /><br />Office 365 overheid G4|Office 365 Enterprise K1|SharePoint Plan 1<br />SharePoint Plan 2|Exchange Online Plan 1<br />Exchange Online Plan 2|
|---------------------------|-------------------------------|-------------------------------|-------------------------------------------------------|---------------------------------------------------------------------------------|----------------------------------------------------------------------------------|----------------------------|----------------------------------------|--------------------------------------------------|
|Information Rights Protection (IRM)|Nee|Nee|Nee|Ja|Ja|Nee|Nee|Nee|

### Azure Rights Management Premium-abonnement
[Gratis proefversie van 30 dagen](https://portal.microsoftonline.com/Signup/MainSignUp15.aspx?&amp;OfferId=A43415D3-404C-4df3-B31B-AAD28118A778&amp;dl=RIGHTSMANAGEMENT&amp;ali=1)

Dit abonnement was voorheen bekend als Azure RMS zelfstandige en is bedoeld voor organisaties die u wilt gebruiken Azure RMS maar geen abonnement met Azure RMS. Bijvoorbeeld, hebt u een abonnement voor Office 365 Business Essentials of Office 365 Enterprise E1, deze abonnementen geen Azure RMS (Zie de tabel in de vorige sectie). Voor gebruik van Azure RMS u een abonnement voor Azure Rights Management Premium (of een ander abonnement, zoals Office 365 Enterprise e 4, waarin Azure RMS).

Zie voor meer informatie [Microsoft Azure Rights Management](http://products.office.com/business/microsoft-azure-rights-management).

Dit abonnement biedt tevens een evaluatieperiode voor u Azure RMS voor 25 gebruikers gratis uitproberen. Als het abonnement is verlopen voordat u een vervanging-abonnement aanschaffen, raadpleegt u de volgende sectie "Wat gebeurt er wanneer de proefabonnement verloopt?"

|Optie-Licentieverlening|Office 365-bedrijfsfuncties|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 onderwijs A1|Office 365 Enterprise E3<br /><br />Office 365 onderwijs A3<br /><br />Office 365 overheid G3|Office 365 Enterprise e 4<br /><br />Office 365 onderwijs A4<br /><br />Office 365 overheid G4|Office 365 Enterprise K1|SharePoint Plan 1<br />SharePoint Plan 2|Exchange Online Plan 1<br />Exchange Online Plan 2|
|---------------------------|-------------------------------|-------------------------------|-------------------------------------------------------|---------------------------------------------------------------------------------|----------------------------------------------------------------------------------|----------------------------|----------------------------------------|--------------------------------------------------|
|Information Rights Protection (IRM)|Ja|Yes <sup>1</sup>|Ja|Ja|Ja|Ja|Ja|Ja|
<sup>1</sup> voor Business Premium zijn enkele beperkingen client: U kunt inhoud beveiligen en gebruiken van beveiligde inhoud met RMS met behulp van de Outlook Web-App en de app RMS sharing. U kunt beveiligde inhoud met behulp van alle andere Office-toepassingen, inclusief Office Online en de clienttoepassingen voor Office 365 Business Premium verbruiken.

#### <a name="BKMK_TrialExpiryBehavior"></a>Wat gebeurt er wanneer de proefabonnement verloopt?
Als uw proefabonnement is verlopen, verliest u toegang tot inhoud die is beveiligd met behulp van uw proefabonnement voor Azure RMS. Als u vervolgens een abonnement dat Azure RMS ondersteunt, wordt toegang echter automatisch hersteld.

Een uitzondering toegang meer hebt na het verstrijken is als uw organisatie Azure RMS met de RMS voor personen abonnement gebruikt voordat u het proefabonnement verkregen. Vervolgens toegang tot eerder beveiligde inhoud blijft, zelfs nadat de evaluatieversie abonnement is verlopen.

### Enterprise mobiliteit Suite-abonnement
[Gratis proefversie van 30 dagen](http://go.microsoft.com/fwlink/?LinkId=615385)

Dit abonnement is ontworpen voor organisaties die willen gebruiken om een combinatie van Azure Active Directory Premium, Windows Intune en Azure Rights Management. Zie voor meer informatie de [overzicht van Microsoft Enterprise mobiliteit](http://go.microsoft.com/fwlink/?LinkId=615386).

|Optie-Licentieverlening|Office 365-bedrijfsfuncties|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 onderwijs A1|Office 365 Enterprise E3<br /><br />Office 365 onderwijs A3<br /><br />Office 365 overheid G3|Office 365 Enterprise e 4<br /><br />Office 365 onderwijs A4<br /><br />Office 365 overheid G4|Office 365 Enterprise K1|SharePoint Plan 1<br />SharePoint Plan 2|Exchange Online Plan 1<br />Exchange Online Plan 2|
|---------------------------|-------------------------------|-------------------------------|-------------------------------------------------------|---------------------------------------------------------------------------------|----------------------------------------------------------------------------------|----------------------------|----------------------------------------|--------------------------------------------------|
|Information Rights Protection (IRM)|Ja|Yes <sup>1</sup>|Ja|Ja|Ja|Ja|Ja|Ja|
<sup>1</sup> voor Business Premium zijn enkele beperkingen client: U kunt inhoud beveiligen en gebruiken van beveiligde inhoud met RMS met behulp van de Outlook Web-App en de app RMS sharing. U kunt beveiligde inhoud met behulp van alle andere Office-toepassingen, inclusief Office Online en de clienttoepassingen voor Office 365 Business Premium verbruiken.

### RMS voor personen-abonnement
Dit abonnement is ontworpen voor personen in een organisatie die nog niet geïmplementeerd Azure RMS of AD RMS. Kunnen deze mensen inhoud die is beveiligd door een organisatie die van Azure RMS gebruikmaakt lezen en ze kunnen ook hun eigen inhoud beveiligen.

Zie voor meer informatie [RMS voor personen en Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## <a name="BKMK_AzureADTenant"></a>Azure AD-map
U hebt een map Azure AD RMS Azure gebruiken. U uw account organisatie voor deze map gebruiken voor aanmelding bij de Azure-beheerportal, waar, bijvoorbeeld, kunt u configureren en beheren Rights Management-sjablonen.

Als u geen Azure-abonnement niet al voor uw organisatie hebt, kunt u een door u zich aanmeldt voor een gratis proefversie downloaden.: Ga naar de [Azure ophalen gestart](https://account.windowsazure.com/organization) pagina en volg de instructies.

Zie de volgende bronnen in de Azure Active Directory-documentatie voor meer informatie:

-   [Wat is een Azure AD-directory?](http://msdn.microsoft.com/en-us/library/185da266-58a9-43e6-9c66-2c8f702545c6)

-   [Hoe de Azure-abonnementen zijn gekoppeld aan Azure AD](http://msdn.microsoft.com/en-us/library/edf05c2e-944a-4da5-a330-dc9dc479f127)

Als u wilt dat uw Azure AD-directory integreren met uw lokale AD forests, Zie [Active Directory-integratie](http://msdn.microsoft.com/en-us/library/bf82bdff-2467-403b-8c1a-0e9eebcf31e8).

> [!NOTE]
> Als u mobiele apparaten of Mac-computers die lokaal worden geverifieerd door AD FS of een equivalente verificatieprovider:
> 
> -   U moet gebruikmaken van AD FS op de minimale serverversie van **Windows Server 2012 R2**, of een alternatieve verificatieprovider die het protocol OAuth 2.0 ondersteunt.

### <a name="BKMK_MFA"></a>Multi-factorauthenticatie (MFA) en Azure RMS
Voor het gebruik van multi-factor moet authentication (MFA) met Azure RMS ten minste één van de volgende:

-   Office 2013 (minimumversie):

    -   Als u Office 2013 hebt, moet u ook installeren de [9 juni 2015 bijwerken voor Office 2013 (KB3054853)](https://support.microsoft.com/kb/3054853). Voor meer informatie over deze update en hoe moderne verificatie, op basis van Active Directory-verificatie bibliotheek ADAL teken Office 2013 wordt, Zie [Office 2013 moderne verificatie openbare preview aangekondigd](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/)  op de Office-blog.

-   Rights Management-toepassing voor Windows delen:

    -   U moet minimaal de versie van 1.0.1908.0, kunnen worden bevestigd met behulp van het Configuratiescherm, programma's en onderdelen hebt geïnstalleerd. Zie voor meer informatie over het delen toepassing  [Rights Management-toepassing voor Windows delen](../Topic/Rights_Management_Sharing_Application_for_Windows.md).

-   Rights Management-app voor mobiele apparaten en Mac-computers delen:

    -   Zorg ervoor dat u hebt de meest recente versie geïnstalleerd. MFA-ondersteuning is een fout bij de release September 2015 van de app RMS sharing.

Stel uw MFA-oplossing:

-   Microsoft beheerde tenants (hebt u Azure Active Directory of Office 365):

    -   Configureer de MFA Azure om af te dwingen MFA voor gebruikers. Zie voor instructies [aan de slag met Azure multi-factor Authentication in de cloud](https://azure.microsoft.com/documentation/articles/multi-factor-authentication-get-started-cloud/) van de documentatie van Azure.

        Zie voor meer informatie over Azure MFA [Wat is Azure multi-Factorauthenticatie?](https://azure.microsoft.com/documentation/articles/multi-factor-authentication/)

-   Federatieve tenants (u werkt federation-servers op de lokale):

    -   De federatieservers configureren voor Azure Active Directory of Office 365. Bijvoorbeeld als u van AD FS gebruikmaakt, Zie [aanvullende verificatiemethoden configureren voor AD FS](https://technet.microsoft.com/library/dn758113.aspx) op TechNet.

        Zie voor meer informatie over dit scenario  [het werken met Office 365-identiteit programma nu gestroomlijnde](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) op de Office-blog.

## <a name="BKMK_SupportedDevices"></a>Clientapparaten die ondersteuning van Azure RMS
De volgende secties gebruiken om te bepalen welke apparaten Azure RMS (Rights Management), ondersteuning en welke RMS-mogelijkheden die worden ondersteund:

-   [Computers](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedComputers)

-   [Mobiele apparaten](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedMobileDevices)

-   [Client-apparaatmogelijkheden](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities)

### <a name="BKMK_RMSSupportedComputers"></a>Computers
De volgende besturingssystemen ondersteunen Azure Rights Management:

-   **Windows 7** (x 86, x 64)

-   **Windows 8** (x 86, x 64)

-   **Windows 8.1** (x 86, x 64)

-   **Windows 10** (x 86, x 64)

-   **Mac OS X**: Minimumversie van Mac OS X 10,8 (Mountain Lion)

### <a name="BKMK_RMSSupportedMobileDevices"></a>Mobiele apparaten
De volgende besturingssystemen voor mobiele apparaten ondersteunen Azure Rights Management:

-   **Windows Phone**: Windows Phone 8.1

-   **Android telefoons en tablets**: Minimumversie van Android 4.0.3

-   **iPhone en iPad**: Minimumversie van iOS 7.0

-   **Windows RT tablets**: Windows 8 RT, Windows 8.1 RT

### <a name="BKMK_ClientCapabilities"></a>Client-apparaatmogelijkheden
Niet alle ondersteunde clientapparaten ondersteuning momenteel voor alle RMS-mogelijkheden. Gebruik de volgende tabel om te bepalen welke toepassingen ondersteunen de RMS-mogelijkheden en de uitzonderingen.

Tenzij anders vermeld, zijn de ondersteunde mogelijkheden van toepassing op Azure RMS en AD RMS. Bovendien AD RMS-ondersteuning voor iOS, Android, OS X en Windows Phone 8.1 vereist [Active Directory Rights Management Services mobiele apparaat extensie](http://technet.microsoft.com/library/a69ead9d-7dd3-4b38-9830-4728e9757341).

Informatie over de tabelkolommen:

-   **PDF beveiligd**: Bestanden die extensie .ppdf hebben en die automatisch worden gemaakt wanneer u de RMS sharing toepassing gebruiken voor het delen van bestanden van Office en PDF-bestanden per e-mail. De RMS-toepassing voor delen bevat een lezer voor beveiligde PDF-bestanden. Eerder, als u PDF-bestanden die u met behulp van Azure RMS of AD RMS beveiligde gemaakt, kunt u blijven deze bestanden op Windows, iOS en Android-apparaten met behulp van Foxit lezer en Nitro Pro lezen.

-   **E-mailadres:** De e-clients die worden vermeld kunnen de e-mailbericht zelf, die wordt automatisch elke bijgevoegde bestanden worden beveiligd worden beveiligd. In dit scenario weergegeven functie van de client de beveiligde inhoud (bericht en bijlage) voor geautoriseerde ontvangers. Als een e-mailbericht zelf is niet beveiligd, maar de bijlage is beveiligd, weergeven niet met de functie van de client preview echter de beveiligde bijlage naar geautoriseerde ontvangers.

-   **Andere bestandstypen**: Tekst en afbeeldingsbestanden bevatten bestanden met de extensie zoals .txt, .xml, JPG, jpeg en. Deze bestanden de bestandsnaamextensie wijzigen nadat ze systeemeigen worden beschermd door RMS en worden alleen-lezen. Bestanden die systeemeigen kunnen niet worden beveiligd hebben extensie .pfile nadat deze RMS generieke zijn beveiligd. Zie voor meer informatie de [beschermingsniveau – systeemeigen en algemene](https://technet.microsoft.com/library/dn339003.aspx) en [ondersteunde bestandstypen en extensies](https://technet.microsoft.com/library/dn339003.aspx) secties van de [delen toepassing Rights Management-beheerdershandleiding](http://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx).

|**Besturingssysteem apparaat**|Word, Excel en PowerPoint|Beveiligde PDF-bestand|E-mailbericht|Andere bestandstypen|
|----------------------------------|-----------------------------|--------------------------|-----------------|------------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Mobiele apps voor Office (alleen Azure RMS)<sup>1</sup><br /><br />Office Online<sup>2</sup>|Gaaiho Doc<br /><br />GigaTrust Desktop PDF-Client voor Adobe<br /><br />Foxit lezer<br /><br />Nitro PDF-Reader<br /><br />RMS delen app|Outlook 2010<br /><br />Outlook 2013<br /><br />Outlook Web-App (OWA)<br /><br />Windows Mail<sup>3</sup>|RMS delen van de toepassing voor Windows: Tekst, afbeeldingen, pfile<br /><br />Siemens JT2Go: JT-bestanden (alleen Windows-10)|
|**iOS**|Office voor iPad en iPhone<sup>4</sup><br /><br />Office Online<sup>2</sup><br /><br />TITUS documenten|Foxit lezer<br /><br />App RMS sharing<sup>1</sup><br /><br />TITUS documenten|NitroDesk<br /><br />Outlook voor iPad en iPhone<sup>3</sup><br /><br />OWA voor iOS<br /><br />Secure eilanden IQProtector<sup>1</sup><br /><br />TITUS Mail|App RMS sharing<sup>1</sup>: Tekst, afbeeldingen, pfile<br /><br />TITUS documenten: Pfile|
|**Android**|GigaTrust App voor Android<br /><br />Office Online<sup>2</sup>|GigaTrust App voor Android<br /><br />Foxit lezer<br /><br />App RMS sharing<sup>1</sup>|9Folders<br /><br />GigaTrust App voor Android<br /><br />NitroDesk<br /><br />OWA voor Android<sup>5</sup><br /><br />Samsung E-mail (S3 en hoger)<br /><br />Secure eilanden IQProtector<sup>1</sup><br /><br />TITUS classificatie voor mobiel|App RMS sharing<sup>1</sup>: Tekst, afbeeldingen, pfile|
|**OS X**|Office 2011 (alleen AD RMS)<br /><br />2016 Office voor Mac<br /><br />Office Online<sup>2</sup>|Foxit lezer<br /><br />App RMS sharing<sup>1</sup>|Outlook 2011 (alleen AD RMS)<br /><br />Outlook 2016 voor Mac<br /><br />Outlook voor Mac|App RMS sharing<sup>1</sup>: Tekst, afbeeldingen, pfile|
|**Windows RT**|Office 2013 RT<br /><br />Office Online<sup>2</sup>|Niet ondersteund|Outlook 2013 RT<br /><br />Mail-app voor Windows<br /><br />Windows Mail<sup>3</sup>|Siemens JT2Go: JT-bestanden|
|**Windows Phone 8.1**|Office Mobile (alleen AD RMS)|App RMS sharing<sup>1</sup>|Outlook Mobile|App RMS sharing<sup>1</sup>: Tekst, afbeeldingen, pfile|
|**BlackBerry 10**|Niet ondersteund|Niet ondersteund|BlackBerry e<sup>3</sup>|Niet ondersteund|
<sup>1</sup> biedt ondersteuning voor beveiligde inhoud te bekijken.

<sup>2</sup> ondersteunt beveiligde inhoud in SharePoint Online, OneDrive voor bedrijfs- en Outlook Web Access bekijken.

<sup>3</sup> maakt gebruik van Exchange ActiveSync IRM, die moet worden ingeschakeld door de Exchange-beheerder. Gebruikers kunnen bekijken, reageren en beantwoord dat alle voor beveiligde e-mailberichten, maar gebruikers nieuwe e-mailberichten zelf kan niet worden beveiligd.

<sup>4</sup> ondersteunt weergeven en bewerken van beveiligde documenten. Voor meer informatie raadpleegt u het volgende bericht op de Office-blog: [Ondersteuning van Azure Rights Management wordt geleverd op Office voor iPad en iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/)

<sup>5</sup> voor meer informatie, raadpleegt u het volgende bericht op de Office-blog: [OWA voor Android nu beschikbaar voor select-apparaten](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/)

> [!TIP]
> Zie het volgende bericht van de Office-blog voor meer informatie over de komende RMS-ondersteuning in Office voor verschillende platforms: [Office overal, overal codering](http://blogs.office.com/2015/02/18/office-everywhere-encryption-everywhere/)

## <a name="BKMK_SupportedApplications"></a>Toepassingen die ondersteuning van Azure RMS
De volgende toepassingen ondersteund standaard Azure RMS, wat betekent dat RMS is nauw geïntegreerd in deze toepassingen met behulp van RMS APIs ter ondersteuning van gebruiksbeperkingen. Deze toepassingen zijn ook bekend als RMS-enlightened:

-   **Microsoft Office-toepassingen** (Word, Excel, PowerPoint en Outlook) van de volgende pakketten kunt inhoud beveiligen door Azure RMS:

    -   Office 365 ProPlus

    -   Office 365 Enterprise E3

    -   Office 365 Enterprise e 4

    -   Office Professional Plus 2016

    -   Office Professional Plus 2013

    -   Office Professional Plus 2010

    Andere edities van Office (met uitzondering van Office 2007) kunnen gebruikmaken van beveiligde inhoud.

    > [!NOTE]
    > Azure RMS met Office Professional Plus 2010 of Office Professional 2010:
    > 
    > -   Is vereist voor het delen van toepassingen voor Windows Rights Management
    > -   Niet ondersteund op Windows 10

-   **Delen van de toepassing voor Windows Rights Management**

    Zie voor meer informatie over het delen Rights Management-toepassing voor Windows de volgende bronnen:

    -   [Rights Management delen toepassing beheerdershandleiding](http://technet.microsoft.com/library/dn339003.aspx)

    -   [Rights Management delen toepassing handleiding](http://technet.microsoft.com/library/dn339006.aspx)

-   **De Rights Management-toepassing voor mobiele platforms delen**

    Zie de volgende bronnen voor meer informatie over de delen Rights Management-toepassing voor mobiele platforms:

    -   De relevante app downloaden via de koppelingen in de [pagina Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970)

    -   Als u mobiele apparaten met Microsoft Intune beheren, u kunt implementeren en configureren van de app op [iOS en Android-apparaten als een beleid beheerd app](https://technet.microsoft.com/library/dn878026.aspx).

    -   [Veelgestelde vragen over Microsoft Rights Management-toepassing voor mobiele Platforms delen](http://technet.microsoft.com/dn451248)

-   **Andere toepassingen die ondersteuning voor de RMS APIs**:

    -   Line-of-business-toepassingen die intern zijn geschreven met behulp van de RMS-SDK

    -   Toepassingen van softwareleveranciers die zijn geschreven met behulp van de RMS-SDK

    Zie voor meer informatie over de SDK, de [Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

> [!IMPORTANT]
> De volgende toepassingen worden momenteel niet ondersteund door Azure RMS:
> 
> -   Microsoft Office voor Mac 2011
> -   Microsoft OneDrive voor zakelijke voor SharePoint Server 2013
> -   XPS-Viewer
> 
> De RMS sharing toepassing heeft bovendien de volgende beperkingen:
> 
> -   Voor Windows-computers: Vereist een minimale versie van Windows 7 Service Pack 1

Zie voor meer informatie over hoe deze toepassingen Azure RMS ondersteunen, [Hoe toepassingen ondersteunen Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

Zie voor meer informatie over het configureren van deze [Toepassingen voor Azure Rights Management configureren](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

## <a name="BKMK_SupportedServers"></a>Servers die ondersteuning van Azure RMS lokaal
De volgende lokale serverproducten worden ondersteund met Azure RMS wanneer u de Azure RMS-connector die als een communicatie-interface (relay) tussen de lokale servers en Azure RMS fungeert gebruikt. Deze configuratie is bovendien vereist tussen uw Active Directory-forest en Azure Active Directory directory-synchronisatie te configureren.

-   **Exchange Server**:

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **File servers waarop Windows Server wordt uitgevoerd en gebruiken van bestand classificatie infrastructuur (FCI)**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Omdat bestandsservers waarop Windows Server 2008 R2 een ingebouwde bestand management taak toe te passen actie RMS beveiliging niet hebt, kunt u de RMS-connector voor dit scenario. Echter, kunt u bestand classificatie infrastructuur en Azure RMS op deze besturingssystemen als u een taak voor het beheer van aangepaste-bestand voor uitvoering van een uitvoerbaar bestand of een script dat u bestanden beveiligen kunt door Azure RMS configureren. Bijvoorbeeld een Windows PowerShell-script dat gebruikmaakt van de [RMS Protection cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx).
    > 
    > U kunt deze cmdlets ook gebruiken met servers met nieuwere versies van Windows Server met het voordeel dat deze cmdlets alle bestandstypen kunt beveiligen. De RMS-connector beschermen Office-bestanden. Zie voor instructies instructies [RMS-beveiliging met Windows Server-bestand classificatie netwerkinfrastructuur &#40;FCI&#41;](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

De RMS-connector wordt ondersteund op Windows Server 2012 R2, Windows Server 2012 en Windows Server 2008 R2.

Zie voor meer informatie over het configureren van de RMS-connector voor deze servers lokale [Implementatie van de Connector van de Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Zie ook
[Aan de slag met Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

