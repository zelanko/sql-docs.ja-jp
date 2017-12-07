---
title: "Oracle スキーマの変換 (OracleToSQL) に評価 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Analyzing Conversion Problems
ms.assetid: 4de9bcf6-1346-4740-87f9-7f24a8226357
caps.latest.revision: "7"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 27faa50ad384ec9061252e056d90976687f7e3d3
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="assessing-oracle-schemas-for-conversion-oracletosql"></a>Oracle スキーマの変換 (OracleToSQL) の評価
オブジェクトを読み込むし、データを移行する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、ほど複雑か、移行されるとどれ時間だけを決定する必要があります、移行になります。 SSMA は、正常に変換されるオブジェクトの割合が表示される評価レポートを作成できます。 SSMA では、変換エラーが発生する特定の問題を表示することもできます。  
  
## <a name="creating-assessment-reports"></a>評価レポートを作成します。  
この評価レポートを作成するとき SSMA オブジェクトに変換、選択されている Oracle データベースに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文、し、結果を表示しています。  
  
**評価レポートを作成するには**  
  
1.  Oracle メタデータ エクスプ ローラーで、評価するスキーマを選択します。  
  
2.  個々 のオブジェクトを省略するには、それらの横にあるチェック ボックスをオフにします。  
  
3.  右クリック**スキーマ**、し、**レポートの作成**です。  
  
    オブジェクトを右クリックして選択し、個々 のオブジェクトを分析することも**レポートの作成**です。  
  
    SSMA は、ウィンドウの下部にあるステータス バーに進行状況が表示されます。 [出力] ペインが表示されている場合は、出力ウィンドウのメッセージも表示されます。  
  
    評価の完了時に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant for Oracle: 評価レポート ウィンドウが表示されます。  
  
## <a name="using-assessment-reports"></a>評価レポートを使用します。  
評価 [レポート] ウィンドウには、3 つのペインが含まれています。  
  
-   左側のウィンドウには、評価レポートに含まれているオブジェクトの階層が含まれています。 階層を参照し、オブジェクトと変換統計、およびコードを表示するオブジェクトのカテゴリを選択できます。  
  
-   右側のペインの内容は、左ペインで選択されている項目に依存します。  
  
    オブジェクトのグループは、選択した場合、このようなスキーマでは、右側のペインがカテゴリ ウィンドウで、変換統計ペインと、オブジェクトを表示するテーブルが選択されている場合またはします。 変換の統計情報 ウィンドウには、選択したオブジェクトの変換統計が表示されます。 カテゴリ ウィンドウでオブジェクトには、オブジェクトまたはオブジェクトのカテゴリの変換統計が表示されます。  
  
    関数、パッケージ、プロシージャ、シーケンス、またはビューが選択されている場合、右側のペインには、統計情報、ソース コード、および対象のコードが含まれています。  
  
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
  
4.  すべてのエラー メッセージを確認しての変換の問題の原因となったオブジェクトで実行する内容を確認してください。  
  
    -   SSMA で Oracle の構文を更新します。 プロシージャ、関数、トリガー、関数をパッケージおよびパッケージ化されたプロシージャの構文を更新することができます。 構文を更新するには、Oracle メタデータ エクスプ ローラー ペインでオブジェクトを選択 をクリックして、 **SQL**タブをクリックし、SQL コードを変更します。 項目から移動するときに、更新された構文の保存が求められます。 表示するには、報告されたエラー オブジェクトを**レポート**タブです。  
  
    -   Oracle では、削除または問題のあるコードを変更するには、Oracle オブジェクトを変更できます。 SSMA に、更新されたコードを読み込むするには、メタデータを更新する必要があります。 詳細については、次を参照してください。 [Oracle データベース &#40;OracleToSQL&#41; への接続](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md)です。  
  
    -   オブジェクトは、移行から除外できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーと Oracle メタデータ エクスプ ローラーにオブジェクトを読み込む前に、項目の横のチェック ボックスをオフ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Oracle からデータを移行します。  
  
## <a name="next-step"></a>次の手順  
[変換する際の Oracle スキーマ &#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md)  
  
## <a name="see-also"></a>参照  
[SQL Server &#40;OracleToSQL&#41; への Oracle データベースの移行](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
