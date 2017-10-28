---
title: "SQL Server (DB2ToSQL) にデータベース オブジェクトを読み込み、変換された |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f74e15c261041ae0a68152417955a81ed96994f8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="loading-converted-database-objects-into-sql-server-db2tosql"></a>SQL Server (DB2ToSQL) にデータベース オブジェクトを変換後の読み込み
DB2 スキーマを変換した後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に結果として得られる、データベース オブジェクトを読み込むことができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 SSMA は、オブジェクトを作成したか、またはオブジェクトのスクリプトを作成して、スクリプトを実行します。 SSMA によりの実際の内容で対象のメタデータを更新する、また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
## <a name="choosing-between-synchronization-and-scripts"></a>同期とスクリプトの選択  
変換後のデータベース オブジェクトを読み込む場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]改変の有無は、SSMA を直接作成またはデータベース オブジェクトを再作成を持つことができます。 そのメソッドは、迅速かつ簡単がのカスタマイズを許可しておらず、[!INCLUDE[tsql](../../includes/tsql_md.md)]を定義するコード、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ストアド プロシージャ以外のオブジェクト。  
  
変更する場合、[!INCLUDE[tsql](../../includes/tsql_md.md)]オブジェクトを作成またはオブジェクトの作成より詳細に制御する場合は、SSMA を使用して、スクリプトを作成するに使用されます。 これらのスクリプトを変更して、個別に、各オブジェクトを作成しを使用しても[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェントがそれらのオブジェクトを作成するスケジュールを設定します。  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>SSMA を使用して、SQL server オブジェクトを同期するには  
SSMA を使用して作成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースがオブジェクト内のオブジェクトを選択する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーを持つオブジェクトを同期し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]次の手順で示すように、します。 既定では、オブジェクトは存在する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SSMA メタデータが内のオブジェクトよりも新しい場合および[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SSMA 内のオブジェクト定義が変更されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 編集して既定の動作を変更することができます**プロジェクト設定**です。  
  
> [!NOTE]  
> 既存の選択[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース DB2 データベースから変換されたオブジェクト。 ただし、これらのオブジェクトを再作成またはされません SSMA によって変更します。  
  
**SQL server オブジェクトを同期するには**  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーで、上部の展開[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ノード、順に展開**データベース**です。  
  
2.  処理するオブジェクトを選択します。  
  
    -   完全なデータベースを同期するために、データベース名の横にあるチェック ボックスを選択します。  
  
    -   個々 のオブジェクトまたはオブジェクトのカテゴリの省略を同期したり、オンまたはオブジェクトまたはフォルダーの横にあるチェック ボックスをオフにします。  
  
3.  処理するオブジェクトを選択したら[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーを右クリックして**データベース**、順にクリック**データベースと同期する**です。  
  
    オブジェクトまたはその親フォルダーを右クリックし、をクリックして、個々 のオブジェクトまたはオブジェクトのカテゴリに分類を同期することも**データベースと同期する**です。  
  
    その後は、SSMA が表示されます、**データベースと同期する**ダイアログ ボックスで、2 つのアイテムのグループを確認できます。 左側にあるは、SSMA は、ツリーで表される選択したデータベース オブジェクトを示します。 右側にある、SSMA メタデータで同じオブジェクトを表すツリーを表示できます。 ことができます、右または左をクリックして、ツリーを展開 ' +' ボタンをクリックします。 同期の方向は、2 つのツリーの間に配置アクション 列に表示されます。  
  
    アクション サインインすると、3 つの状態があります。  
  
    -   左向きの矢印は、メタデータの内容は、データベース (既定) に保存されますを意味します。  
  
    -   右向きの矢印は、データベースの内容は、SSMA メタデータを上書きを意味します。  
  
    -   バツ印は、アクションは実行されません。 を意味します。  
  
状態を変更するアクションの記号をクリックします。 クリックすると、実際の同期が実行されます**OK**のボタン、**データベースと同期する**ダイアログ。  
  
## <a name="scripting-objects"></a>オブジェクトのスクリプト作成  
保存する[!INCLUDE[tsql](../../includes/tsql_md.md)]定義の変換後のデータベース オブジェクトまたはオブジェクトの定義を変更およびスクリプトを実行、保存できます変換後のデータベース オブジェクトの定義を[!INCLUDE[tsql](../../includes/tsql_md.md)]スクリプト。  
  
**オブジェクトをスクリプトとして保存するには**  
  
1.  スクリプトを保存するオブジェクトを選択したら右**データベース**、順にクリック**スクリプトとして保存**です。  
  
    また、オブジェクトまたはその親フォルダーを右クリックし、をクリックして個々 のオブジェクトまたはオブジェクトのカテゴリをスクリプト**スクリプトとして保存**です。  
  
2.  **名前を付けて保存** ダイアログ ボックスで、ファイル名を入力、スクリプトを保存フォルダーを探し、**ファイル名**ボックスで、し[!INCLUDE[clickOK](../../includes/clickok_md.md)]です。 SSMA では、.sql というファイル名拡張子を追加します。  
  
### <a name="modifying-scripts"></a>スクリプトを変更します。  
保存した後、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]使用する 1 つまたは複数のスクリプトとしてオブジェクトの定義、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]を表示して、スクリプトを変更します。  
  
**スクリプトを変更するには**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **ファイル**メニューのをポイント**開く**、順にクリック**ファイル**です。  
  
2.  **開く**ダイアログ ボックスでは、スクリプト ファイルを選択し、okをクリックします。
  
3.  クエリ エディターを使用して、スクリプト ファイルを編集します。  
  
    クエリ エディターの詳細についてを参照してください"エディター利便性のためのコマンドと機能[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
4.  ファイル メニューの スクリプトを保存する**保存**です。  
  
### <a name="running-scripts"></a>スクリプトを実行します。  
スクリプト、または個々 のステートメントを実行できます[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]です。  
  
**スクリプトを実行するには**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **ファイル**メニューのをポイント**開く**、順にクリック**ファイル**です。  
  
2.  **開く** ダイアログ ボックスで、スクリプト ファイルを選択し、[!INCLUDE[clickOK](../../includes/clickok_md.md)]  
  
3.  完全なスクリプトを実行するキーを押して、 **f5 キーを押して**キー。  
  
4.  一連のステートメントを実行するクエリ エディター ウィンドウで、ステートメントを選択し、キーを押します、 **f5 キーを押して**キー。  
  
クエリ エディターを使用してスクリプトを実行する方法の詳細については、次を参照してください。"[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] [!INCLUDE[tsql](../../includes/tsql_md.md)]クエリ"で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
使用して、コマンドラインからスクリプトを実行することも、 **sqlcmd**ユーティリティとの間、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェントです。 詳細については**sqlcmd**、"sqlcmd ユーティリティ"を参照してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。 詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェントを参照してください"管理タスクを自動化する ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェント)"で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="securing-objects-in-sql-server"></a>SQL Server のオブジェクトのセキュリティ保護  
変換後のデータベース オブジェクトを読み込んだ後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、付与し、それらのオブジェクトに対する権限を拒否することができます。 そのために移行する前にことをお勧めするデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 セキュリティで保護する方法に関する情報内のオブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、「セキュリティの考慮事項のデータベースとデータベース アプリケーション」を参照してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順が、 [SQL Server 内の DB2 データの移行](http://msdn.microsoft.com/en-us/86cbd39f-6dac-409a-9ce1-7dd54403f84b)です。  
  
## <a name="see-also"></a>参照  
[SQL Server &#40;DB2ToSQL"&"#41; への DB2 データの移行](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  

