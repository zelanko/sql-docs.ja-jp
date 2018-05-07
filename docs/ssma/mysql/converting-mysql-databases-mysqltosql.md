---
title: MySQL データベース (MySQLToSQL) の変換 |Microsoft ドキュメント
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
ms.assetid: ac21850b-fb32-4704-9985-5759b7c688c7
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: a1925166a672523f6e4cf5eef7cdc0bc5235c3fd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="converting-mysql-databases-mysqltosql"></a>MySQL データベース (MySQLToSQL) の変換
MySQL を接続すると後に、接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]MySQL のデータベース オブジェクトに変換するには SQL Azure、およびプロジェクトの設定とデータのマッピング オプション、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベースのオブジェクト。  
  
## <a name="the-conversion-process"></a>変換プロセス  
データベース オブジェクトを変換する MySQL からオブジェクト定義を受け取り、同様に変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure オブジェクト、および SSMA メタデータにこの情報を読み込みます。 インスタンスに、情報は読み込まれません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 使用して、オブジェクトとそのプロパティを表示することができますし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラー。  
  
変換中には、SSMA は、出力ウィンドウに出力メッセージとエラー一覧 ウィンドウにエラー メッセージを出力します。 MySQL データベースまたは必要な変換の結果を得るため、変換プロセスを変更するのにかどうかを確認するのにには、出力とエラー情報を使用します。  
  
