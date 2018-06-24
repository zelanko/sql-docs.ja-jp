---
title: データをサポートする ADO.NET Data Services をインストールのフィードのエクスポート SharePoint リスト |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: d4241d56aa3257bd0ec2cddf4b439a4939f8ab9f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075156"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a>データの SharePoint リストのフィードのエクスポートをサポートする ADO.NET Data Services のインストールします。
  ADO.NET Data Services は、SharePoint リストのデータ フィードのエクスポートに必要です。 SharePoint 2010 では、このコンポーネントは SharePoint の必須コンポーネントのインストーラー プログラムに含まれていないため、手動でインストールする必要があります。  
  
 この前提条件なしで、データ フィードとしてエクスポートされた SharePoint リストの使用を試みると、次のエラーが表示されます。"セキュリティ上の理由から、この XML 文書での DTD 処理は禁止されています。 XmlReaderSettings の ProhibitDtd プロパティを false に設定し、その設定を XmlReader.Create メソッドに渡してください。"  
  
 次の手順に従って、リストをデータ フィードとしてエクスポートできるようにする各 SharePoint サーバーに ADO.NET Data Services をインストールします。  
  
### <a name="download-and-install-adonet-data-services"></a>ADO.NET Data Services のダウンロードとインストール  
  
1.  SharePoint 2010 のハードウェアとソフトウェア要件のドキュメントに移動して[Hardware and Software Requirements (SharePoint 2010)](http://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  **適用可能なソフトウェアへのアクセス**、ADO.NET Data Services 3.5 のオペレーティング システムに対応するは、(Windows Server 2008 SP2 または Windows Server 2008 R2) を使用しているのリンクを見つけます。  
  
3.  リンクをクリックし、サービスをインストールするセットアップ プログラムを実行します。  
  
## <a name="see-also"></a>参照  
 [PowerPivot for SharePoint 2010 のインストール](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  