---
title: "既定のスナップショットの場所の指定 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "スナップショット [SQL Server レプリケーション], 既定の場所"
  - "既定のスナップショットの場所"
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# 既定のスナップショットの場所の指定 (SQL Server Management Studio)
  上のスナップショットの既定の場所の指定、 **スナップショット フォルダー** ディストリビューションの構成ウィザードのページです。 このウィザードの使用に関する詳細については、次を参照してください。 [パブリッシングとディストリビューション](../../relational-databases/replication/configure-publishing-and-distribution.md)します。 ディストリビューターとして構成されていないサーバーでパブリケーションを作成する場合は、スナップショットの既定の場所を指定で、 **スナップショット フォルダー** パブリケーションの新規作成ウィザードのページです。 このウィザードの使用に関する詳細については、次を参照してください。 [パブリケーションを作成](../../relational-databases/replication/publish/create-a-publication.md)します。  
  
 スナップショットの既定の場所を変更、 **パブリッシャー** のページ、 **ディストリビューターのプロパティ - \< ディストリビューター>** ] ダイアログ ボックス。 詳細については、次を参照してください。 [表示と変更のディストリビューターとパブリッシャーのプロパティ](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)します。 内の各パブリケーションのスナップショット フォルダーの設定、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 詳しくは、「 [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」をご覧ください。  
  
### 既定のスナップショットの場所を変更するには  
  
1.   **パブリッシャー** のページ、 **ディストリビューターのプロパティ - \< ディストリビューター>** ] ダイアログ ボックスで、[プロパティ] ボタンをクリックして (**...**) スナップショットの既定の場所を変更するパブリッシャーのです。  
  
2.   **パブリッシャーのプロパティ - \< Publisher>** ] ダイアログ ボックスで、値を入力、 **既定のスナップショット フォルダー** プロパティです。  
  
    > [!NOTE]  
    >  スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用している場合、必要があります、共有ディレクトリを指定汎用名前付け規則 (UNC) パスなど \\\computername\snapshot します。 詳細については、次を参照してください。 [スナップショット フォルダーをセキュリティで保護された](../../relational-databases/replication/security/secure-the-snapshot-folder.md)します。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## 参照  
 [スナップショット フォルダーの代替位置](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  