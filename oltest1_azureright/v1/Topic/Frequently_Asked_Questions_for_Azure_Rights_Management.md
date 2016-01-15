---
description: na
keywords: na
title: Frequently Asked Questions for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
---
# Veelgestelde vragen voor Azure Rights Management
Sommige Veelgestelde vragen over Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], ook wel Azure RMS:

## Wat moet ik Azure RMS implementeren en hoe ik te beginnen?
Controleer eerst, [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md), die informatie over de opties cloud-abonnement is, hoe u kunt uw lokale servers met Azure RMS welke implementatiescenario's momenteel niet zijn ondersteund, welke apparaten en toepassingen ondersteuning Azure RMS en een koppeling als u een lijst met IP-adressen en domeinnamen voor firewalls of proxy-servers. U kunt ook controleren van de andere onderwerpen de [Aan de slag met Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md) sectie om inzicht van het [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] kan helpen bij het beschermen van gegevens van uw organisatie, hoe het werkt met toepassingen, hoe deze worden vergeleken met de lokale versie van Active Directory Rights Management en begrijpen termen en afkortingen die specifiek zijn voor [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Wanneer u klaar bent om te testen Azure RMS zelf of voor uw organisatie implementeren, gebruik vervolgens de [Azure Rights Management-implementatieschema](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) voor een lijst met stappen met koppelingen voor meer informatie en procedures voor instructies.

