---
title: Erstellen von Microsoft 365-Benutzerkonten mit PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: In diesem Artikel erfahren Sie, wie Sie mithilfe von PowerShell Benutzerkonten oder mehrere Microsoft 365-Benutzerkonten erstellen.
ms.openlocfilehash: 53077352862b6d0df6bb569300e2d8bc2475df91
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46690659"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="d5801-103">Erstellen von Microsoft 365-Benutzerkonten mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5801-103">Create Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="d5801-104">*Dieser Artikel gilt sowohl für Microsoft 365 Enterprise als auch für Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="d5801-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="d5801-105">Sie können PowerShell für Microsoft 365 zum effizienten Erstellen von Benutzerkonten verwenden, insbesondere für mehrere Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="d5801-105">You can use PowerShell for Microsoft 365 to efficiently create user accounts, especially multiple user accounts.</span></span> <span data-ttu-id="d5801-106">Wenn Sie Benutzerkonten in PowerShell erstellen, sind bestimmte Kontoeigenschaften immer erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d5801-106">When you create user accounts in PowerShell, certain account properties are always required.</span></span> <span data-ttu-id="d5801-107">Andere Eigenschaften sind nicht erforderlich, um das Konto zu erstellen, sind aber dennoch wichtig.</span><span class="sxs-lookup"><span data-stu-id="d5801-107">Other properties aren't required to create the account, but are otherwise important.</span></span> <span data-ttu-id="d5801-108">Diese Eigenschaften werden in der folgenden Tabelle beschrieben:</span><span class="sxs-lookup"><span data-stu-id="d5801-108">These properties are described in the following table:</span></span>
  
|<span data-ttu-id="d5801-109">**Eigenschaftenname**</span><span class="sxs-lookup"><span data-stu-id="d5801-109">**Property name**</span></span>|<span data-ttu-id="d5801-110">**Erforderlich?**</span><span class="sxs-lookup"><span data-stu-id="d5801-110">**Required?**</span></span>|<span data-ttu-id="d5801-111">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="d5801-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d5801-112">**Anzeigename**</span><span class="sxs-lookup"><span data-stu-id="d5801-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="d5801-113">Ja</span><span class="sxs-lookup"><span data-stu-id="d5801-113">Yes</span></span>  <br/> |<span data-ttu-id="d5801-114">Dies ist der Anzeigename, der in Microsoft 365-Diensten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d5801-114">This is the display name that's used in Microsoft 365 services.</span></span> <span data-ttu-id="d5801-115">Zum Beispiel „Caleb Sills".</span><span class="sxs-lookup"><span data-stu-id="d5801-115">For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="d5801-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="d5801-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="d5801-117">Ja</span><span class="sxs-lookup"><span data-stu-id="d5801-117">Yes</span></span>  <br/> |<span data-ttu-id="d5801-118">Hierbei handelt es sich um den Kontonamen, der für die Anmeldung bei Microsoft 365-Diensten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d5801-118">This is the account name that's used to sign in to Microsoft 365 services.</span></span> <span data-ttu-id="d5801-119">Zum Beispiel „CalebS@contoso.onmicrosoft.com".</span><span class="sxs-lookup"><span data-stu-id="d5801-119">For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="d5801-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="d5801-120">**FirstName**</span></span> <br/> |<span data-ttu-id="d5801-121">Nein</span><span class="sxs-lookup"><span data-stu-id="d5801-121">No</span></span>  <br/> ||
|<span data-ttu-id="d5801-122">**Nachname**</span><span class="sxs-lookup"><span data-stu-id="d5801-122">**LastName**</span></span> <br/> |<span data-ttu-id="d5801-123">Nein</span><span class="sxs-lookup"><span data-stu-id="d5801-123">No</span></span>  <br/> ||
|<span data-ttu-id="d5801-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="d5801-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="d5801-125">Nein</span><span class="sxs-lookup"><span data-stu-id="d5801-125">No</span></span>  <br/> |<span data-ttu-id="d5801-126">Hierbei handelt es sich um den Lizenzierungs Plan (auch als Lizenzplan oder SKU bezeichnet), von dem eine verfügbare Lizenz dem Benutzerkonto zugewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="d5801-126">This is the licensing plan (also known as the license plan or SKU) from which an available license is assigned to the user account.</span></span> <span data-ttu-id="d5801-127">Die Lizenz definiert die Microsoft 365-Dienste, die für das Konto verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="d5801-127">The license defines the Microsoft 365 services that are available to account.</span></span> <span data-ttu-id="d5801-128">Sie müssen einem Benutzer beim Erstellen des Kontos keine Lizenz zuweisen, aber für das Konto ist eine Lizenz für den Zugriff auf Microsoft 365-Dienste erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d5801-128">You don't have to assign a license to a user when you create the account, but the account requires a license to access Microsoft 365 services.</span></span> <span data-ttu-id="d5801-129">Sie haben 30 Tage Zeit, um das Benutzerkonto zu lizenzieren, nachdem Sie es erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="d5801-129">You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="d5801-130">**Password**</span><span class="sxs-lookup"><span data-stu-id="d5801-130">**Password**</span></span> <br/> |<span data-ttu-id="d5801-131">Nein</span><span class="sxs-lookup"><span data-stu-id="d5801-131">No</span></span>  <br/> | <span data-ttu-id="d5801-p105">Wenn Sie kein Kennwort angeben, wird dem Benutzerkonto ein zufälliges Kennwort zugewiesen, und das Kennwort wird in den Ergebnissen des Befehls angezeigt. Wenn Sie ein Kennwort angeben, muss es aus 8 bis 16 ASCII-Textzeichen aus drei der folgenden Kategorien bestehen: Kleinbuchstaben, Großbuchstaben, Zahlen oder Symbole.</span><span class="sxs-lookup"><span data-stu-id="d5801-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="d5801-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="d5801-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="d5801-135">Nein</span><span class="sxs-lookup"><span data-stu-id="d5801-135">No</span></span>  <br/> |<span data-ttu-id="d5801-136">Dies ist ein gültiger ISO 3166-1-Alpha-2-Ländercode.</span><span class="sxs-lookup"><span data-stu-id="d5801-136">This is a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="d5801-137">„US" steht zum Beispiel für die Vereinigten Staaten und „FR" für Frankreich.</span><span class="sxs-lookup"><span data-stu-id="d5801-137">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="d5801-138">Es ist wichtig, diesen Wert anzugeben, da einige Microsoft 365-Dienste in bestimmten Ländern nicht verfügbar sind, sodass Sie einem Benutzerkonto keine Lizenz zuweisen können, es sei denn, das Konto hat diesen Wert konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="d5801-138">It's important to provide this value, because some Microsoft 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured.</span></span> <span data-ttu-id="d5801-139">Weitere Informationen finden Sie unter [Informationen zu Lizenzbeschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="d5801-139">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>  <br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d5801-140">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="d5801-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d5801-141">Stellen Sie zunächst [eine Verbindung mit Ihrem Microsoft 365-Mandanten her](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="d5801-141">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="d5801-142">Nachdem Sie eine Verbindung hergestellt haben, verwenden Sie die folgende Syntax, um ein einzelnes Konto zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="d5801-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="d5801-143">In diesem Beispiel wird ein Konto für den US-amerikanischen Benutzer mit dem Namen „Caleb Sills“ erstellt:</span><span class="sxs-lookup"><span data-stu-id="d5801-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d5801-144">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5801-144">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d5801-145">Stellen Sie zunächst [eine Verbindung mit Ihrem Microsoft 365-Mandanten her](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d5801-145">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="d5801-146">Erstellen eines einzelnen Benutzerkontos</span><span class="sxs-lookup"><span data-stu-id="d5801-146">Create an individual user account</span></span>

