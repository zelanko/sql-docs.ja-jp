---
title: 'レッスン 3: マージ パブリケーションへのサブスクリプションの同期 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 63d8f82d207a985bac34b5c9a9be3273bb84ef7d
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000395"
---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a>レッスン 3:マージ パブリケーションへのサブスクリプションの同期
  このレッスンでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でマージ エージェントを起動して、サブスクリプションを初期化します。 この手順を使用して、パブリッシャーと同期することもできます。 このレッスンを始める前に、前のレッスンの「 [レッスン 2: マージ パブリケーションへのサブスクリプションの作成](lesson-2-creating-a-subscription-to-the-merge-publication.md)」を完了している必要があります。  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>同期を開始しサブスクリプションを初期化するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続し、サーバー ノードを展開して、 **[レプリケーション]** フォルダーを展開します。  
  
2.  **[ローカル サブスクリプション]** フォルダーで、 **SalesOrdersReplica** データベースのサブスクリプションを右クリックし、 **[同期の状態の表示]** をクリックします。  
  
3.  **[開始]** をクリックして、サブスクリプションを初期化します。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、マージ エージェントを実行し、同期の開始とサブスクリプションの初期化を行いました。 パブリッシャーまたはサブスクライバー側で、 **SalesOrderHeader** テーブルまたは **SalesOrderDetail** テーブルに対しデータの挿入、変更、削除を行い、ネットワーク接続が使用できるときにこの手順でパブリッシャーとサブスクライバーの間のデータを同期した後、もう一方のサーバーの **SalesOrderHeader** テーブルまたは **SalesOrderDetail** テーブルにクエリを実行すると、レプリケートされた変更を確認することができます。  
  
 以上で、モバイル クライアントとの間のデータのレプリケーションに関するチュートリアルは完了です。 トランザクション レプリケーションを使用する類似のチュートリアルとして、「 [Tutorial: Replicating Data Between Continuously Connected Servers](tutorial-replicating-data-between-continuously-connected-servers.md)」も参照してください。  
  
## <a name="see-also"></a>参照  
 [スナップショットを使用したサブスクリプションの初期化](initialize-a-subscription-with-a-snapshot.md)   
 [データの同期](synchronize-data.md)   
 [プル サブスクリプションの同期](synchronize-a-pull-subscription.md)  
  
  