## <a name="setting-conversion-options"></a>変換オプションの設定  
オブジェクトを変換する前に、プロジェクトの変換オプションを確認、**プロジェクト設定** ダイアログ ボックス。 このダイアログ ボックスを使用すると、SSMA がテーブルとインデックスに変換する方法を設定することができます。 詳細については、「[プロジェクト設定&#40;変換&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
  
## <a name="conversion-results"></a>変換結果  
次の表は、MySQL オブジェクトは変換し、結果として得られる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクト。  
  
|||  
|-|-|  
|**MySQL オブジェクト**|**SQL Server オブジェクトの結果として得られる**|  
|インデックスなどの依存オブジェクトを持つテーブル|SSMA は、依存オブジェクトをテーブルを作成します。 テーブルは、すべてのインデックスおよび制約に変換されます。 インデックスが個別に変換される[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクト。<br /><br />**空間データ型マッピング**テーブル ノード レベルでのみ実行できます。<br /><br />テーブルの変換の設定の詳細については、次を参照してください[変換の設定。](http://msdn.microsoft.com/en-us/f551cf6e-1575-4206-9cca-975b5b43a6b8)|  
|関数|関数は、TRANSACT-SQL に直接変換できます、SSMA は、関数を作成します。 場合によっては、関数は、ストアド プロシージャに変換する必要があります。 使用してこれ行う**関数の変換**プロジェクトの設定にします。 この例では、SSMA は、ストアド プロシージャおよびストアド プロシージャを呼び出す関数を作成します。<br /><br />**選択できるは:**<br /><br />プロジェクトの設定に応じて変換します。<br /><br />関数への変換します。<br /><br />ストアド プロシージャへの変換します。<br /><br />関数の変換の設定の詳細については、次を参照してください[変換の設定。](http://msdn.microsoft.com/en-us/f551cf6e-1575-4206-9cca-975b5b43a6b8)|  
|手順|プロシージャは、TRANSACT-SQL に直接変換できます、SSMA は、ストアド プロシージャを作成します。 場合によっては、自律的なトランザクションでストアド プロシージャを呼び出す必要があります。 SSMA が 2 つのストアド プロシージャを作成するこの例では、: プロシージャ、および別の実装を呼び出すために使用されるを実装するいずれかのストアド プロシージャです。|  
|データベースの変換|MySQL オブジェクトとしてデータベースが直接変換されない SSMA によって for MySQL。 MySQL データベースはスキーマ名のようによりに扱われ、物理的なすべてのパラメーターは変換中に失われます。 SSMA for MySQL を使用して[MySQL データベースを SQL Server スキーマへのマッピング&#40;MySQLToSQL&#41; ](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)に MySQL データベースから適切な SQL Server データベースまたはスキーマのペアにオブジェクトをマップします。|  
|トリガーの変換|**SSMA では、次の規則に基づいてトリガーを作成します。**<br /><br />トリガーが INSTEAD OF T-SQL トリガーに変換される前に<br /><br />AFTER トリガーは、行ごとのイテレーションの有無の後に T-SQL トリガーに変換されます。|  
|ビューの変換|SSMA は、依存オブジェクトを含むビューを作成します。|  
|ステートメントの変換|-各 SQL ステートメントのオブジェクトが (DDL、DML、およびその他の種類のステートメント) など 1 つ MySQL ステートメントを含めることがありますか開始しています.終了ブロック。<br />-   **複数ステートメントの変換: 開始しています.終了ブロック変換**SQL ステートメントでは、BEGIN を含めることができますもしています.プロシージャ、関数、またはトリガーの定義でいずれかのような終了ブロック。 これらのブロックには、MySQL の 1 つのステートメント オブジェクトの変換と同様を変換する必要があります。|  
  
## <a name="converting-mysql-database-objects"></a>MySQL データベース オブジェクトを変換します。  
MySQL データベースのオブジェクトに変換するには、最初に、変換するオブジェクトを選択し、SSMA が変換を実行します。 変換中に出力メッセージを表示する、**ビュー**メニューの **出力**です。  
  
**MySQL オブジェクトを SQL Server または SQL Azure の構文に変換するには**  
  
1.  MySQL メタデータ エクスプ ローラーで、MySQL サーバーを展開し、展開**データベース**です。  
  
2.  変換するオブジェクトを選択します。  
  
    -   すべてのスキーマを変換するには、チェック ボックスを横に選択**データベース**です。  
  
    -   変換するか、データベースを省略するには、データベース名の横にあるチェック ボックスを選択します。  
  
    -   変換またはオブジェクトのカテゴリの省略は、スキーマを展開し、選択するか、カテゴリの横にあるチェック ボックスをオフにします。  
  
    -   変換または個々 のオブジェクトを省略、カテゴリ フォルダーを展開し、選択するか、オブジェクトの横にあるチェック ボックスをオフにします。  
  
3.  選択したすべてのオブジェクトを変換するを右クリックして**データベース**選択**スキーマの変換**です。  
  
    オブジェクトまたはその親フォルダーを右クリックしを選択して、個々 のオブジェクトまたはオブジェクトのカテゴリを変換することができますも**変換スキーマ**です。  
  
## <a name="viewing-conversion-problems"></a>変換の問題を表示します。  
MySQL の一部のオブジェクトを変換できません可能性があります。 集計変換レポートを表示して、変換の成功率を指定できます。  
  
**概要レポートを表示するには**  
  
1.  MySQL メタデータ エクスプ ローラーで、次のように選択します。**データベース**です。  
  
2.  右側のペインで、**レポート**タブです。  
  
    このレポートには、評価または変換されているすべてのデータベース オブジェクトの評価の概要レポートが表示されます。 個々 のオブジェクトの概要レポートを表示することもできます。  
  
    -   個々 のスキーマのレポートを表示するには、メタデータ エクスプ ローラーで MySQL データベースを選択します。  
  
    -   個々 のオブジェクトのレポートを表示するには、MySQL メタデータ エクスプ ローラーで、オブジェクトを選択します。 変換の問題のあるオブジェクトでは、赤いエラー アイコンがあります。  
  
オブジェクトの変換に失敗した場合に、変換エラーが発生した構文を表示することができます。  
  
**個々 の変換の問題を表示するには**  
  
1.  MySQL メタデータ エクスプ ローラーで、**データベース**です。  
  
2.  赤いエラー アイコンが表示されるデータベースを展開します。  
  
3.  データベースの下に赤いエラー アイコンを持つフォルダーを展開します。  
  
4.  赤いエラー アイコンがあるオブジェクトを選択します。  
  
5.  右側のウィンドウでをクリックして、**レポート**タブです。  
  
6.  上部にある、**レポート**タブは、ドロップダウン リスト。 一覧に表示される場合**統計**、選択を変更するに**ソース**です。  
  
    SSMA は、ソース コードとコードのすぐ上のいくつかのボタンに表示されます。  
  
7.  クリックして、**次の問題**ボタンをクリックします。 これは、右側に、矢印の付いた赤いエラー アイコンです。  
  
    SSMA は、現在のオブジェクト内で見つかった最初の問題のあるソース コードを強調表示されます。  
  
変換できなかった項目ごとのオブジェクトで実行するかを決定する必要があります。  
  
-   MySQL データベースを削除するか、問題のあるコードの修正を内のオブジェクトを変更することができます。 SSMA に、更新されたコードを読み込むするには、メタデータを更新する必要があります。 詳細については、次を参照してください[MySQL への接続&#40;MySQLToSQL。&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
-   オブジェクトは、移行から除外できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラーと MySQL メタデータ エクスプ ローラーにオブジェクトを読み込む前に、アイテムの横のチェック ボックスをオフに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure と MySQL からデータを移行します。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順は[SQL Server に変換されたデータベース オブジェクトの読み込み&#40;MySQLToSQL&#41;](../../ssma/mysql/loading-converted-database-objects-into-sql-server-mysqltosql.md)  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB にデータベースを移行する MySQL &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
