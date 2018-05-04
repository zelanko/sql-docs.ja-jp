---
title: SQL Server (AccessToSQL) にデータベース オブジェクトを読み込み、変換された |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
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
- Access databases, loading converted objects into SQL Azure
- Access databases, loading converted objects into SQL Server
- data, securing
- loading objects into SQL Azure
- loading objects into SQL Server
- migrating objects into SQL Azure
- migrating objects into SQL Server
- moving objects into SQL Azure
- moving objects into SQL Server
- schemas, loading into SQL Azure
- schemas, loading into SQL Server
- scripting converted objects
- securing data
- SQL Azure, loading objects into
- SQL Server, loading objects into
- synchronizing metadata with SQL Azure
- synchronizing metadata with SQL Server
- uploading objects into SQL Azure
- uploading objects into SQL Server
ms.assetid: 4e854eee-b10c-4f0b-9d9e-d92416e6f2ba
caps.latest.revision: 16
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 2d3aa3c367ee065fb04dbe828003d0a2fa304e08
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="loading-converted-database-objects-into-sql-server-accesstosql"></a>SQL Server (AccessToSQL) にデータベース オブジェクトを変換後の読み込み
データベース オブジェクトに変換した後に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SQL Azure に作成されたデータベース オブジェクトを読み込むことができますか[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 SSMA は、オブジェクトを作成したか、またはオブジェクトのスクリプトを作成して、スクリプトを実行します。 SSMA によりの実際の内容で対象のメタデータを更新する、また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベース。  
  
## <a name="choosing-between-synchronization-and-scripts"></a>同期とスクリプトの選択  
変換後のデータベース オブジェクトを読み込む場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]加えなければ SQL Azure、SSMA を直接作成またはデータベース オブジェクトを作成し直すことができますか。 そのメソッドは、迅速かつ簡単がのカスタマイズを許可しておらず、[!INCLUDE[tsql](../../includes/tsql_md.md)]を定義するコード、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]またはストアド プロシージャ以外の SQL Azure オブジェクト。  
  
