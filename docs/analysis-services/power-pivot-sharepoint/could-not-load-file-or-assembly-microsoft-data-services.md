---
title: "ファイルまたは Microsoft Data Services アセンブリを読み込めませんでした |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 653e99076ed3b4aec45b116e02c20cccdde53c21
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="could-not-load-file-or-assembly-microsoft-data-services"></a>ファイルまたは Microsoft Data Services アセンブリを読み込めませんでした。
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint がある SharePoint 2010 環境では、データ フィードのエクスポートを実行しようとした場合に必要なバージョンの Microsoft ADO.NET Data Services がないと、このエラーが発生します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|適用対象|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|ADO.NET Data Services 3.5 SP1 が見つかりませんでした。|  
|メッセージ テキスト|ファイルまたはアセンブリ 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'、またはその依存関係の 1 つが読み込めませんでした。 指定されたファイルが見つかりません|  
  
## <a name="explanation"></a>説明  
 SharePoint 2010 には、SharePoint リストを XML データ フィードとしてエクスポートするための [データ フィードとしてエクスポート] ボタンがあります。 また、SharePoint モードの Reporting Services と [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint では、ADO.NET Data Services を必要とするデータ フィード機能をサポートしています。  
  
 ADO.NET Data Services がインストールされていない場合、データ フィードを実行しようとすると、このエラーが発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
  
1.  SharePoint 2010 のハードウェアおよびソフトウェアの要件に関するドキュメント「 [ハードウェアおよびソフトウェアの要件の決定 (SharePoint 2010)](http://go.microsoft.com/fwlink/?LinkId=169734) 」(http://go.microsoft.com/fwlink/?LinkId=169734) を開きます。  
  
2.  「 **前提条件となっているソフトウェアをインストールする**」で、使用しているオペレーティング システムに対応する ADO.NET Data Services 3.5 のリンクを見つけます。  
  
3.  リンクをクリックし、サービスをインストールするセットアップ プログラムを実行します。  
  
## <a name="see-also"></a>参照  
 [SharePoint への PowerPivot ソリューションの配置](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
