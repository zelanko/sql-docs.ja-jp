---
title: 入門 SSMA for MySQL (MySQLToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Getting started, MySQL metadata explorer
- Getting started, SQL Server or SQL Azure metadata explorer
- Getting started,Installing and licensing
ms.assetid: 8ebfa061-be6f-4a07-923f-8dc832a82f70
caps.latest.revision: 19
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: f7101f7c249b478524955b3d601a7b20bd178498
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getting-started-with-ssma-for-mysql-mysqltosql"></a>入門 SSMA for MySQL (MySQLToSQL)
SQL Server Migration Assistant (SSMA) for MySQL を迅速に MySQL データベース スキーマを SQL Server または Azure SQL DB のスキーマに変換、SQL Server または Azure SQL DB に結果のスキーマをアップロードおよび MySQL から SQL Server または Azure SQL DB にデータを移行することができます。  
  
このトピックでは、インストール プロセスを導入し、し SSMA ユーザー インターフェイスを理解するために役立ちます。  
  
## <a name="installing-ssma"></a>SSMA のインストール  
SSMA を使用するには、必要がありますに初めてインストールする SSMA クライアント プログラムのソースの MySQL データベースと SQL Server または Azure SQL DB のターゲット インスタンスの両方にアクセスできるコンピューター。 次に、SSMA クライアント プログラムを実行しているコンピューターに MySQL プロバイダー (MySQL 5.1 Odbc (信頼関係)) をインストールします。 インストール手順については、次を参照してください[for MySQL をインストールする SSMA &#40;MySqlToSql。&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
  
SSMA を起動する をクリックして**開始**、 をポイント**すべてのプログラム**、 をポイント**SQL Server Migration Assistant for MySQL**、クリックして**SQL Server Migration Assistant for MySQL**です。  
  
## <a name="ssma-for-mysql-user-interface"></a>SSMA for MySQL のユーザー インターフェイス  
SSMA がインストールされ、ライセンス後、は、SQL Server または Azure SQL DB に MySQL データベースを移行する SSMA を行うこともできます。 開始する前に、SSMA ユーザー インターフェイスを理解するのに役立ちます。 次の図は、SSMA を含むメタデータ エクスプ ローラー、メタデータ、ツールバー、出力ウィンドウ、およびエラー一覧 ウィンドウのユーザー インターフェイスを示しています。  
  
![SSMA for MySql のグラフィカル ユーザー インターフェイス](../../ssma/mysql/media/ssmaformysqlgui.gif "SSMA for MySql のグラフィカル ユーザー インターフェイス")  
  
移行を開始するには、次の必要があります。  
  
1.  新しいプロジェクトを作成します。  
  
2.  MySQL データベースに接続します。  
  
3.  接続が成功した MySQL のスキーマは、MySQL メタデータ エクスプ ローラーに表示されます。 タスクを実行するよう MySQL メタデータ エクスプ ローラーで右クリックしてオブジェクトは、SQL Server と Azure SQL DB への変換を評価するレポートを作成します。  
  
ツールバーとメニューを使用して、これらのタスクを行うこともできます。  
  
また、SQL Server のインスタンスに接続する必要があります。 接続に成功した後は、SQL Server データベースの階層は、SQL Server メタデータ エクスプ ローラーに表示されます。 MySQL スキーマを SQL Server スキーマに変換した後は、SQL Server メタデータ エクスプ ローラーで、これらの変換されたスキーマを選択し、スキーマを SQL Server と同期します。  
  
新しいプロジェクト ダイアログ ボックスのドロップダウン リストに、移行から Azure SQL DB を選択した場合は、Azure SQL DB に接続する必要があります。 接続に成功した後は、Azure SQL DB データベースの階層は、Azure SQL DB メタデータ エクスプ ローラーに表示されます。 Azure SQL DB のスキーマに MySQL スキーマを変換した後は、Azure SQL DB メタデータ エクスプ ローラーで、これらの変換されたスキーマを選択し、Azure SQL DB とスキーマを同期します。  
  
SQL Server または Azure SQL DB に変換されたスキーマを同期した後は、MySQL メタデータ エクスプ ローラーに戻っておよび MySQL のスキーマから SQL Server または Azure SQL DB データベースにデータを移行できます。  
  
これらのタスクとその実行方法の詳細については、次を参照してください。 [SQL Server - Azure SQL DB への MySQL データベースの移行&#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)です。  
  
次のセクションでは、SSMA ユーザー インターフェイスの機能を説明します。  
  
### <a name="metadata-explorers"></a>メタデータ エクスプ ローラー  
SSMA にはを参照して、MySQL および SQL Server データベースに対する操作の 2 つのメタデータ エクスプ ローラーが含まれています。  
  
### <a name="mysql-metadata-explorer"></a>MySQL メタデータ エクスプ ローラー  
MySQL メタデータ エクスプ ローラーでは、MySQL スキーマについての情報が表示されます。 MySQL メタデータ エクスプ ローラーを使用すると、次のタスクを実行できます。  
  
-   各スキーマ内のオブジェクトを参照します。  
  
-   変換に、オブジェクトを選択し、SQL Server の構文にオブジェクトを変換します。 詳細については、次を参照してください[MySQL データベースを変換する&#40;MySQLToSQL。&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
-   データ移行のためのテーブルを選択し、それらのテーブルからデータを SQL Server を移行します。 詳細については、次を参照してください[SQL Server - Azure SQL DB に MySQL のデータを移行する&#40;MySQLToSQL。&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQL Server または Azure SQL DB メタデータ エクスプ ローラー  
SQL Server または Azure SQL DB メタデータ エクスプ ローラーは、SQL Server または Azure SQL DB のインスタンスに関する情報を表示します。 SQL Server または Azure SQL DB のインスタンスに接続するときに、SSMA はそのインスタンスに関するメタデータを取得し、プロジェクト ファイルに格納します。  
  
このメタデータ エクスプ ローラーを使用して、、変換後の MySQL データベース オブジェクトを選択し、SQL Server や Azure SQL DB のインスタンスにそれらのオブジェクトを同期できます。  
  
詳細については、次を参照してください[同期 (SQL Server に MySQL/Azure SQL DB)。](http://msdn.microsoft.com/en-us/ac993a6d-0283-4823-8793-6b217677dfa3)  
  
### <a name="metadata"></a>メタデータ  
各メタデータ エクスプ ローラーの右側には、選択したオブジェクトを記述するタブが。 たとえば、MySQL メタデータ エクスプ ローラーでテーブルを選択する場合は、9 つのタブは表示:**テーブル**、 **SQL**、**型マッピング**、**データ**、**設定**、 **Charset マッピング**、 **SQL モード**、**プロパティ**、および**レポート**です。 **レポート** タブは、選択したオブジェクトを格納しているレポートを作成した後のみに情報を格納します。 SQL Server メタデータ エクスプ ローラーでテーブルを選択する場合、3 つのタブが表示されます:**テーブル**、 **SQL**と**データ**です。  
  
ほとんどのメタデータの設定とは、読み取り専用です。 ただし、次のメタデータを変更することができます。  
  
-   MySQL メタデータ エクスプ ローラーで、型のマッピング、文字セットのマッピングを SQL モードを変更することができます。 変更後の型のマッピングまたは文字セットのマッピングまたは SQL モードに変換するには、スキーマを変換する前に、変更をします。  
  
-   SQL Server メタデータ エクスプ ローラーで、[テーブル] タブで、テーブルとインデックスのプロパティを変更できます。SQL Server でこれらの変更を確認するには、これらの変更、スキーマを SQL Server に読み込む前にします。  
  
ソースまたはターゲット データベースではなく、プロジェクトのメタデータには、メタデータ エクスプ ローラーで行われた変更が反映されます。  
  
### <a name="toolbars"></a>[ツール バー]  
SSMA は 2 つのツールバー: プロジェクト ツールバー、および移行ツールバー。  
  
### <a name="the-project-toolbar"></a>プロジェクトのツールバー  
プロジェクトのツールバーには、プロジェクトで作業し、MySQL に接続し、SQL Server または Azure SQL DB に接続するためのボタンが含まれています。 これらのボタンで、コマンドのように、**ファイル**メニュー。  
  
### <a name="migration-toolbar"></a>移行のツールバー  
次の表は、移行のツール バー コマンドを示しています。  
  
|||  
|-|-|  
|**ボタン**|**関数**|  
|**レポートを作成します。**|SQL Server または Azure SQL DB のオブジェクトに、選択した MySQL オブジェクトを変換し、成功に変換されたを示すレポートを作成します。<br /><br />MySQL メタデータ エクスプ ローラーでオブジェクトが選択されている場合を除き、このコマンドは無効です。|  
|**スキーマを変換します。**|選択した MySQL オブジェクトを SQL Server または Azure SQL DB オブジェクトに変換します。<br /><br />MySQL メタデータ エクスプ ローラーでオブジェクトが選択されている場合を除き、このコマンドは無効です。|  
|**データを移行します。**|SQL Server または Azure SQL DB に、MySQL データベースからデータを移行します。 このコマンドを実行する前に、MySQL スキーマを SQL Server または Azure SQL DB のスキーマに変換しして SQL Server または Azure SQL DB に、オブジェクトを読み込む必要があります。<br /><br />MySQL メタデータ エクスプ ローラーでオブジェクトが選択されている場合を除き、このコマンドは無効です。|  
|**[停止]**|現在のプロセスを停止します。|  
  
### <a name="menus"></a>メニュー  
次の表は、SSMA メニューを表示します。  
  
|||  
|-|-|  
|**メニュー**|**Description**|  
|**ファイル**|プロジェクトで作業し、MySQL に接続し、SQL Server または Azure SQL DB に接続するためのコマンドが含まれています。|  
|**[編集]**|検索して、詳細ページにテキストを含む作業用のコマンドが含まれています。 開くには**管理ブックマーク** ダイアログの 編集 メニューの ブックマークの管理 をクリックします。 ダイアログ ボックスでは、既存のブックマークの一覧が表示されます。 ダイアログ ボックスの右側にあるボタンを使用するには、それらのブックマークを管理します。|  
|**[表示]**|含まれています、**メタデータ エクスプ ローラーの同期**コマンド。 MySQL メタデータ エクスプ ローラーと SQL Server または Azure SQL DB メタデータ エクスプ ローラーの間でオブジェクトを同期するとします。 コマンドを表示/非表示を含む、**出力**と**エラー一覧**ペインおよびオプション**レイアウト**レイアウトを管理します。|  
|**ツール**|レポートを作成、スキーマの変換、データベースから更新、オブジェクトとデータの移行、およびスクリプトとして保存するためのコマンドが含まれています。 アクセスする、**グローバル設定、プロジェクト設定の既定の**と**プロジェクト設定** ダイアログ ボックス。|  
|**ヘルプ**|SSMA のヘルプにされ、アクセスできるように、**に関する** ダイアログ ボックス。|  
  
### <a name="output-pane-and-error-list-pane"></a>出力ウィンドウとエラー一覧ウィンドウ  
**ビュー**メニュー コマンドの出力ウィンドウと [エラー一覧] ウィンドウの表示を切り替えるには。  
  
-   [出力] ペインは、SSMA からオブジェクトへの変換、オブジェクトの同期、およびデータの移行中にステータス メッセージを示します。  
  
-   エラー一覧 ウィンドウは、並べ替え可能な一覧で、エラー、警告、および情報メッセージを示します。  
  
## <a name="see-also"></a>参照  
[ユーザー インターフェイス リファレンス&#40;MySQLToSQL&#41;](../../ssma/mysql/user-interface-reference-mysqltosql.md)  
[SQL Server - Azure SQL DB に MySQL データの移行&#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
