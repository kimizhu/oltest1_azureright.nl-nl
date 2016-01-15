---
description: na
keywords: na
title: Dialog box options for the Rights Management sharing application
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b91ab30-6363-4929-bcbd-4dfbd05f644a
---
# De opties in het dialoogvenster voor de Rights Management-toepassing delen
Deze informatie gebruiken om te helpen u de opties in de RMS sharing toepassing opgeven **Beveiliging toevoegen** in het dialoogvenster of de **beveiligd delen** in het dialoogvenster. Ziet u dit dialoogvenster vak wanneer u [een bestand te delen beveiligd](http://technet.microsoft.com/library/dn574735.aspx) of u [beveiligen van een bestand in plaats](http://technet.microsoft.com/library/dn574733.aspx) en kies aangepaste machtigingen.

> [!IMPORTANT]
> Als de opties die u ziet verschillen van de hier beschreven, hebt u waarschijnlijk niet de nieuwste versie van de delen toepassing is geïnstalleerd. U kunt download de nieuwste versie van de [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) pagina.
> 
> Hoe weet u als u de meest recente versie? Zoek naar **Microsoft Rights Management-toepassing voor delen** vermeld in programma's en onderdelen en de bijbehorende versienummer controleren. Als u wilt zien en gebruikt u de opties in de tabel, de versie moet ten minste **1.0.1770.0**. U kunt het nummer van de meest recente versie van de downloadpagina controleren.

Naast de opties die u kunt kiezen, vraagt u mogelijk ook worden af:

-   [Wat is het bestand .ppdf die automatisch wordt gemaakt?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_PPDF)

-   [Wat is het verschil tussen algemene bescherming en ingebouwde (standaard)?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_GenericNative)

|Optie|Beschrijving|
|---------|----------------|
|**GEBRUIKERS**|Als u al een e-mailadres van Outlook nog niet hebt opgegeven, typt u de e-mailadressen van de mensen die u wilt kan het bestand te openen.<br /><br />Als uw organisatie gebruikmaakt van de lokale versie van Rights Management (AD RMS), is de kunt u e-mailadressen zijn beperkt tot mensen binnen uw organisatie. Wanneer dit is van toepassing en probeer het externe e-mailadressen opgeven, ziet u een bericht weergegeven dat de configuratie van uw bedrijf kunt delen van beveiligde inhoud binnen het bedrijf. Als uw organisatie gebruikmaakt van Azure RMS, kunnen deze e-mailadressen echter voor mensen binnen uw organisatie of voor mensen in een andere organisatie.<br /><br />Voorbeeld: janetm@contoso.com; p.Dover@Fabrikam.com|
|**Algemene beveiliging**|Als deze optie is geselecteerd, betekent dit dat het geselecteerde bestand systeemeigen kan niet worden beveiligd. Zie voor meer informatie. [Wat is het verschil tussen algemene bescherming en ingebouwde (standaard)?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_GenericNative) in dit onderwerp.|
|**Viewer – alleen weergeven**<br /><br />**Revisor – weergeven en bewerken**<br /><br />**Auteurs – weergeven, bewerken, kopiëren en afdrukken**<br /><br />**Collega eigenaar – alle machtigingen** **Note:** Deze opties hebben een rond pictogram voordat u de naam die een globe world vertegenwoordigen. Dit pictogram wordt gebruikt, omdat er meestal u een van deze opties wanneer u uw bijlage naar iemand anders te in een andere organisatie verzenden.|Selecteer een van deze opties als u wilt de rechten voor het beveiligde document definiëren. Klik op elke optie om een beschrijving weer te geven.<br /><br />Wanneer u een van de volgende opties kiezen, alleen de mensen die u opgeeft in **gebruikers** beschikt over de rechten u opgeeft om te openen en gebruiken van het document. Bijvoorbeeld als ze naar iemand anders doorstuurt, zou het document niet openen.|
|Beleidssjablonen die uw beheerder configureert.<br /><br />Bijvoorbeeld als de naam van uw bedrijf Contoso, Ltd: **Contoso, Ltd - alleen vertrouwelijke weergeven** **Note:** Deze opties hebben een vierkant pictogram voordat u de naam die een office ontwikkelen vertegenwoordigen. Dit pictogram wordt gebruikt, omdat er meestal u een van deze opties wanneer u uw bijlage naar iemand anders te in uw organisatie verzenden.|Wanneer u een document met mensen die werken voor uw organisatie delen, ziet u de beschikbare sjablonen die uw beheerder configureert. Kies een van deze wanneer het document mag niet worden gedeeld buiten uw organisatie.<br /><br />Wanneer u een van deze opties kiest, bepaalt de beheerder de rechten voor het document en wie het kunt openen.|
|**Deze documenten verlopen op**|Selecteer deze optie alleen voor tijdgebonden bestanden die de gebruikers die u hebt geselecteerd niet kunnen openen na een datum die u opgeeft. U kunt zich nog steeds het oorspronkelijke bestand openen, maar na middernacht (uw huidige tijdzone) op de dag die u opgeeft, anderen niet mogelijk om het bestand te openen.<br /><br />Deze optie is niet beschikbaar als u een beleidssjabloon die uw beheerder configureert.|
|**E-mail me wanneer iemand probeert te openen van deze documenten**|**Note:** Deze optie is momenteel preview.<br />Selecteer deze optie als u e-mailmeldingen ontvangen wilt wanneer iemand probeert te openen van het document dat u bent beschermen. Het e-mailbericht kan aangeven die probeert te openen, wanneer en of ze voltooid zijn.<br /><br />Deze optie is alleen beschikbaar als uw organisatie Azure RMS gebruikt. Als uw organisatie gebruikt de lokale versie van Rights Management (AD RMS), ziet u deze optie niet.|
|**Kan ik toegang tot deze documenten meteen intrekken**|Selecteer deze optie als u toegang tot de documenten later intrekken moet mogelijk met behulp van het document site bijhouden en intrekken moet onmiddellijk van kracht. Instellen van deze optie manier die tijdens het document niet is ingetrokken, moeten gebruikers altijd echter een internetverbinding nodig om te lezen van het document telkens wanneer die ze toegang hebben. Er is mogelijk een aantal scenario's waar gebruikers hun apparaat kunnen geen verbinding met Internet en gebruikers het document als u de bedoeling kunnen niet lezen.<br /><br />Als u deze optie niet kiest, kunt u de documenten nog steeds later intrekken met behulp van de site document bijhouden. Echter, omdat gebruikers niet altijd een internetverbinding nodig om te lezen van het document hoeven, ze weet niet direct het document is ingetrokken en kan worden voortgezet totdat ze vervolgens met Azure RMS verifiëren lezen. Het maximum aantal dagen dat iemand kan doorgaan met het lezen van een beveiligd document die u hebt ingetrokken is 30 dagen standaard, maar deze waarde groter dan 30 dagen of minder zijn door een beheerder kan wijzigen.<br /><br />Deze optie is alleen beschikbaar als uw organisatie Azure RMS gebruikt. Als uw organisatie gebruikt de lokale versie van Rights Management (AD RMS), ziet u deze optie niet.|

## <a name="BKMK_GenericNative"></a>Wat is het verschil tussen algemene bescherming en ingebouwde (standaard)?

-   Wanneer u **generieke een bestand beveiligd**, niet-geautoriseerde personen het bestand niet openen. Maar als gemachtigde personen het bestand opent, kan vervolgens doorsturen naar anderen de beveiliging is opgeheven of op een locatie die anderen kunnen toegang krijgen tot opslaan. Ze een bericht dat ze machtigingen die ze voor het bestand hebben echter doet, zien en hun wordt gevraagd om deze, maar deze beveiliging kan niet worden afgedwongen. Wanneer u een bestand generieke beveiligt, beperken niet u bovendien de machtigingen heeft meer dan autorisatie. Zoals u de inhoud niet beperken tot alleen-lezen of niet afdrukken.:

    > [!NOTE]
    > Een algemeen beveiligd bestand heeft altijd extensie van **.pfile**.

-   In de vergelijking, wanneer u de **ingebouwde (standaard) bescherming** van Rights Management met toepassingen die deze (bijvoorbeeld Office-bestanden ondersteunen), de bescherming van toepassing op het bestand zelfs als het bestand vervolgens wordt verzonden naar iemand anders of opgeslagen in een andere locatie. En als u deze bestanden worden beveiligd, kunt u beperkte machtigingen, zoals alleen-lezen, of de machtiging bewerken, maar niet afdrukken of kopiëren. Bijvoorbeeld, kunt u selecteren **Viewer – alleen weergeven**, zodat de inhoud kan niet worden bewerkt, afgedrukt of gekopieerd.

Zie voor aanvullende technische informatie, de [Niveaus van beveiliging – systeemeigen en algemene](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection) sectie de [Rights Management delen toepassing beheerdershandleiding](../Topic/Rights_Management_sharing_application_administrator_guide.md).

## <a name="BKMK_PPDF"></a>Wat is het bestand .ppdf die automatisch wordt gemaakt?

-   De RMS sharing toepassing automatisch wordt gemaakt wanneer u een beveiligd bestand delen via e-mail (beveiligd delen), een **.ppdf** versie van het bestand voor Word, Excel, PowerPoint of PDF-bestand. Dit is een alleen-lezen beschermde versie van het bestand dat alleen gemachtigde personen kunt openen, en zorgt ervoor dat de geadresseerden de bijlage kunnen lezen zelfs als ze een mobiel apparaat dat een toepassing die Rights Management ondersteunt geen gebruiken. Mits deze mensen de app RMS sharing geïnstalleerd hebben, worden ze kunnen lezen van de bijlage.

    In dit scenario, in tegenstelling tot een algemeen beveiligd bestand wordt gebruiksbeperking afgedwongen. De ontvanger worden niet met deze versie van het bestand opslaan en als ze de bijlage aan iemand anders doorsturen, de oorspronkelijke beperkingen blijven met het document. Alleen de personen die gemachtigd zijn voor het beveiligde document is het mogelijk om deze te openen.

    > [!NOTE]
    > Een bestand .ppdf wordt automatisch gemaakt wanneer u delen van beveiligde (share per e-mail), maar niet gemaakt is wanneer u direct beveiligen.

## Voorbeelden en andere instructies
Zie de volgende secties van de Rights Management delen application user guide voor voorbeelden voor het gebruik van de Rights Management-toepassing en praktische instructies delen:

-   [Voorbeelden voor het gebruik van de RMS sharing toepassing](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingExamples)

-   [Wat wilt u doen?](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingInstructions)

## Zie ook
[Rights Management delen toepassing handleiding](../Topic/Rights_Management_sharing_application_user_guide.md)

