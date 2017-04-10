---
title: "Oracle テーブルスペースの管理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Oracle パブリッシング [SQL Server レプリケーション], テーブルスペースの管理"
  - "テーブルスペース [SQL Server レプリケーション]"
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Oracle テーブルスペースの管理
  テーブル スペース内のファイル グループとほぼ同等であるデータベースの記憶領域の単位は、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 テーブルスペースでは、個々のグループ内でデータベース オブジェクトの格納および管理が可能です。 詳細については Oracle のマニュアルを参照してください。  
  
 Oracle パブリケーションの一部としてテーブルを構成する場合、必要に応じて、レプリケーション ログ情報を格納するときに既存の Oracle テーブルスペースを使用するように指定できます。 指定しない場合、レプリケーション オブジェクトのテーブルスペースは、パブリッシャーの構成時に構成したレプリケーション管理ユーザー スキーマに関連付けられた既定のテーブルスペースとなります。  
  
 **アーティクル ログ テーブルのテーブル スペースを指定する**:  
  
-   指定のテーブル スペース、 **アーティクルのプロパティ** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
-   使用 [sp_changearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)します。 使用する **sp_changearticle**, 、以下を指定します。  
  
    -   パラメーターの Oracle パブリッシャーの名前 **@publisher**します。  
  
    -   パラメーターの Oracle パブリケーションの名前 **@publication**します。  
  
    -   アーティクルの名前をパラメーターに **@article**します。  
  
    -   パラメーターには、「tablespace」の値 **@property**します。  
  
    -   パラメーターのテーブル スペースの名前 **@value**します。  
  
## 参照  
 [Oracle パブリッシャーの構成](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oracle パブリッシャー上で作成されたオブジェクト](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md)  
  
  