Als u aanvullende informatie, bronnen en ondersteuningsopties, Zie [Informatie en ondersteuning voor Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## Kan ik Azure RMS integreren met mijn lokale servers
Ja. Azure RMS kan worden geïntegreerd met uw lokale servers, zoals bestandsservers Exchange Server, SharePoint en Windows. Hiervoor gebruikt u de [Rights Management-connector](https://technet.microsoft.com/library/dn375964.aspx). Of als u alleen geïnteresseerd bent in bestand classificatie infrastructuur (FC) gebruiken met Windows Server, kunt u de [RMS Protection cmdlets](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx). U kunt ook synchroniseren en uw Active Directory-domeincontrollers met Azure AD voor een naadloze verificatie-ervaring voor gebruikers, bijvoorbeeld communiceren met behulp van [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

Azure RMS genereert automatisch en beheert XrML certificaten als vereist, zodat deze een lokale PKI niet gebruiken. Zie voor meer informatie over hoe Microsoft Azure RMS certificaten gebruikt de [Overzicht van de werking van Azure RMS: Eerst gebruikt, beveiliging, inhoud verbruik van inhoud](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Walthrough) sectie de [Wat is Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) onderwerp.

## Ik heb een hybrid-implementatie van Exchange met bepaalde gebruikers op Exchange Online en andere op Exchange Server, wordt dit door Azure RMS ondersteund?
Absoluut, en het leuke is, gebruikers zich naadloos beveiligen en beveiligde e-mailberichten en bijlagen binnen de twee Exchange-implementaties in beslag nemen. Voor deze configuratie [activeren Azure RMS](https://technet.microsoft.com/library/jj658941.aspx) en [IRM inschakelen voor Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx), klikt u vervolgens [implementeren en configureren van de connector RMS](https://technet.microsoft.com/library/dn375964.aspx) voor Exchange Server.

## Als ik Azure RMS in productieomgevingen implementeren, is mijn bedrijf vervolgens vergrendeld in de oplossing of het risico toegang tot inhoud die we beveiligd met Azure RMS verliezen?
Nee, u altijd blijven controle over uw gegevens en toegang houden tot, zelfs als u besluit geen gebruik Azure RMS te. Zie voor meer informatie [Buiten gebruik stellen en Azure Rights Management deactiveren](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

Echter, voordat u uw Azure RMS-implementatie buiten gebruik stellen, willen we horen en te begrijpen waarom u deze beschikking gemaakt. Als Azure RMS niet voldoet aan uw zakelijke vereisten, controleert u met ons geval nieuwe functionaliteit is gepland voor de toekomst in de buurt of als er alternatieven. Een e-mailbericht te verzenden [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS) en we graag uw technische en zakelijke behoeften bespreken.

## Kan ik bepalen welke van mijn gebruikers Azure RMS kunt gebruiken om inhoud te beschermen?
Ja, heeft Azure RMS onboarding besturingselementen voor dit scenario. Zie voor meer informatie de [Onboarding besturingselementen voor een gefaseerde implementatie configureren](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) sectie de [Azure Rights Management activeren](../Topic/Activating_Azure_Rights_Management.md) onderwerp.

## Kan ik voorkomen dat gebruikers beveiligde documenten delen met specifieke organisaties?
Een van de grootste voordelen van Azure RMS is deze bedrijven samenwerking ondersteunt zonder dat u hoeft expliciete vertrouwensrelaties voor elke partnerorganisatie configureren omdat Azure AD voor de verificatie voor u zorgt.

Er is geen Beheeroptie om te voorkomen dat gebruikers documenten veilig delen met specifieke organisaties. U wilt bijvoorbeeld een organisatie die u niet vertrouwt blokkeren of waarvoor een concurrerende bedrijf. Voorkomen dat Azure RMS beveiligde documenten verzenden naar gebruikers in deze wouldn't organisaties verstandig omdat uw gebruikers deel vervolgens hun documenten die niet zijn beveiligd, dit is waarschijnlijk het laatste wat dat u wilt laten uitvoeren in dit scenario. Bijvoorbeeld, zou u kunnen identificeren die is vertrouwelijke documenten delen met welke gebruikers in deze organisaties, u doen kunt wanneer het document (of e-mail) door Azure RMS beveiligde.

## Wanneer ik een beveiligd document met iemand buiten mijn bedrijf delen, hoe die gebruiker ophalen geverifieerd?
Azure RMS gebruikt altijd een Azure Active Directory-account en een bijbehorende e-mailadres voor verificatie van de gebruiker die bedrijven samenwerking naadloze voor beheerders. Als de andere organisatie Azure-services gebruikt, wordt gebruikers al accounts hebben in Azure Active Directory, zelfs als deze accounts zijn gemaakt en lokale beheerd en worden gesynchroniseerd naar Azure.  Als de organisatie Office 365 achter de heeft, gebruikt deze service ook Azure Active Directory voor de gebruikersaccounts.  Als de organisatie van de gebruiker geen beheerde accounts in Azure, gebruikers kunnen zich aanmeldt voor [RMS voor personen](https://technet.microsoft.com/library/dn592127.aspx), die maakt u een niet-beheerde Azure tenant en de map voor de organisatie met een account voor de gebruiker zodat deze gebruiker kan worden geverifieerd voor Azure RMS.

De verificatiemethode die voor deze accounts kan variëren afhankelijk van hoe de beheerder in de andere organisatie de Azure Active Directory-accounts is geconfigureerd. Ze kunnen bijvoorbeeld wachtwoorden die zijn gemaakt gebruiken voor deze accounts, multi-factorauthenticatie (MFA), federation of wachtwoorden die zijn gemaakt in Active Directory Domain Services en worden gesynchroniseerd met Azure Active Directory.

## Kan ik gebruikers van buiten mijn bedrijf toevoegen aan aangepaste sjablonen?
Ja.  Maken van aangepaste sjablonen die eindgebruikers (en beheerders) van toepassingen selecteren kunnen kunt u snel en eenvoudig van toepassing van de beveiliging van gegevens te werken met vooraf gedefinieerde beleid dat u opgeeft. Een van de instellingen in de sjabloon die is toegang tot de inhoud is en kunt u gebruikers en groepen van binnen uw organisatie en gebruikers van buiten uw organisatie.

Gebruikers van buiten uw organisatie, gebruikt u de [Windows PowerShell-module voor Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx). U kunt een van deze opties:

-   **Exporteren, bewerken en de bijgewerkte sjabloon importeren**:  Dit is de gemakkelijkste methode als u wilt deze externe gebruikers toevoegen aan een bestaande sjabloon met andere groepen. Gebruik de [exporteren AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) cmdlet exporteren van de sjabloon naar een. CSV-bestand dat u bewerken wilt, om toe te voegen van de externe e-mailadressen van deze gebruikers en hun rechten op de bestaande groepen en rechten. Gebruik vervolgens de [importeren AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) voor het importeren van deze wijziging van de cmdlet weer in Azure RMS.

-   **Met een object van de definitie van rechten te maken of bijwerken van een sjabloon**:    Geef de externe e-mailadressen en hun rechten in een rechten definition-object dat u wilt maken of bijwerken van een sjabloon gebruiken. U de rechten definition-object opgeeft door de [Nieuw AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) cmdlet naar een variabele maken en geef deze variabele naar de parameter - RightsDefinition met de [toevoegen AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx) cmdlet (voor een nieuwe sjabloon) of [Set AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) cmdlet (als u een bestaande sjabloon wijzigt). Als u deze gebruikers aan een bestaande sjabloon toevoegen wilt, wordt u moet rechten definitie om objecten te definiëren voor de bestaande groepen in de sjablonen en niet alleen de externe gebruikers.

Zie voor meer informatie over aangepaste sjablonen [Aangepaste sjablonen configureren voor Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

## Welke apparaten en welke bestandstypen worden ondersteund door Azure RMS?
Voor een lijst met ondersteunde apparaten raadpleegt u de [Clientapparaten die ondersteuning van Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices) sectie de [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) onderwerp. Omdat niet alle ondersteunde apparaten alle RMS-mogelijkheden momenteel ondersteunen kunnen, moet u ook controleren of de [Client-apparaatmogelijkheden](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities) tabel in hetzelfde onderwerp.

Azure RMS kan alle bestandstypen ondersteunen. Voor tekst, afbeeldingen, Microsoft Office (Word, Excel en PowerPoint) bestanden, PDF-bestanden en enkele andere toepassing bestandstypen biedt Azure RMS systeemeigen beveiliging met codering en afdwingen van rechten (machtigingen). Algemene protection biedt voor alle andere toepassingen en bestandstypen, bestand inkapseling en verificatie om te controleren of een gebruiker is gemachtigd om het bestand te openen.

Voor een lijst met bestandsextensies die worden ondersteund door Azure RMS, raadpleegt u de [ondersteunde bestandstypen en extensies](http://technet.microsoft.com/library/dn339003.aspx) sectie van de [delen toepassing Rights Management-beheerdershandleiding](http://technet.microsoft.com/library/dn339003.aspx). Bestandsextensies niet in lijst worden met behulp van de RMS sharing toepassing die automatisch algemene beveiliging van toepassing op deze bestanden ondersteund.

## Wanneer wordt u ondersteuning voor migratie van AD RMS?
Azure RMS ondersteunen niet in eerste instantie migratie van een lokale implementatie van Rights Management, zoals AD RMS. Maar nu wordt ondersteund.

Zie voor meer informatie [Migratie van AD RMS naar Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

## We echt wilt BYOK met Azure RMS gebruiken, maar hebben geleerd dat dit is niet compatibel met Exchange Online, wat is uw advies?
Niet toestaan dat deze beperking vertraging van uw Azure RMS-implementatie. Als u Exchange Online en wilt gebruik brengt uw eigen sleutel (BYOK), wordt aangeraden het implementeren van Azure RMS in de Sleutelbeheer standaardmodus nu waar Microsoft genereert en beheert de sleutel. Op die manier u alle voordelen van het beschermen van uw belangrijke bestanden en e-mailberichten nu met de optie verplaatsen naar BYOK later (bijvoorbeeld, wanneer Exchange Online biedt ondersteuning voor BYOK).

Als het beleid van uw bedrijf moeten u een hardware HSM (security module) gebruiken en dit anders uw Azure RMS-implementatie wilt blokkeren, moet een andere optie is echter Azure RMS met BYOK nu implementeren met verminderde RMS-functionaliteit voor Exchange. Zie voor meer informatie de [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) sectie de [Plannen en implementeren van uw Azure Rights Management Tenant-sleutel](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) onderwerp.

## Een functie die ik op zoek ben lijkt niet werken met SharePoint beveiligd bibliotheken — is ondersteuning voor de functie Mijn geplande?
Momenteel beveiligd SharePoint ondersteunt RMS beveiligde documenten met IRM-bibliotheken bieden geen ondersteuning voor aangepaste sjablonen, document bijhouden en een aantal andere mogelijkheden.  Voor meer informatie, vouw de   [SharePoint Online en OneDrive voor bedrijven: IRM-configuratie](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline) sectie de [Hoe toepassingen ondersteunen Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md) onderwerp.

Als u geïnteresseerd in een specifieke mogelijkheid die nog niet wordt ondersteund bent, moet u op aankondigingen op dat de [RMS-teamblog](http://blogs.technet.com/b/rms/).

## Hoe kan ik een station voor zakelijke configureren in SharePoint Online zodat gebruikers hun bestanden veilig met mensen binnen en buiten het bedrijf delen kunnen?
Standaard configureren als een Office 365-beheerder u niet. gebruikers doen.

Als de beheerder van een SharePoint-site kunt en configureert u IRM voor een SharePoint-bibliotheek waarvan ze eigenaar, wordt OneDrive voor bedrijven ontworpen voor gebruikers inschakelen en configureren van IRM voor hun eigen OneDrive voor Business-bibliotheek.  Echter met PowerShell, kunt u dit doen voor deze. Vouw voor instructies de [SharePoint Online en OneDrive voor bedrijven: IRM-configuratie](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline)  sectie de [Toepassingen voor Azure Rights Management configureren](../Topic/Configuring_Applications_for_Azure_Rights_Management.md) artikel.

## Hebt u geen tips of trucs voor een geslaagde RMS-implementatie?
Nadat de toezicht op vele implementaties en luisteren naar onze klanten, partners, optreden adviseurs en support-engineers – een van de grootste tips die we van doorgeven kunnen: **Ontwerpen en implementeren van beleid eenvoudige rechten**.

Omdat Azure RMS veilig delen met anderen ondersteunt, kunt u enkele ambitieus met uw informatie protection bereik. Maar wees voorzichtig met het beleid van uw rechten. Voor veel organisaties is de grootste business impact afkomstig van het lekken gegevens voorkomen door het toepassen van de rechten beleid standaardsjabloon die toegankelijk voor mensen in uw organisatie alleen. Natuurlijk, krijgt u veel meer gedetailleerde dan die als u wilt – voorkomen mensen afdrukken dat, bewerken, enzovoort. Maar houd de meer gedetailleerde beperkingen als de uitzondering voor documenten die op hoog niveau beveiliging echt nodig hebt en niet meer beperkende beleid implementeren op dag, maar plan voor een meer gefaseerde benadering.

## Welke functies kunt of kan niet worden gebruikt met de verschillende abonnementen voor Azure RMS?
Er zijn enkele verschillen in de RMS-functies die worden ondersteund voor de betaalde abonnementen die ondersteuning van Azure RMS (Office 365, Azure RMS Premium en Enterprise mobiliteit Suite). Zie voor een lijst van deze [aanbiedingen voor vergelijking van Rights Management Services (RMS)](http://technet.microsoft.com/dn858608).

De gratis abonnement die Azure RMS (RMS voor personen) worden ondersteund ondersteunt in beslag inhoud die is beveiligd door Azure RMS. Zie voor meer informatie [RMS voor personen en Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## Hoe kom ik technische gegevens over de gratis Azure RMS-abonnement (RMS voor personen), bijvoorbeeld hoe het echt werkt, hoe controle krijgen over de accounts en welke domeinen kunnen niet worden gebruikt?
Vindt u antwoorden op deze vragen in de [RMS voor personen en Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md) onderwerp.

## Hoe we krijgen toegang tot bestanden die zijn beveiligd door een werknemer die heeft nu de organisatie verlaten?
Gebruik de functie supergebruiker Azure RMS, waarmee geautoriseerde gebruikers hebben volledige eigendomsrechten voor alle licenties die zijn toegewezen door uw organisatie RMS-tenant. Deze dezelfde functie kunt u geautoriseerde services-index en inspecteren van bestanden, indien nodig.

Zie voor meer informatie [Supergebruikers configureren voor Azure Rights Management en van detectieservices of gegevens te herstellen](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

## Rights Management kan voorkomen schermvastleggingen dat?
Rights Management worden schermvastleggingen vanuit de meeste van de meest gebruikte scherm vastleggen-hulpprogramma's die u helpen kunnen om te voorkomen dat per ongeluk of nalatig openbaarmaking van vertrouwelijke of gevoelige gegevens geblokkeerd. Er zijn echter vele manieren dat een gebruiker de gegevens die worden weergegeven op het scherm delen en duurt een schermafbeelding slechts één methode kunt is. Een gebruiker bedoeling op het delen van de weergegeven informatie kan bijvoorbeeld een afbeelding van hun telefoonnummer camera via, typen of gewoon woorden doorsturen naar iemand anders te.

Als deze voorbeelden technologie niet altijd voorkomen dat gebruikers delen van gegevens die ze niet moeten worden. Rights Management kan helpen bij het beschermen van uw belangrijke gegevens met behulp van autorisatie en gebruiksbeleid, moet deze enterprise rights management-oplossing worden gebruikt met andere besturingselementen. Bijvoorbeeld, fysieke beveiliging implementeren, zorgvuldig scherm en te bewaken mensen die u hebt toegang tot de gegevens van uw organisatie gemachtigd en investeren in gebruiker onderwijs, zodat gebruikers weten welke gegevens mag niet worden gedeeld.

## Waar kan ik vinden ondersteunende informatie voor Azure RMS, zoals juridische, compatibiliteit en sla's?
Azure RMS ondersteunt andere services en ook is afhankelijk van andere services. Als u naar informatie die is gerelateerd aan Azure RMS, maar niet over het gebruik van de Azure RMS-service zoekt, controleert u de volgende bronnen:

**Juridische en privacy:**

-   Voor informatie over Microsoft Azure: [Microsoft Azure-overeenkomst](http://azure.microsoft.com/support/legal/subscription-agreement/)

-   Voor Microsoft Azure privacy-informatie: [Privacyverklaring voor Microsoft Azure](http://azure.microsoft.com/support/legal/privacy-statement/)

**Beveiliging, compatibiliteit en controle:**

Zie de [Beveiliging, compatibiliteit en regelgevingsvereisten](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMScompliance) sectie de [Wat is Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) onderwerp. Bovendien:

-   Voor externe certificeringen voor Azure RMS: [Microsoft Azure Vertrouwenscentrum](http://azure.microsoft.com/support/trust-center/)

-   FIPS 140 informatie: [FIPS 140 validatie](https://technet.microsoft.com/library/security/cc750357.aspx)

**Serviceovereenkomsten:**

-   Serviceovereenkomst voor Azure RMS geselecteerde land: [Serviceovereenkomst](http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37)

-   Serviceovereenkomst voor Azure Active Directory: [Serviceovereenkomsten](http://azure.microsoft.com/support/legal/sla/)

**Documentatie:**

-   Azure Active Directory-documentatie site: [Azure Active Directory](http://azure.microsoft.com/documentation/services/active-directory/)

-   Azure Active Directory-bibliotheek: [Azure Active Directory](http://msdn.microsoft.com/library/azure/jj673460.aspx)

-   Office 365-bibliotheek: [Office 365](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

## Wat moet ik doen als mijn vraag is hier niet?
Gebruik de koppelingen en bronnen die worden vermeld [Informatie en ondersteuning voor Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

Bovendien zijn ontworpen voor eindgebruikers Veelgestelde vragen:

-   [Veelgestelde vragen voor Rights Management-toepassing voor Windows delen](https://technet.microsoft.com/dn467883)

-   [Veelgestelde vragen voor Rights Management-toepassing voor Mac-Platforms en mobiele delen](https://technet.microsoft.com/dn451248)

-   [Veelgestelde vragen over het Document bijhouden](http://go.microsoft.com/fwlink/?LinkId=523977)

Deze pagina Veelgestelde vragen over regelmatig bijgewerkt met nieuwe toevoegingen vermeld in de maandelijkse documentatie aankondigingen op de [Team van Microsoft Rights Management (RMS)](http://blogs.technet.com/b/rms/) blog.

> [!TIP]
> U kunt de [documenten label](http://blogs.technet.com/b/rms/archive/tags/docs/) op de blog om snel te vinden met deze aankondigingen documentatie.

## Zie ook
[Aan de slag met Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

