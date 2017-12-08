---
title: "'Microsoft.analysisservices.sharepoint.integration' を読み込めませんでした |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: power-pivot-sharepoint
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dec23d57b74350f9952246c5b0a0fa915b91a9d7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="could-not-load-microsoftanalysisservicessharepointintegration"></a>Microsoft.AnalysisServices.SharePoint.Integration を読み込むことができませんでした。
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint がある SharePoint 2010 環境で、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] のアプリケーション レベルのソリューションが正しく配置されていない場合にこのエラーが発生します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|適用対象|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|Powerpivotwebapp ソリューションが配置されていないか、配置が正しくありません。|  
|メッセージ テキスト|ファイルまたはアセンブリ 'Microsoft.AnalysisServices.SharePoint.Integration' を読み込めませんでした|  
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint では、その機能を SharePoint サーバーに配置するためにソリューション パッケージを使用します。 ソリューションのいずれかが正しく配置されていません。 そのため、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーまたは SharePoint サイトのその他の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] アプリケーション ページを開こうとするたびに、このエラーが表示されます。  
  
## <a name="user-action"></a>ユーザーの操作  
 ソリューション パッケージを配置します。  
  
1.  サーバーの全体管理で、[システム設定] の **[ファーム ソリューションの管理]**をクリックします。  
  
2.  **[Powerpivotwebapp]**をクリックします。  
  
3.  **[ソリューションの配置]**をクリックします。  
  
4.  このエラーが発生している Web アプリケーションを選択します。 複数の Web アプリケーションがある場合は、そのすべてについてソリューションを再配置します。  
  
5.  **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [SharePoint への PowerPivot ソリューションの配置](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
