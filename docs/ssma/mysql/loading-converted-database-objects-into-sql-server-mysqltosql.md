---
title: SQL Server (MySQLToSQL) にデータベース オブジェクトを読み込み、変換された |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
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
ms.assetid: ac993a6d-0283-4823-8793-6b217677dfa3
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 3d96528033ab2f852be1e91e64efdda77eb3807a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="loading-converted-database-objects-into-sql-server-mysqltosql"></a>SQL Server (MySQLToSQL) にデータベース オブジェクトを変換後の読み込み
MySQL データベースを変換した後に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SQL Azure に作成されたデータベース オブジェクトを読み込むことができますか[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 SSMA は、オブジェクトを作成したか、またはオブジェクトのスクリプトを作成して、スクリプトを実行します。 SSMA によりの実際の内容で対象のメタデータを更新する、また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベース。  
  
## <a name="choosing-between-synchronization-and-scripts"></a>同期とスクリプトの選択  
変換後のデータベース オブジェクトを読み込む場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]加えなければ SQL Azure、SSMA を直接作成またはデータベース オブジェクトを作成し直すことができますか。 メソッドは迅速かつ簡単ですを定義する TRANSACT-SQL コードのカスタマイズを許容しないこと、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure オブジェクト。  
  
オブジェクトを作成するために使用する Transact SQL を変更する場合、またはオブジェクトの作成をより細かく制御する場合は、SSMA を使用してスクリプトを作成します。 これらのスクリプトを変更、各オブジェクトを個別に、作成、およびでも SQL Server エージェントを使用してこれらのオブジェクトを作成するスケジュールを設定することができます。  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>SSMA を使用して、SQL server オブジェクトを同期するには  
内のオブジェクトを選択する SSMA を使用して、SQL Server または SQL Azure のデータベース オブジェクトを作成する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラー、および関係を持つオブジェクトを同期[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、次の手順で示すようにします。 既定では、オブジェクトは存在する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、SSMA メタデータがいくつかのローカルの変更または非常にそれらのオブジェクトの定義を更新、内のオブジェクト定義が変更され SSMA[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 編集して既定の動作を変更することができます**プロジェクト設定**です。  
  
> [!NOTE]  
> 既存の選択[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または MySQL データベースから変換された SQL Azure データベースのオブジェクト。 ただし、これらのオブジェクトを再作成またはされません SSMA によって変更します。  
  
##### <a name="to-synchronize-objects-with-sql-server-or-sql-azure"></a>SQL Server または SQL Azure とオブジェクトを同期するには  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラーで、上部の展開[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure ノードを展開し、**データベース**です。  
  
2.  処理するオブジェクトを選択します。  
  
    -   完全なデータベースを同期するために、データベース名の横にあるチェック ボックスを選択します。  
  
    -   個々 のオブジェクトまたはオブジェクトのカテゴリの省略を同期したり、オンまたはオブジェクトまたはフォルダーの横にあるチェック ボックスをオフにします。  
  
3.  SQL Server または SQL Azure メタデータ エクスプ ローラーで処理するオブジェクトを選択したら右**データベース**、順にクリック**データベースと同期する**です。  
  
    オブジェクトまたはその親フォルダーを右クリックし、をクリックして、個々 のオブジェクトまたはオブジェクトのカテゴリに分類を同期することも**データベースと同期する**です。  
  
    その後は、SSMA が表示されます、**データベースと同期する**ダイアログ ボックスで、2 つのアイテムのグループを確認できます。 左側にあるは、SSMA は、ツリーで表される選択したデータベース オブジェクトを示します。 右側にある、SSMA メタデータで同じオブジェクトを表すツリーを表示できます。 ことができます、右または左をクリックして、ツリーを展開 ' +' ボタンをクリックします。 同期の方向は、2 つのツリーの間に配置アクション 列に表示されます。  
  
    アクション サインインすると、次の 3 つの状態があります。  
  
    -   左向きの矢印は、メタデータの内容は、データベース (既定) に保存されますを意味します。  
  
    -   右向きの矢印は、データベースの内容は、SSMA メタデータを上書きを意味します。  
  
    -   バツ印は、アクションは実行されません。 を意味します。  
  
    -   状態を変更するアクションの記号をクリックします。 クリックすると、実際の同期が実行されます**OK**のボタン、**データベースと同期する**ダイアログ。  
  
## <a name="scripting-objects"></a>オブジェクトのスクリプト作成  
保存する[!INCLUDE[tsql](../../includes/tsql_md.md)]定義の変換後のデータベース オブジェクトまたはオブジェクトの定義を変更およびスクリプトを実行、保存できます変換後のデータベース オブジェクトの定義を[!INCLUDE[tsql](../../includes/tsql_md.md)]スクリプト。  
  
**オブジェクトをスクリプトとして保存するには**  
  
1.  スクリプトを保存するオブジェクトを選択したら右**データベース**、順にクリック**スクリプトとして保存**です。  
  
    また、オブジェクトまたはその親フォルダーを右クリックし、をクリックして個々 のオブジェクトまたはオブジェクトのカテゴリをスクリプト**スクリプトとして保存**です。  
  
2.  **名前を付けて保存** ダイアログ ボックスで、ファイル名を入力、スクリプトを保存フォルダーを探し、**ファイル名**ボックスで、し[!INCLUDE[clickOK](../../includes/clickok_md.md)]SSMA .sql というファイル名拡張子が追加されます。  
  
### <a name="modifying-scripts"></a>スクリプトを変更します。  
スクリプトとして SQL Server または SQL Azure オブジェクトの定義を保存した後は、スクリプトを修正するのに SQL Server Management Studio を使用することができます。  
  
**スクリプトを変更するには**  
  
1.  Management Studio で**ファイル** メニューのをポイント**開く**、順にクリック**ファイル**です。  
  
2.  [開く] ダイアログ ボックスと、スクリプト ファイルの選択を見つけてクリックして**OK**です。  
  
3.  クエリ エディターを使用して、スクリプト ファイルを編集します。クエリ エディターの詳細については、"エディター利便性のためのコマンドと機能 で SQL Server オンライン ブックを参照してください。  
  
4.  ファイル メニュー、スクリプトを保存する **保存**です。  
  
### <a name="running-scripts"></a>スクリプトを実行します。  
SQL Server Management Studio では、スクリプト、または個々 のステートメントを実行できます。  
  
**スクリプトを実行するには**  
  
1.  SQL Server Management Studio で**ファイル** メニューのをポイント**開く** をクリックし、**ファイル**です。  
  
2.  [開く] ダイアログ ボックスと、スクリプト ファイルの選択を見つけてクリックして**OK**です。  
  
3.  完全なスクリプトを実行するキーを押して、 **f5 キーを押して**キー。  
  
4.  一連のステートメントを実行するクエリ エディター ウィンドウで、ステートメントを選択し、キーを押します、 **f5 キーを押して**キー。  
  
5.  クエリ エディターを使用してスクリプトを実行する方法の詳細については、「SQL Server Management Studio TRANSACT-SQL クエリ」SQL Server オンライン ブックを参照してください。  
  
6.  使用して、コマンドラインからスクリプトを実行することも、 **sqlcmd**ユーティリティ、および SQL Server エージェントからです。 詳細については**sqlcmd**、SQL Server オンライン ブックの"sqlcmd ユーティリティ"を参照してください。 SQL Server エージェントの詳細については、「管理タスクを自動化する (SQL Server エージェント)」で SQL Server オンライン ブックを参照してください。  
  
## <a name="securing-objects-in-sql-server"></a>SQL Server のオブジェクトのセキュリティ保護  
変換後のデータベース オブジェクトは、SQL Server に読み込まれたが後、は、付与し、これらのオブジェクトに対する権限の拒否できます。 そのために移行する前にことをお勧めデータを SQL Server。 SQL Server のセキュリティで保護されたオブジェクトを保護する方法については、「セキュリティの考慮事項のデータベースとデータベース アプリケーションの」SQL Server オンライン ブックを参照してください。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順は[SQL Server - Azure SQL DB に MySQL のデータを移行する&#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB にデータベースを移行する MySQL &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
