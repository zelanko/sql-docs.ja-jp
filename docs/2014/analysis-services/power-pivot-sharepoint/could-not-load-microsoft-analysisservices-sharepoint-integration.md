---
title: ファイルまたはアセンブリ &#39;読み込むことができませんでした。サービス、バージョン = 3.5.0.0、Culture = ニュートラル、PublicKeyToken = b77a5c561934e089&#39;、またはその依存関係の1つです。 指定されたファイルが見つかりません。 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b33e09d4dc7471f6447f1205f5c39746bc247ae7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66071629"
---
# <a name="could-not-load-file-or-assembly-39microsoftdataservices-version3500-cultureneutral-publickeytokenb77a5c561934e08939-or-one-of-its-dependencies-the-system-cannot-find-the-file-specified"></a>ファイルまたはアセンブリ &#39;読み込むことができませんでした。サービス、バージョン = 3.5.0.0、Culture = ニュートラル、PublicKeyToken = b77a5c561934e089&#39;、またはその依存関係の1つです。 指定されたファイルが見つかりません。
  PowerPivot for SharePoint がある SharePoint 2010 環境では、データ フィードのエクスポートを実行しようとした場合に必要なバージョンの Microsoft ADO.NET Data Services がないと、このエラーが発生します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|適用対象|PowerPivot for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|ADO.NET Data Services 3.5 SP1 が見つかりませんでした。|  
|メッセージ テキスト|ファイルまたはアセンブリ 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'、またはその依存関係の 1 つが読み込めませんでした。 指定されたファイルが見つかりません|  
  
## <a name="explanation"></a>説明  
 SharePoint 2010 には、SharePoint リストを XML データ フィードとしてエクスポートするための [データ フィードとしてエクスポート] ボタンがあります。 また、SharePoint モードの Reporting Services と PowerPivot for SharePoint では、ADO.NET Data Services を必要とするデータ フィード機能をサポートしています。  
  
 ADO.NET Data Services がインストールされていない場合、データ フィードを実行しようとすると、このエラーが発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
  
1.  SharePoint 2010 のハードウェアとソフトウェアの要件に関するドキュメントにアクセスし、[ハードウェアとソフトウェアの要件を決定します (sharepoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734) (https://go.microsoft.com/fwlink/?LinkId=169734)「」を参照してください。  
  
2.  「**必要なソフトウェアのインストール**」で、使用しているオペレーティングシステムに対応する ADO.NET Data Services 3.5 のリンクを見つけます。  
  
3.  リンクをクリックし、サービスをインストールするセットアップ プログラムを実行します。  
  
## <a name="see-also"></a>参照  
 [SharePoint への PowerPivot ソリューションの配置](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
