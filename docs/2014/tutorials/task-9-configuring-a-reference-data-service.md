---
title: 'タスク 9: 参照データ サービスの構成 |Microsoft ドキュメント'
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
ms.topic: article
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5a08d3848ddaf65b9e10b654f55e8a0a4d9be690
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179587"
---
# <a name="task-9-configuring-a-reference-data-service"></a>タスク 9: 参照データ サービスを構成する
  ここでは、Windows Azure Marketplace の参照データ サービスを使用するように DQS を構成します。 次のタスクでは、構成、 **Address Validation**このサービスを使用するドメインです。 実行時に、クレンジング アクティビティ中に DQS 渡します内のドメインの値、 **Address Validation**クレンジングのためのサービスにドメインをします。 参照してください[Configure DQS to Use Reference Data](http://msdn.microsoft.com/library/hh213070.aspx)詳細についてはします。  
  
1.  メイン ページで**DQS クライアント**で、**管理** ウィンドウで、をクリックして**構成**です。  
  
2.  いることを確認**参照データ**タブがアクティブにします。  
  
3.  **ネットワーク設定**領域で、型の適切な値に、**プロキシ サーバー**と**ポート**フィールドの場合は、インターネットへの接続にプロキシ サーバーを使用する必要があります。  
  
4.  型、 **Windows Azure Marketplace アカウント キー**の**DataMarket のアカウント ID**フィールドです。  
  
     ![Azure Data Market 参照データ サービスのアカウント](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Azure Data Market 参照データ サービスのアカウント")  
  
5.  をクリックして**検証**アカウント ID を検証するテキスト ボックスの横にあるボタンをクリックします。  
  
6.  をクリックして**OK**メッセージ ボックスにします。  
  
7.  をクリックして**閉じる**DQS クライアントのメイン ページに切り替えるには、ページの下部にあります。  
  
## <a name="next-task"></a>次の作業  
 [タスク 10: 参照データ サービスを使用して複合ドメインを構成する](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  