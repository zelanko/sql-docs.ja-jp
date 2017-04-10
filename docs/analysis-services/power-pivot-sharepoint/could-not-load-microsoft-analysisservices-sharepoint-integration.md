---
title: "ファイルまたはアセンブリ &#39;Microsoft.AnalysisServices.SharePoint.Integration&#39; を読み込めませんでした | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
caps.latest.revision: 7
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 7
---
# ファイルまたはアセンブリ &#39;Microsoft.AnalysisServices.SharePoint.Integration&#39; を読み込めませんでした
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint がある SharePoint 2010 環境で、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] のアプリケーション レベルのソリューションが正しく配置されていない場合にこのエラーが発生します。  
  
## 詳細  
  
|||  
|-|-|  
|適用対象|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|Powerpivotwebapp ソリューションが配置されていないか、配置が正しくありません。|  
|メッセージ テキスト|ファイルまたはアセンブリ 'Microsoft.AnalysisServices.SharePoint.Integration' を読み込めませんでした|  
  
## 説明  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]  for SharePoint では、その機能を SharePoint サーバーに配置するためにソリューション パッケージを使用します。 ソリューションのいずれかが正しく配置されていません。 そのため、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーまたは SharePoint サイトのその他の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] アプリケーション ページを開こうとするたびに、このエラーが表示されます。  
  
## ユーザーの操作  
 ソリューション パッケージを配置します。  
  
1.  サーバーの全体管理で、[システム設定] の **[ファーム ソリューションの管理]**をクリックします。  
  
2.  **[Powerpivotwebapp]** をクリックします。  
  
3.  **[ソリューションの配置]**をクリックします。  
  
4.  このエラーが発生している Web アプリケーションを選択します。 複数の Web アプリケーションがある場合は、そのすべてについてソリューションを再配置します。  
  
5.  **[OK]**をクリックします。  
  
## 参照  
 [SharePoint への PowerPivot ソリューションの配置](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  