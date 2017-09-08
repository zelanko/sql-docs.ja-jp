---
title: "MySQL データベースを評価する変換 (MySQLToSQL) |Microsoft ドキュメント"
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
helpviewer_keywords:
- Assessment reports
ms.assetid: 2a56a003-3b0f-453a-963c-00c9e40933ec
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 24e18761f50997b32da67a8ed2277259f5d53516
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="assessing-mysql-databases-for-conversion-mysqltosql"></a>変換 (MySQLToSQL) の MySQL データベースを評価します。
オブジェクトを読み込むし、データを移行する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure 移行が複雑な方法で、どれ時間だけを決定する必要があります、移行になります。 SSMA は、正常に変換されるオブジェクトの割合が表示される評価レポートを作成できます。 SSMA では、変換エラーが発生する特定の問題を表示することもできます。  
  
## <a name="creating-assessment-reports"></a>評価レポートを作成します。  
SSMA 変換を選択した MySQL データベース オブジェクトでこの評価レポートを作成するとき[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の構文、し、結果を表示しています。  
  
**評価レポートを作成するには**  
  
1.  MySQL メタデータ エクスプ ローラーで、評価するスキーマを選択します。  
  
2.  個々 のオブジェクトを省略するには、それらの横にあるチェック ボックスをオフにします。  
  
3.  右クリック**スキーマ**、し、**レポートの作成**です。  
  
    個々 のオブジェクトを分析するオブジェクトを右クリックします。 次に、選択**レポートの作成**です。  
  
    SSMA は、ウィンドウの下部にあるステータス バーに進行状況が表示されます。 [出力] ペインが表示されている場合は、出力ウィンドウのメッセージも表示されます。  
  
    評価の完了時に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant for MySQL、評価レポート ウィンドウが表示されます。  
  
## <a name="using-assessment-reports"></a>評価レポートを使用します。  
評価 [レポート] ウィンドウには、3 つのペインが含まれています。  
  
-   左側のウィンドウには、評価レポートに含まれているオブジェクトの階層が含まれています。 階層を参照し、オブジェクトと変換統計、およびコードを表示するオブジェクトのカテゴリを選択できます。  
  
-   右側のペインの内容は、左側のペインで選択されている項目に依存します。  
  
    スキーマなど、オブジェクトのグループが選択されている場合、右側のペインはカテゴリ ウィンドウで変換統計ペインとオブジェクトを表示します。 変換の統計情報 ウィンドウには、選択したオブジェクトの変換統計が表示されます。 カテゴリ ウィンドウでオブジェクトには、オブジェクトまたはオブジェクトのカテゴリの変換統計が表示されます。  
  
    関数、プロシージャ、テーブルまたはビューが選択されている場合、右側のペインには、統計情報、ソース コード、および対象のコードが含まれています。  
  
    -   上部の領域には、オブジェクトの全体的な統計情報が表示されます。 展開する必要があります**統計**この情報を表示します。  
  
    -   コピー元領域は、左ペインで選択されているオブジェクトのソース コードを示しています。 強調表示された領域は、問題のあるソース コードを示します。  
  
    -   対象となる領域は、変換後のコードを示しています。 赤いテキストには、問題のコードとエラー メッセージが表示されます。  
  
-   下のペインは、変換のメッセージを使用して、メッセージ番号でグループ化を示しています。 クリックして**エラー**、**警告**、または**情報**をメッセージのカテゴリを表示し、メッセージのグループの順に展開します。 左ペインでオブジェクトを選択し、右側のウィンドウで詳細を表示する個々 のメッセージをクリックします。  
  
## <a name="analyzing-conversion-problems-by-using-the-assessment-report"></a>評価レポートを使用して、変換の問題を分析します。  
変換の統計情報 ウィンドウでは、変換の統計情報を表示します。 任意のカテゴリの割合が 100% 未満の場合は、理由、変換に失敗しましたを指定する必要があります。  
  
**変換の問題を表示するには**  
  
1.  前の手順の手順を使用して評価レポートを作成します。  
  
2.  左側のウィンドウで、スキーマまたはに赤いエラー アイコンが付いたフォルダーを展開します。 変換に失敗した個々 の項目を選択するまでの項目の展開を続行します。  
  
3.  [ソース] ウィンドウの上部には、をクリックして**次の問題**です。  
  
    問題のあるコードが強調表示されて、ターゲットのナビゲーション ウィンドウで、関連するコードが格納されます。  
  
4.  すべてのエラー メッセージを確認しの変換の問題の原因となったオブジェクトで実行するを決定します。  
  
-   SSMA で MySQL 構文を更新します。 プロシージャおよび関数のみの構文を更新することができます。 構文を更新するには、MySQL メタデータ エクスプ ローラー ペインでオブジェクトを選択 をクリックして、 **SQL**タブをクリックし、SQL コードを変更します。 項目から移動するときに、更新された構文の保存が求められます。 表示するには、報告されたエラー オブジェクトを**レポート**タブです。  
  
-   MySQL では、削除するか、問題のあるコードを修正する MySQL オブジェクトを変更できます。 SSMA に、更新されたコードを読み込むするには、メタデータを更新する必要があります。 詳細については、次を参照してください[MySQL &#40; に接続する。MySQLToSQL &#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md).  
  
-   オブジェクトは、移行から除外できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラーと MySQL メタデータ エクスプ ローラーにオブジェクトを読み込む前に、アイテムの横のチェック ボックスをオフに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure と MySQL からデータを移行します。  
  
## <a name="next-step"></a>次の手順  
[MySQL データベース &#40; を変換します。MySQLToSQL &#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40; への MySQL データベースの移行MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

