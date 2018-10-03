---
title: ファイルまたはアセンブリを読み込めませんでした&#39;Microsoft.AnalysisServices.SharePoint.Integration&#39; |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2b8328c060d7096cb43edcbc31206a8b55e82e7e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049212"
---
# <a name="could-not-load-file-or-assembly-39microsoftanalysisservicessharepointintegration39"></a>ファイルまたはアセンブリを読み込めませんでした&#39;Microsoft.AnalysisServices.SharePoint.Integration&#39;
  PowerPivot for SharePoint がある SharePoint 2010 環境で、PowerPivot のアプリケーション レベルのソリューションが正しく配置されていない場合にこのエラーが発生します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|適用対象|PowerPivot for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|Powerpivotwebapp ソリューションが配置されていないか、配置が正しくありません。|  
|メッセージ テキスト|ファイルまたはアセンブリ 'Microsoft.AnalysisServices.SharePoint.Integration' を読み込めませんでした|  
  
## <a name="explanation"></a>説明  
 PowerPivot for SharePoint では、その機能を SharePoint サーバーに配置するためにソリューション パッケージを使用します。 ソリューションのいずれかが正しく配置されていません。 そのため、PowerPivot ギャラリーまたは SharePoint サイトのその他の PowerPivot アプリケーション ページを開こうとするたびに、このエラーが表示されます。  
  
## <a name="user-action"></a>ユーザーの操作  
 ソリューション パッケージを配置します。  
  
1.  サーバーの全体管理で、[システム設定] の **[ファーム ソリューションの管理]** をクリックします。  
  
2.  **[Powerpivotwebapp]** をクリックします。  
  
3.  **[ソリューションの配置]** をクリックします。  
  
4.  このエラーが発生している Web アプリケーションを選択します。 複数の Web アプリケーションがある場合は、そのすべてについてソリューションを再配置します。  
  
5.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SharePoint に PowerPivot ソリューションを配置します。](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