<span data-ttu-id="d5801-147">Verwenden Sie die folgende Syntax, um ein einzelnes Konto zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="d5801-147">To create an individual account, use the following syntax:</span></span>
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
><span data-ttu-id="d5801-148">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="d5801-148">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="d5801-149">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="d5801-149">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="d5801-150">Mit dem folgenden Befehl erhalten Sie eine Liste der Namen der Lizenzierungspläne:</span><span class="sxs-lookup"><span data-stu-id="d5801-150">To list the available licensing plan names, use this command:</span></span>

````powershell
Get-MsolAccountSku
````

<span data-ttu-id="d5801-151">In diesem Beispiel wird ein Konto für den US-amerikanischen Benutzer mit dem Namen „Caleb Sills" erstellt und eine Lizenz aus dem `contoso:ENTERPRISEPACK`-Lizenzierungsplan (Office 365 Enterprise E3) zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="d5801-151">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="d5801-152">Erstellen mehrerer Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="d5801-152">Create multiple user accounts</span></span>

1. <span data-ttu-id="d5801-p108">Erstellen Sie eine durch Kommata getrennte Wertedatei (CSV), die die erforderlichen Informationen zum Benutzerkonto enthält. Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d5801-p108">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="d5801-155">Die Spaltennamen und ihre Reihenfolge in der ersten Zeile der CSV-Datei sind willkürlich, aber stellen Sie sicher, dass die Daten im Rest der Datei mit der Reihenfolge der Spaltennamen übereinstimmen, und verwenden Sie die Spaltennamen für die Parameterwerte im PowerShell for Microsoft 365-Befehl.</span><span class="sxs-lookup"><span data-stu-id="d5801-155">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the PowerShell for Microsoft 365 command.</span></span>
    
2. <span data-ttu-id="d5801-156">Verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="d5801-156">Use the following syntax:</span></span>
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="d5801-157">In diesem Beispiel werden die Benutzerkonten aus der Datei mit dem Namen „C:\My Documents\NewAccounts.csv“ erstellt, und die Ergebnisse werden in der Datei mit dem Namen „C:\My Documents\NewAccountResults.csv“ protokolliert.</span><span class="sxs-lookup"><span data-stu-id="d5801-157">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="d5801-158">Die Ergebnisse können Sie in der Ausgabedatei überprüfen.</span><span class="sxs-lookup"><span data-stu-id="d5801-158">Review the output file to see the results.</span></span> <span data-ttu-id="d5801-159">Es wurden keine Kennwörter angegeben, sodass die zufälligen Kennwörter, die von Microsoft 365 generiert wurden, in der Ausgabedatei angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d5801-159">We didn't specify passwords, so the random passwords that Microsoft 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="d5801-160">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d5801-160">See also</span></span>

[<span data-ttu-id="d5801-161">Verwalten von Microsoft 365-Benutzerkonten, -Lizenzen und -Gruppen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5801-161">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="d5801-162">Verwalten von Microsoft 365 mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5801-162">Manage Microsoft 365 with PowerShell</span></span>](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="d5801-163">Erste Schritte mit PowerShell für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d5801-163">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-microsoft-365-powershell.md)