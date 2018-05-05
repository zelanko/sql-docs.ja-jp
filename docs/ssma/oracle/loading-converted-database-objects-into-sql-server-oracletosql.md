---
title: SQL Server (OracleToSQL) にデータベース オブジェクトを読み込み、変換された |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Synchronization, Securing Objects in SQL Server
- Synchronization,Scripting Objects
ms.assetid: a8ae33b2-1883-4785-922b-ea0e31c0b37a
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 77ff748a71f976755718d1bcd9cd4fa2b8923b39
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="loading-converted-database-objects-into-sql-server-oracletosql"></a>SQL Server (OracleToSQL) にデータベース オブジェクトを変換後の読み込み
Oracle スキーマを SQL Server に変換すると、SQL Server に結果のデータベース オブジェクトを読み込むことができます。 SSMA は、オブジェクトを作成したか、またはオブジェクトのスクリプトを作成して、スクリプトを実行します。 また、SSMA には、SQL Server データベースの実際の内容で対象のメタデータを更新することができます。  
  
## <a name="choosing-between-synchronization-and-scripts"></a>同期とスクリプトの選択  
SQL Server に変更しなくても、変換後のデータベース オブジェクトを読み込む場合は、SSMA を直接作成またはデータベース オブジェクトを再作成を持つことができます。 メソッドは迅速かつ簡単ですがのカスタマイズを許容しないこと、[!INCLUDE[tsql](../../includes/tsql_md.md)]ストアド プロシージャ以外の SQL Server オブジェクトを定義するコードです。  
  
変更する場合、[!INCLUDE[tsql](../../includes/tsql_md.md)]オブジェクトを作成またはオブジェクトの作成より詳細に制御する場合は、SSMA を使用して、スクリプトを作成するに使用されます。 これらのスクリプトを変更、個別に、各オブジェクトを作成、およびでも SQL Server エージェントを使用してそれらのオブジェクトを作成するスケジュールを設定することができます。  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>SSMA を使用して、SQL server オブジェクトを同期するには  
SSMA を使用して SQL Server データベース オブジェクトを作成するには、SQL Server メタデータ エクスプ ローラーで、オブジェクトを選択し、次の手順で示すように SQL Server でのオブジェクトを同期します。 既定では、SQL Server で、オブジェクトが存在しない場合や SSMA メタデータは、SQL Server 内のオブジェクトよりも新しい場合 SSMA は変わるオブジェクト定義と、SQL Server。 編集して既定の動作を変更することができます**プロジェクト設定**です。  
  
> [!NOTE]  
> Oracle データベースからに変換されなかった既存の SQL Server データベース オブジェクトを選択することができます。 ただし、これらのオブジェクトを再作成またはされません SSMA によって変更します。  
  
**SQL server オブジェクトを同期するには**  
  
1.  SQL Server メタデータ エクスプ ローラーで、最上位の SQL Server ノードを展開し、展開**データベース**です。  
  
2.  処理するオブジェクトを選択します。  
  
    -   完全なデータベースを同期するために、データベース名の横にあるチェック ボックスを選択します。  
  
    -   個々 のオブジェクトまたはオブジェクトのカテゴリの省略を同期したり、オンまたはオブジェクトまたはフォルダーの横にあるチェック ボックスをオフにします。  
  
3.  SQL Server メタデータ エクスプ ローラーで処理するオブジェクトを選択したら右**データベース**、順にクリック**データベースと同期する**。  
  
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
  
2.  **名前を付けて保存** ダイアログ ボックスで、ファイル名を入力、スクリプトを保存フォルダーを探し、**ファイル名**ボックスをクリックして OK SSMA .sql というファイル名拡張子が追加されます。  
  
### <a name="modifying-scripts"></a>スクリプトを変更します。  
SQL Server オブジェクトの定義に、1 つ以上のスクリプトを保存して、後に行うこともできます[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]を表示して、スクリプトを変更します。  
  
**スクリプトを変更するには**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **ファイル** メニューのをポイント**開く**、順にクリック**ファイル**です。  
  
2.  **開く**ダイアログ ボックスでは、スクリプト ファイルを選択し、[ok] をクリックします。
  
3.  クエリ エディターを使用して、スクリプト ファイルを編集します。  
  
    クエリ エディターの詳細については、"エディター利便性のためのコマンドと機能 で SQL Server オンライン ブックを参照してください。  
  
4.  ファイル メニューの スクリプトを保存する**保存**です。  
  
### <a name="running-scripts"></a>スクリプトを実行します。  
スクリプト、または個々 のステートメントを実行できます[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]です。  
  
**スクリプトを実行するには**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **ファイル** メニューのをポイント**開く**、順にクリック**ファイル**です。  
  
2.  **開く**ダイアログ ボックスでは、スクリプト ファイルを選択し、[ok] をクリックして  
  
3.  完全なスクリプトを実行するキーを押して、 **f5 キーを押して**キー。  
  
4.  一連のステートメントを実行するクエリ エディター ウィンドウで、ステートメントを選択し、キーを押します、 **f5 キーを押して**キー。  
  
クエリ エディターを使用してスクリプトを実行する方法の詳細については、次を参照してください。"[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] [!INCLUDE[tsql](../../includes/tsql_md.md)]クエリ"SQL Server オンライン ブック。  
  
使用して、コマンドラインからスクリプトを実行することも、 **sqlcmd**ユーティリティ、および SQL Server エージェントからです。 詳細については**sqlcmd**、SQL Server オンライン ブックの"sqlcmd ユーティリティ"を参照してください。 SQL Server エージェントの詳細については、「管理タスクを自動化する (SQL Server エージェント)」で SQL Server オンライン ブックを参照してください。  
  
## <a name="securing-objects-in-sql-server"></a>SQL Server のオブジェクトのセキュリティ保護  
変換後のデータベース オブジェクトは、SQL Server に読み込まれたが後、は、付与し、それらのオブジェクトに対する権限の拒否できます。 そのために移行する前にことをお勧めデータを SQL Server。 SQL Server のセキュリティで保護されたオブジェクトを保護する方法については、「セキュリティの考慮事項のデータベースとデータベース アプリケーションの」SQL Server オンライン ブックを参照してください。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順が、 [SQL Server にデータを移行](http://msdn.microsoft.com/en-us/e23c5268-41ed-4e55-9fe7-a11376202a13)です。  
  
## <a name="see-also"></a>参照  
[SQL Server にデータベースを移行する Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
