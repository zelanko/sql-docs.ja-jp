---
title: 'タスク 9: 参照データ サービスの構成 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3a743fd3fe576296a67072762cdfa3a186584cd0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37326862"
---
# <a name="task-9-configuring-a-reference-data-service"></a>タスク 9: 参照データ サービスを構成する
  ここでは、Windows Azure Marketplace の参照データ サービスを使用するように DQS を構成します。 次のタスクでは、構成、 **Address Validation**ドメインをこのサービスを使用します。 実行時に、クレンジング アクティビティ中に DQS 渡します内のドメインの値、 **Address Validation**ドメインをクレンジングするためのサービスです。 参照してください[Configure DQS to Use Reference Data](http://msdn.microsoft.com/library/hh213070.aspx)の詳細。  
  
1.  メイン ページで**DQS クライアント**の**管理**ウィンドウで、をクリックして**構成**します。  
  
2.  いることを確認**参照データ**タブがアクティブにします。  
  
3.  **ネットワーク設定**領域で、型の適切な値で、**プロキシ サーバー**と**ポート**フィールドのプロキシ サーバーを使用してインターネットに接続する必要がある場合。  
  
4.  型、 **Windows Azure Marketplace アカウント キー**の**DataMarket のアカウント ID**フィールド。  
  
     ![Azure Data Market 参照データ サービスのアカウント](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Azure Data Market 参照データ サービス アカウント")  
  
5.  クリックして**検証**アカウント ID を検証するテキスト ボックスの横にあるボタンをクリックします。  
  
6.  クリックして**OK**メッセージ ボックス。  
  
7.  クリックして**閉じる**DQS クライアントのメイン ページに移動するページの下部にあります。  
  
## <a name="next-task"></a>次の作業  
 [タスク 10: 参照データ サービスを使用して複合ドメインを構成する](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  
