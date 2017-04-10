---
title: "[ディストリビューターのプロパティ]、[全般] | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.configdistwizard.distproperties.general.f1"
helpviewer_keywords: 
  - "[ディストリビューターのプロパティ] ダイアログ ボックス"
ms.assetid: ab4120ec-e524-4c0c-8b48-f2f40adb1a3b
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# [ディストリビューターのプロパティ]、[全般]
   **全般** のページ、 **ディストリビューターのプロパティ** ダイアログ ボックスでは、追加し、ディストリビューション データベースを削除およびディストリビューション データベースのプロパティを設定することができます。  
  
 ディストリビューション データベースには、すべての種類のレプリケーションのメタデータと履歴データ、およびトランザクション レプリケーションのトランザクションが格納されます。 多くの場合、ディストリビューション データベースは 1 つで十分です。 ただし、複数のパブリッシャーが 1 つのディストリビューターを使用する場合、各パブリッシャーにディストリビューション データベースを作成することを検討してください。 これによって、各ディストリビューション データベースを経由するデータ フローが区別されます。  
  
## オプション  
 **データベース**  
  **データベース** 、ディストリビューター側のディストリビューション データベースの名前と保有期間のプロパティがプロパティ グリッドに表示します。 **トランザクションの保有期間** がトランザクション レプリケーションのトランザクションの期間の長さが格納されます (トランザクションの保有期間はディストリビューションの保有期間でとも呼ばれます)。 **履歴の保有期間** はあらゆる種類のレプリケーション時間履歴メタデータの長さを保存します。 ディストリビューションの保有期間の詳細については、次を参照してください。 [サブスクリプションの有効期限と非アクティブ化](../../relational-databases/replication/subscription-expiration-and-deactivation.md)します。  
  
 プロパティ ボタンをクリックして (**...**) で、 **データベース** を起動する、プロパティ グリッド、 **ディストリビューション データベースのプロパティ** ] ダイアログ ボックス。  
  
 **新規**  
 新しいディストリビューション データベースを作成します。  
  
 **Del**  
 内の既存のディストリビューション データベースを選択、 **データベース** プロパティ グリッド、およびクリック **削除** 、データベースを削除します。 ディストリビューターは少なくとも 1 つのディストリビューション データベースを持つ必要があるため、データベースが 1 つだけの場合はディストリビューション データベースを削除することはできません。 すべてのディストリビューション データベースを削除するには、コンピューターでディストリビューションを無効にする必要があります。 詳細については、次を参照してください。 [パブリッシングの無効化と配布](../../relational-databases/replication/disable-publishing-and-distribution.md)します。  
  
 **[プロファイルの既定値]**  
 [アクセスのレプリケーション エージェント プロファイルを **エージェント プロファイル** ] ダイアログ ボックス。 プロファイルの詳細については、次を参照してください。 [レプリケーション エージェント プロファイル](../../relational-databases/replication/agents/replication-agent-profiles.md)します。  
  
## 参照  
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  