変更する場合、[!INCLUDE[tsql](../../includes/tsql_md.md)]オブジェクトを作成またはオブジェクトの作成より詳細に制御する場合は、SSMA を使用して、スクリプトを作成するに使用されます。 これらのスクリプトを変更して、個別に、各オブジェクトを作成しを使用しても[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェントがそれらのオブジェクトを作成するスケジュールを設定します。  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>SSMA を使用して、SQL server オブジェクトを同期するには  
SSMA を使用して作成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベースのオブジェクト内のオブジェクトを選択する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラー、および関係を持つオブジェクトを同期[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、次の手順で示すようにします。 既定では、オブジェクトは存在する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、SSMA メタデータがいくつかのローカルの変更または非常にそれらのオブジェクトの定義を更新、内のオブジェクト定義が変更され SSMA[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 編集して既定の動作を変更することができます**プロジェクト設定**です。  
  
> [!NOTE]  
> 既存の選択[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Access データベースから変換された SQL Azure データベースのオブジェクト。 ただし、SSMA をいないを再作成またはそれらのオブジェクトを変更します。  
  
**SQL Server または SQL Azure とオブジェクトを同期するには**  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラーで、上部の展開[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure ノードを展開し、**データベース**です。  
  
2.  処理するオブジェクトを選択します。  
  
    -   完全なデータベースを同期するために、データベース名の横にあるチェック ボックスを選択します。  
  
    -   個々 のオブジェクトまたはオブジェクトのカテゴリの省略を同期したり、オンまたはオブジェクトまたはフォルダーの横にあるチェック ボックスをオフにします。  
  
3.  処理するオブジェクトを選択した後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラーを右クリックして**データベース**、クリックして**データベースと同期する**です。  
  
    オブジェクトまたはその親フォルダーを右クリックし、をクリックして、個々 のオブジェクトまたはオブジェクトのカテゴリに分類を同期することも**データベースと同期する**です。  
  
    その後は、SSMA が表示されます、**データベースと同期する**ダイアログ ボックスで、2 つのアイテムのグループを確認できます。 左側にあるは、SSMA は、ツリーで表される選択したデータベース オブジェクトを示します。 右側にある、SSMA メタデータで同じオブジェクトを表すツリーを表示できます。 ことができます、右または左をクリックして、ツリーを展開 ' +' ボタンをクリックします。 同期の方向は、2 つのツリーの間に配置アクション 列に表示されます。  
  
    アクション サインインすると、3 つの状態があります。  
  
    -   左向きの矢印は、メタデータの内容は、データベース (既定) に保存されますを意味します。  
  
    -   右向きの矢印は、データベースの内容は、SSMA メタデータを上書きを意味します。  
  
    -   バツ印は、アクションは実行されません。 を意味します。  
  
    状態を変更するアクションの記号をクリックします。 クリックすると、実際の同期が実行されます**OK**のボタン、**データベースと同期する**ダイアログ。  
  
## <a name="scripting-objects"></a>オブジェクトのスクリプト作成  
保存する場合[!INCLUDE[tsql](../../includes/tsql_md.md)]オブジェクトの定義を変更するか、変換後のデータベース オブジェクトの定義および実行スクリプトを自分で、オブジェクトの定義を変換後のデータベースに保存する[!INCLUDE[tsql](../../includes/tsql_md.md)]スクリプト。  
  
**1 つまたは複数のオブジェクトをスクリプトに保存するには**  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーで、最上位ノード (サーバー名) を展開し、展開**データベース**です。  
  
2.  次の 1 つ以上の操作を行います。  
  
    -   データベース全体のスクリプトを作成するには、データベース名の横にあるチェック ボックスを選択します。  
  
    -   スクリプトまたは個々 のビューの省略は、データベースを展開し、**ビュー**を選択するか、ビューの横にあるチェック ボックスをオフにします。  
  
    -   スクリプトまたは個々 のテーブルの省略は、データベースを展開し、**テーブル**を選択するか、テーブルの横にあるチェック ボックスをオフにします。  
  
    -   スクリプト化または省略テーブルに複数のインデックス、テーブルを展開し、**インデックス**を選択するか、インデックスをオフにします。  
  
3.  右クリック**データベース**選択**スクリプトとして保存**です。  
  
    個々 のオブジェクトをスクリプトにすることもできます。 オブジェクトの選択に関係なく、オブジェクトのスクリプト オブジェクトを右クリックし、選択**スクリプトとして保存**です。  
  
4.  **名前を付けて保存** ダイアログ ボックスで、ファイル名を入力、スクリプトを保存フォルダーを探し、**ファイル名**ボックスし、をクリックして**OK**です。  
  
    SSMA では、.sql というファイル名拡張子を追加します。  
  
### <a name="modifying-scripts"></a>スクリプトを変更します。  
保存した後、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、オブジェクト定義としてスクリプトを使用できます[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]スクリプトを変更します。  
  
**スクリプトを変更するには**  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] **ファイル** メニューのをポイント**開く**、順にクリック**ファイル**です。  
  
2.  **開く** ダイアログ ボックスと、スクリプト ファイルの選択を見つけてクリックして**OK**です。  
  
3.  クエリ エディターを使用して、スクリプト ファイルを編集します。  
  
    クエリ エディターの詳細についてを参照してください"エディター利便性のためのコマンドと機能[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
4.  ファイル メニュー、スクリプトを保存する **保存**です。  
  
### <a name="running-scripts"></a>スクリプトを実行します。  
スクリプト、または個々 のステートメントを実行できます[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]です。  
  
**スクリプトを実行するには**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **ファイル** メニューのをポイント**開く** をクリックし、**ファイル**です。  
  
2.  **開く** ダイアログ ボックスと、スクリプト ファイルの選択を見つけてクリックして**OK**です。  
  
3.  完全なスクリプトを実行するキーを押して、 **f5 キーを押して**キー。  
  
4.  一連のステートメントを実行するクエリ エディター ウィンドウで、ステートメントを選択し、キーを押します、 **f5 キーを押して**キー。  
  
クエリ エディターを使用してスクリプトを実行する方法の詳細については、次を参照してください。"[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] [!INCLUDE[tsql](../../includes/tsql_md.md)]クエリ"で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
使用して、コマンドラインからスクリプトを実行することも、 **sqlcmd**ユーティリティ、およびから[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェントです。 詳細については**sqlcmd**、"sqlcmd ユーティリティ"を参照してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。 詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェントを参照してください"管理タスクを自動化する ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェント)"で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="securing-objects-in-sql-server"></a>SQL Server のオブジェクトのセキュリティ保護  
変換後のデータベース オブジェクトを読み込んだ後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、付与し、それらのオブジェクトに対する権限を拒否することができます。 そのために移行する前にことをお勧めするデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 セキュリティで保護する方法に関する情報内のオブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、「セキュリティの考慮事項のデータベースとデータベース アプリケーション」を参照してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順は[SQL Server にデータを移行](http://msdn.microsoft.com/en-us/f3b18af7-1af0-499d-a00d-a0af94895625)です。  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
