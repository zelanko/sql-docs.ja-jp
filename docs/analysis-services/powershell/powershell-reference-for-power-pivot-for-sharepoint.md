---
title: PowerShell Analysis Services のリファレンス Power Pivot for SharePoint |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9228eb879ed1417b31c95d53783d32acf53bcdb4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62509811"
---
# <a name="powershell-reference-for-power-pivot-for-sharepoint"></a>Power Pivot for SharePoint 用 PowerShell リファレンス
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] インストールを構成または管理するための PowerShell コマンドレットの一覧を次に示します。 コマンドレットの有効化と組み込まれているヘルプの表示については、「 [Windows PowerShell を使用した Power Pivot の構成](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)」を参照してください。  

>[!NOTE] 
>この記事では、古い情報と例を含めることができます。 最新バージョンには、Get-help コマンドレットを使用します。
  
## <a name="cmdlet-list"></a>コマンドレットの一覧  
 PowerShell プロンプトからコマンドレットの一覧を表示するには:  
  
1.  **[管理者として実行]** オプションを使用して SharePoint 管理シェルを開きます。  
  
2.  次のコマンドを入力します。 `Get-help *powerpivot*`  
  
|コマンドレット|Supported Versions|  
|------------|------------------------|  
|[Get-PowerPivotServiceApplication コマンドレット](../../analysis-services/powershell/get-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Get-PowerPivotSystemService コマンドレット](../../analysis-services/powershell/get-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Get-PowerPivotSystemServiceInstance コマンドレット](../../analysis-services/powershell/get-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[New-PowerPivotServiceApplication コマンドレット](../../analysis-services/powershell/new-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[New-PowerPivotSystemServiceInstance コマンドレット](../../analysis-services/powershell/new-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Remove-PowerPivotServiceApplication コマンドレット](../../analysis-services/powershell/remove-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Remove-PowerPivotSystemServiceInstance コマンドレット](../../analysis-services/powershell/remove-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Set-PowerPivotServiceApplication コマンドレット](../../analysis-services/powershell/set-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Set-PowerPivotSystemService コマンドレット](../../analysis-services/powershell/set-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Update-PowerPivotSystemService コマンドレット](../../analysis-services/powershell/update-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
  
 注:次のコマンドレットは、SharePoint 2010 でのみ機能する[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]はサポートしていません。  
  
-   Get-PowerPivotEngineService  
  
-   Get-PowerPivotEngineServiceInstance  
  
-   New-PowerPivotEngineServiceInstance  
  
-   Remove-PowerPivotEngineServiceInstance  
  
-   Set-PowerPivotEngineService  
  
-   Set-PowerPivotEngineServiceInstance  
  
-   Update-PowerPivotEngineService  
  
  
