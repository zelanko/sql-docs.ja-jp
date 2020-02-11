---
title: ファイルまたはアセンブリを読み込めませんでした &#39;Microsoft.analysisservices.sharepoint.integration.dll&#39; |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 42c7b7e876f244831920be390d97c88412eed63f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66071665"
---
# <a name="could-not-load-file-or-assembly-39microsoftanalysisservicessharepointintegration39"></a>Microsoft.analysisservices.sharepoint.integration.dll&#39; &#39;ファイルまたはアセンブリを読み込めませんでした
  PowerPivot for SharePoint がある SharePoint 2010 環境で、PowerPivot のアプリケーション レベルのソリューションが正しく配置されていない場合にこのエラーが発生します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|適用対象|PowerPivot for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|Powerpivotwebapp ソリューションが配置されていないか、配置が正しくありません。|  
|メッセージ テキスト|ファイルまたはアセンブリ 'Microsoft.AnalysisServices.SharePoint.Integration' を読み込めませんでした|  
  
## <a name="explanation"></a>説明  
 PowerPivot for SharePoint では、その機能を SharePoint サーバーに配置するためにソリューション パッケージを使用します。 ソリューションのいずれかが正しく配置されていません。 そのため、PowerPivot ギャラリーまたは SharePoint サイトのその他の PowerPivot アプリケーション ページを開こうとするたびに、このエラーが表示されます。  
  
## <a name="user-action"></a>ユーザーの操作  
 ソリューション パッケージを配置します。  
  
1.  サーバーの全体管理で、[システム設定] の **[ファーム ソリューションの管理]** をクリックします。  
  
2.  
  **[Powerpivotwebapp]** をクリックします。  
  
3.  
  **[ソリューションの配置]** をクリックします。  
  
4.  このエラーが発生している Web アプリケーションを選択します。 複数の Web アプリケーションがある場合は、そのすべてについてソリューションを再配置します。  
  
5.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SharePoint への PowerPivot ソリューションの配置](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
