---
title: "変換 (SybaseToSQL) 用の Sybase ASE データベース オブジェクトの評価 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: eb996b7c-1eef-4f73-b5e6-2fa6faf7336c
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9683542427256511b961ad8f6ffd74af43eb23d5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="assessing-sybase-ase-database-objects-for-conversion-sybasetosql"></a>変換 (SybaseToSQL) Sybase ASE データベース オブジェクトを評価します。
オブジェクトを読み込むし、データを移行する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure 移行が複雑な方法で、どれ時間だけを決定する必要があります、移行になります。 SSMA は、オブジェクトおよびを正常に変換されたプロシージャの割合が表示される評価レポートを作成できます[!INCLUDE[tsql](../../includes/tsql_md.md)]です。 SSMA では、変換エラーの原因となる特定の問題を表示することもできます。  
  
## <a name="creating-assessment-reports"></a>評価レポートを作成します。  
SSMA が選択されている Sybase Adaptive Server Enterprise (ASE) データベース オブジェクトに変換しますこの評価レポートを作成するとき[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の構文、し、結果を表示しています。  
  
**評価レポートを作成するには**  
  
1.  Sybase メタデータ エクスプ ローラーで、評価する必要のあるデータベースを選択します。  
  
2.  個々 のオブジェクトを省略するには、を評価しないようにするには、オブジェクトの横にあるチェック ボックスをオフにします。  
  
3.  右クリック**データベース**、し、**レポートの作成**です。  
  
    オブジェクトを右クリックして選択し、個々 のオブジェクトを分析することも**レポートの作成**です。  
  
    SSMA は、ウィンドウの下部にあるステータス バーに進行状況が表示されます。 [出力] ペインが表示されている場合は、出力ウィンドウのメッセージも表示されます。  
  
    評価の完了時に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant for Sybase: 評価レポート ウィンドウが表示されます。  
  
## <a name="using-assessment-reports"></a>評価レポートを使用します。  
評価 [レポート] ウィンドウには、3 つのペインが含まれています。  
  
-   左側のウィンドウには、評価レポートに含まれているオブジェクトの階層が含まれています。 階層を参照し、オブジェクトおよびオブジェクトの変換の統計情報を表示およびコードのカテゴリを選択できます。  
  
-   右側のペインの内容は、左側のペインで選択したアイテムに依存します。  
  
    このようなスキーマ、またはテーブルが選択されている場合は、オブジェクトのグループを選択すると、右側のペインがカテゴリ ウィンドウで変換統計ペインと、オブジェクトを表示します。 変換の統計情報 ウィンドウには、選択したオブジェクトの変換統計が表示されます。 カテゴリ ウィンドウでオブジェクトには、オブジェクトまたはオブジェクトのカテゴリの変換統計が表示されます。  
  
    ストアド プロシージャ、ビュー、またはトリガーが選択されている場合は、統計情報、ソース コード、およびターゲット コードに右側のペインが含まれます。  
  
    -   上部の領域には、オブジェクトの全体的な統計情報が表示されます。 展開する必要があります**統計**この情報を表示します。  
  
    -   コピー元領域は、左ペインで選択されているオブジェクトのソース コードを示しています。 強調表示された領域は、問題のあるソース コードを示します。  
  
    -   対象となる領域は、変換後のコードを示しています。 赤いテキストには、問題のコードとエラー メッセージが表示されます。  
  
-   下のペインは、変換のメッセージを使用して、メッセージ番号でグループ化を示しています。 クリックして**エラー**、**警告**、または**情報**をメッセージのカテゴリを表示し、メッセージのグループの順に展開します。 左ペインでオブジェクトを選択し、右側のウィンドウで詳細を表示する個々 のメッセージをクリックします。  
  
## <a name="analyzing-conversion-problems-using-the-assessment-report"></a>評価レポートを使用する変換の問題を分析します。  
変換統計ペインは、変換の統計情報を表示します。 任意のカテゴリの割合が 100% 未満の場合は、理由、変換に失敗しましたを指定する必要があります。  
  
**変換の問題を表示するには**  
  
1.  前の手順の手順を使用して評価レポートを作成します。  
  
2.  左側のウィンドウで、スキーマまたはに赤いエラー アイコンが付いたフォルダーを展開します。 変換に失敗した個々 の項目を選択するまでの項目の展開を続行します。  
  
3.  [ソース] ウィンドウの上部には、をクリックして**次の問題**です。  
  
    問題のあるコードが強調表示されて、ターゲットのナビゲーション ウィンドウで、関連するコードが格納されます。  
  
4.  すべてのエラー メッセージを確認しての変換の問題の原因となったオブジェクトで実行する内容を確認してください。  
  
    -   SSMA で ASE 構文を更新します。 ストアド プロシージャおよびトリガーに対してのみ、構文を更新することができます。 構文を更新するには、Sybase メタデータ エクスプ ローラー ペインでオブジェクトを選択 をクリックして、 **SQL**タブ、および SQL コードを編集します。 項目から移動するときに、更新された構文の保存が求められます。 表示するには、報告されたエラー オブジェクトを**レポート**タブです。  
  
    -   ASE、ASE オブジェクトを削除するか、問題のあるコードの修正を変更できます。 SSMA に、更新されたコードを読み込むするには、メタデータを更新する必要があります。 詳細については、次を参照してください[Sybase ASE &#40; に接続する。SybaseToSQL &#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
    -   オブジェクトは、移行から除外できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラーと Sybase メタデータ エクスプ ローラーにオブジェクトを読み込む前に、アイテムの横のチェック ボックスをオフに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure と ASE からデータを移行します。  
  
## <a name="next-step"></a>次の手順  
[Sybase ASE データベース オブジェクト &#40; を変換します。SybaseToSQL &#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40; への Sybase ASE データベースの移行SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

