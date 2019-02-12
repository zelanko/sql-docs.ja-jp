---
title: タスク 9:参照データ サービスの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: adbde32de86da407bdd2655f66d036021e6784f8
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56039413"
---
# <a name="task-9-configuring-a-reference-data-service"></a>タスク 9:参照データ サービスを構成する
  ここでは、Windows Azure Marketplace の参照データ サービスを使用するように DQS を構成します。 次のタスクでは、構成、 **Address Validation**ドメインをこのサービスを使用します。 実行時に、クレンジング アクティビティ中に DQS 渡します内のドメインの値、 **Address Validation**ドメインをクレンジングするためのサービスです。 参照してください[Configure DQS to Use Reference Data](https://msdn.microsoft.com/library/hh213070.aspx)の詳細。  
  
1.  メイン ページで**DQS クライアント**の**管理**ウィンドウで、をクリックして**構成**します。  
  
2.  いることを確認**参照データ**タブがアクティブにします。  
  
3.  **ネットワーク設定**領域で、型の適切な値で、**プロキシ サーバー**と**ポート**フィールドのプロキシ サーバーを使用してインターネットに接続する必要がある場合。  
  
4.  型、 **Windows Azure Marketplace アカウント キー**の**DataMarket のアカウント ID**フィールド。  
  
     ![Azure Data Market 参照データ サービスのアカウント](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Azure Data Market 参照データ サービス アカウント")  
  
5.  クリックして**検証**アカウント ID を検証するテキスト ボックスの横にあるボタンをクリックします。  
  
6.  クリックして**OK**メッセージ ボックス。  
  
7.  クリックして**閉じる**DQS クライアントのメイン ページに移動するページの下部にあります。  
  
## <a name="next-task"></a>次の作業  
 [タスク 10:参照データ サービスを使用する複合ドメインの構成](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  
