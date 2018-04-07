---
title: 変換 (SybaseToSQL) 用の SAP ASE データベース オブジェクトの評価 |Microsoft ドキュメント
ms.custom: ''
ms.date: 12/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: eb996b7c-1eef-4f73-b5e6-2fa6faf7336c
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 99342797792c8b57eff144e8c5a611bbace2776d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="assessing-sap-ase-database-objects-for-conversion-sybasetosql"></a>変換 (SybaseToSQL) のデータベース オブジェクトを SAP ASE を評価します。
オブジェクトを読み込むし、データを移行する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または決定する必要があります、Azure SQL 方法、移行の複雑さとどれだけ時間かかります。 SSMA は、オブジェクトおよびに正常に変換されるプロシージャの割合が表示される評価レポートを作成できます[!INCLUDE[tsql](../../includes/tsql_md.md)]です。 SSMA では、変換エラーを引き起こす可能性のある特定の問題を表示することもできます。  
  
## <a name="create-assessment-reports"></a>評価レポートを作成します。  
この評価レポートを作成するには、SSMA、選択した SAP Adaptive Server Enterprise (ASE) データベース オブジェクトに変換します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL の構文、し、結果を表示しています。  
  
**評価レポートを作成するには**  
  
1.  Sybase メタデータ エクスプ ローラーで、評価する必要のあるデータベースを選択します。  
  
2.  個々 のオブジェクトを省略するには、を評価しないようにするには、オブジェクトの横にあるチェック ボックスをオフにします。  
  
3.  右クリック**データベース**、し、**レポートの作成**です。  
  
    オブジェクトを右クリックして選択し、個々 のオブジェクトを分析することも**レポートの作成**です。  
  
    SSMA は、ウィンドウの下部にあるステータス バーで進行状況を示しています。 [出力] ペインが表示されている場合は、関連するメッセージも表示されます。  
  
    評価の完了時に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant for Sybase: 評価レポート ウィンドウが表示されます。  
  
## <a name="use-assessment-reports"></a>評価レポートを使用します。  
評価 [レポート] ウィンドウには、3 つのペインが含まれています。  
  
-   左側のウィンドウには、評価レポートに含まれているオブジェクトの階層が含まれています。 階層を参照し、オブジェクトと変換の統計情報とコードを表示するオブジェクトのカテゴリを選択できます。  
  
-   右側のペインの内容は、左ペインで選択されている項目に基づいて異なります。  
  
    (スキーマ) などのオブジェクトまたはテーブルのグループが選択されている場合、右側のペインには、2 つのペインが表示されます。 **変換統計**ウィンドウは、選択したオブジェクトの変換の統計情報を表示します。 **カテゴリ別にオブジェクトを**ウィンドウがオブジェクトまたはオブジェクトのカテゴリの変換の統計情報を表示します。  
  
    ストアド プロシージャ、ビュー、またはトリガーが選択されている場合は、統計情報、ソース コード、およびターゲット コードに右側のペインが含まれます。  
  
    -   上部の領域には、オブジェクトの全体的な統計情報が表示されます。 展開する必要があります**統計**この情報を表示します。 
    -   コピー元領域は、左ペインで選択されているオブジェクトのソース コードを示しています。 強調表示された領域は、問題のあるソース コードを示します。  
    -   対象となる領域は、変換後のコードを示しています。 赤いテキストには、問題のコードとエラー メッセージが表示されます。  
  
-   下のペインは、変換のメッセージを使用して、メッセージ番号でグループ化を示しています。 選択**エラー**、**警告**、または**情報**をメッセージのカテゴリを表示し、メッセージのグループの順に展開します。 右側のウィンドウで詳細を表示、左側のウィンドウで、オブジェクトを選択する個々 のメッセージをクリックします。  
  
## <a name="analyze-conversion-problems-by-using-the-assessment-report"></a>評価レポートを使用して、変換の問題を分析します。  
**変換統計ペイン**変換統計情報を示します。 任意のカテゴリの割合が 100% 未満の場合は、理由、変換に失敗しましたを指定する必要があります。  
  
**変換の問題を表示するには**  
  
1.  前の手順の手順を使用して評価レポートを作成します。  
  
2.  左側のウィンドウで、スキーマまたはに赤いエラー アイコンが付いたフォルダーを展開します。 変換に失敗した個々 の項目を選択するまでの項目の展開を続行します。  
  
3.  [ソース] ウィンドウの上部には、次のように選択します。**次の問題**です。  
    問題のあるコードが強調表示に関連するコードが格納される、**ターゲット ナビゲーション**ウィンドウです。  
  
4.  すべてのエラー メッセージを確認しての変換の問題の原因となったオブジェクトで実行する内容を確認してください。  
  
    -   SSMA で ASE 構文を更新します。 ストアド プロシージャおよびトリガーに対してのみ、構文を更新することができます。 構文を更新するには、Sybase メタデータ エクスプ ローラー ペインでオブジェクトを選択 をクリックして、 **SQL**タブ、および SQL コードを編集します。 項目から移動するときに、更新された構文の保存を求められます。 オブジェクトについては、報告されたエラーを表示、**レポート**タブです。  
  
    -   ASE、ASE オブジェクトを削除するか、問題のあるコードの修正を変更できます。 SSMA に、更新されたコードを読み込むするには、メタデータを更新する必要があります。 詳細については、次を参照してください。 [Sybase ASE に接続する&#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)です。  
  
    -   オブジェクトは、移行から除外できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL メタデータ エクスプ ローラーと Sybase メタデータ エクスプ ローラーにオブジェクトを読み込む前に、アイテムの横のチェック ボックスをオフに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL ASE からデータを移行します。
  
## <a name="next-steps"></a>次の手順  
[SAP ASE データベース オブジェクトを変換する&#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB への SAP ASE データベースの移行&#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
