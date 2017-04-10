---
title: "Oracle パブリッシングの用語 | Microsoft Docs"
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
  - "Oracle パブリッシング [SQL Server レプリケーション]、用語集"
ms.assetid: e21dfa4b-6144-4be7-9cbf-ca2709b2bd9f
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# Oracle パブリッシングの用語
  Oracle パブリッシングの構成および管理を行う場合には、以下に示す Oracle の用語を理解している必要があります。 Oracle の用語の完全な一覧については、Oracle のオンライン マニュアルを参照してください。  
  
 索引構成表 (IOT)  
 データが含まれるがディスク上のインデックスの順序で並べ替えられた物理的にテーブルに似ていますが、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クラスター化インデックスを含むテーブル。 IOT はクラスター化インデックス付きテーブルとしてサブスクライバーにレプリケートされます。  
  
 インスタンス  
 Oracle データベースはインスタンスに関連付けられています。 このインスタンスは、メモリ、およびデータベースをサポートするバックグラウンド プロセスから構成されます。 Oracle のインスタンスは常に単一のデータベースにマッピングされます。一方、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスには複数のデータベースを格納できます。 状況によっては、1 つの Oracle データベースに複数のインスタンスを持たせることもできます。  
  
 Oracle リスナー  
 Oracle データベース インスタンスの受信ネットワーク トラフィックを処理します。 Oracle データベースへのネットワーク接続を構成する場合、トラフィックの送信に使用するプロトコルと、リスナーがトラフィックを受信待ちするポートを指定します。 通常の構成ではリスナーは Oracle データベースのインスタンスと同一のコンピューター上で実行されます。リスナーは 1 つ以上のインスタンスに対し機能するように構成できます。  
  
 ROWID  
 データベースの特定の行の位置を示すポインターです。 テーブル スキャンやインデックスよりも ROWID を使用する方が行を高速に取得できるため、レプリケーションではパブリッシュされたテーブルの変更を処理する際、一時的に ROWID が使用されます。  
  
 Sequence  
 一意の数値を生成するためのデータベース オブジェクトです。 レプリケーションではシーケンスを使用して、パブリッシュされたテーブルへの変更を順序付けします。  
  
 SQL\*Plus  
 Oracle データベースへのアクセスおよび照会に使用されるアプリケーションです。 に似ていますが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sqlcmd**します。  
  
 シノニム  
 オブジェクトの別名です。 特殊なパブリック シノニム **MSSQLSERVERDISTRIBUTOR** が Oracle パブリッシャーを構成するときに自動的に作成します。 シノニムの参照、 **HREPL_Distributor** テーブルへの論理ポインターが表示され、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューター、パブリッシャーにサービスをします。  
  
 Oracle データベースがパブリッシュされた後で、別の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターを使用するようにパブリッシャーを構成することはできません。これは、パブリッシャーにサービスを提供するように既に構成されている特定のディストリビューターが、このパブリック シノニムによって識別されるためです。  
  
 テーブルスペース  
 データベース領域の単位で、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のファイル グループにほぼ等しい意味です。  
  
 TNS サービス名  
 TNS (Transparent Network Substrate) とは、Oracle データベースが使用する通信層です。 TNS サービス名は、ネットワーク上での Oracle データベース インスタンスの名前です。 TNS サービス名は、Oracle データベースへの接続を構成するときに割り当てます。 レプリケーションでは TNS サービス名を使用してパブリッシャーを識別し、接続を確立します。  
  
 ユーザー スキーマ  
 ユーザー スキーマは、特定のデータベース オブジェクトのセットを所有するデータベース ユーザーとして考えることができます。 レプリケーション管理ユーザー スキーマによって作成されたすべてのオブジェクトを所有している、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーションが Oracle データベースでの処理、 **MSSQLSERVERDISTRIBUTOR** パブリック シノニム。  
  
## 参照  
 [Oracle パブリッシャーの構成](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oracle パブリッシャー上で作成されたオブジェクト](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md)   
 [SQL Server 以外のパブリッシャー](../../../relational-databases/replication/non-sql/non-sql-server-publishers.md)   
 [Oracle パブリッシングの概要](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  