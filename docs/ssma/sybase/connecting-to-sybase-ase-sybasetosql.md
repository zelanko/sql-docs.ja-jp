---
title: Sybase ASE (SybaseToSQL) への接続 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Connecting to Sybase ASE
ms.assetid: a45a2330-9175-4c9e-af38-ef920e350614
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 3cc8ebc1e0a4250ef29f307cf6c1b5fa45b9be6c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-sybase-ase-sybasetosql"></a>Sybase ASE (SybaseToSQL) に接続します。
Sybase Adaptive Server Enterprise (ASE) データベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure に移行するデータベースを含むアダプティブ サーバーに接続する必要があります。 接続するときに、SSMA は、アダプティブ サーバー上のすべてのデータベースに関するメタデータを取得し、Sybase メタデータ エクスプ ローラー ペインでデータベースのメタデータを表示します。 SSMA は、データベース サーバーに関する情報を格納しますが、パスワードは保存されません。  
  
プロジェクトを閉じるまで ASE への接続をアクティブに保ちます。 プロジェクトを再度開くと、アクティブなサーバーに接続する場合 ASE に再接続する必要があります。  
  
アダプティブ サーバーについてのメタデータは自動的に更新されません。 代わりに、Sybase メタデータ エクスプ ローラー内のメタデータを更新する場合は、する必要があります手動で更新するメタデータ、このトピックの「「Sybase ASE メタデータの更新」セクションで説明します。  
  
## <a name="required-ase-permissions"></a>必要な ASE アクセス許可  
ASE への接続に使用されるアカウントが少なくとも必要**パブリック**に移行するソース データベースおよび master データベースにアクセス[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 さらは、移行対象のテーブルに対する権限を選択するには、ユーザー SELECT 権限が必要で、次のシステム テーブル。  
  
-   [source_db].dbo.sysobjects  
  
-   [source_db].dbo.syscolumns  
  
-   [source_db].dbo.sysusers  
  
-   [source_db].dbo.systypes  
  
-   [source_db].dbo.sysconstraints  
  
-   [source_db].dbo.syscomments  
  
-   [source_db].dbo.sysindexes  
  
-   [source_db].dbo.sysreferences  
  
-   master.dbo.sysdatabases  
  
## <a name="establishing-a-connection-to-ase"></a>ASE への接続を確立します。  
アダプティブ サーバーに接続して SSMA は、データベース サーバーで、データベース メタデータを読み取ってプロジェクト ファイルにこのメタデータが追加されます。 このメタデータは、オブジェクトに変換するとき、SSMA によって使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の構文にデータを移行したときと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 Sybase メタデータ エクスプ ローラー ウィンドウでこのメタデータを参照して、個々 のデータベース オブジェクトのプロパティを確認できます。  
  
> [!IMPORTANT]  
> データベース サーバーに接続しようとすると、前に、データベース サーバーが実行されているとが接続を受け入れることを確認します。  
  
**Sybase ASE に接続するには**  
  
1.  **ファイル**メニューの  **Sybase への接続**です。  
  
    Sybase に接続されていた場合、コマンド名になります**sybase 再接続**です。  
  
2.  **プロバイダー**ボックスで、Sybase サーバーに接続するコンピューターにインストールされているプロバイダーのいずれかを選択します。  
  
3.  **モード**ボックスで、いずれかを選択**標準モード**または**高度なモード**です。  
  
    標準モードを使用すると、サーバー名、ポート、ユーザー名とパスワードを指定します。 詳細設定モードを使用すると、接続文字列を指定します。 このモードは通常、トラブルシューティングやテクニカル サポートの操作にのみ使用します。  
  
4.  選択した場合**標準モード**の値を指定します。  
  
    1.  **サーバー名**ボックスで、入力するか、またはデータベース サーバーの IP アドレスを選択します。  
  
    2.  既定値 (5000) のポートでは、Sybase 接続で使用されるポート番号を入力に接続を受け入れるように、データベース サーバーが構成されていない場合、**サーバー ポート**ボックス。  
  
    3.  **ユーザー名**ボックスに、必要なアクセス許可のある Sybase アカウントを入力します。  
  
    4.  **パスワード**ボックスで、指定されたユーザー名のパスワードを入力します。  
  
5.  選択した場合**高度なモード**での接続文字列を指定、**接続文字列**ボックス。  
  
    別の接続文字列の例は次のとおりです。  
  
    1.  **Sybase OLE DB プロバイダーの接続文字列:**  
  
        Sybase ASE OLE DB 12.5 の接続文字列の例のとおりです。  
  
        `Server Name=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=Sybase.ASEOLEDBProvider;`  
  
        For Sybase ASE OLE DB 15、接続文字列の例のとおりです。  
  
        `Server=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider= ASEOLEDB;Port=5000;`  
  
    2.  **Sybase ODBC プロバイダーの接続文字列:**  
  
        `Driver=Adaptive Server Enterprise;Server=sybserver;uid=MyUserID;pwd=MyP@$$word;Port=5000;`  
  
    3.  **Sybase ADO.NET プロバイダーの接続文字列:**  
  
        `Server=sybserver;Port=5000;uid=MyUserID;pwd=MyP@$$word;`  
  
    詳細については、次を参照してください。 [Sybase への接続&#40;SybaseToSQL&#41;](../../ssma/sybase/connect-to-sybase-sybasetosql.md)です。  
  
## <a name="reconnecting-to-sybase-ase"></a>Sybase ASE への再接続  
プロジェクトを終了するまで、データベース サーバーへの接続をアクティブに保ちます。 プロジェクトを再度開くと、アダプティブ サーバーにアクティブに接続する場合を再接続する必要があります。 メタデータを更新するには、データベース オブジェクトに読み込む必要がなくなるまでオフラインで作業できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure とデータを移行します。  
  
## <a name="refreshing-sybase-ase-metadata"></a>Sybase ASE メタデータの更新  
ASE データベースについてのメタデータは、自動的に更新されません。 Sybase メタデータ エクスプ ローラー内のメタデータは、アダプティブ サーバー、または前回のメタデータを手動で更新することを最初に接続したときのメタデータのスナップショットです。 1 つのデータベース、1 つのデータベース スキーマ、またはすべてのデータベースのメタデータを手動で更新することができます。  
  
**メタデータを更新するには**  
  
1.  アダプティブ サーバーに接続していることを確認します。  
  
2.  Sybase メタデータ エクスプ ローラーで、データベースまたは更新するデータベース スキーマの横にあるチェック ボックスを選択します。  
  
3.  データベースまたは個々 のデータベースまたはデータベース スキーマを右クリックし、**データベースから更新**です。  
  
4.  現在のオブジェクトを確認するメッセージが表示されたら、クリックして**はい**です。  
  
## <a name="next-step"></a>次の手順  
  
-   移行プロセスの次の手順が、 [SQL Server のインスタンスへの接続](http://msdn.microsoft.com/en-us/dd368a1a-45b0-40e9-b4d3-5cdb48c26606) / [SQL Azure のインスタンスに接続します。](http://msdn.microsoft.com/en-us/9e77e4b0-40c0-455c-8431-ca5d43849aa7)  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40;への Sybase ASE データベースの移行SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
