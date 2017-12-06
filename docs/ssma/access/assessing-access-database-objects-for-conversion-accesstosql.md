---
title: "変換 (AccessToSQL) のデータベース オブジェクトへのアクセスを評価する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- assessing SQL
- assessing syntax
- assessment reports
- creating assessment reports
- estimating migration effort
- reports
- SQL, assessing
- syntax, assessing
ms.assetid: 8b9e23d6-da62-437a-8c05-8ad2628b9441
caps.latest.revision: "16"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b56dec5144daf0531fa630c2d6fc016903c5eeaa
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="assessing-access-database-objects-for-conversion-accesstosql"></a>変換 (AccessToSQL) のデータベース オブジェクトへのアクセスを評価します。
オブジェクトを読み込むし、データを移行する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SQL Azure、する必要があります量を調べるか、移行の成功、し、どのくらいの時間、変換かかる場合があります。 SSMA を正常に変換されたオブジェクトの割合が表示される評価レポートを作成できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の構文と時刻の評価、移行を実行します。 SSMA では、変換エラーの原因となった特定の問題を表示することもできます。  
  
## <a name="creating-assessment-reports"></a>評価レポートを作成します。  
SSMA が、選択したデータベース オブジェクトに変換します評価レポートを作成するとき[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の構文、し、結果を表示しています。  
  
**評価レポートを作成するには**  
  
1.  メタデータ エクスプ ローラーでのアクセス、または、対象とする複数のデータベースを選択します。  
  
2.  個々 のオブジェクトを省略する場合、オブジェクトを評価したくない横のチェック ボックスをオフにします。  
  
3.  右クリック**データベース**、し、**レポートの作成**です。  
  
    オブジェクトを右クリックして選択し、個々 のオブジェクトを分析することもできます。**レポートの作成**です。  
  
    SSMA は、ウィンドウの下部にあるステータス バーで進行状況を示しています。 [出力] ペインが表示されている場合は、出力ウィンドウのメッセージも表示されます。  
  
評価の完了時に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant for Access: 評価レポート ウィンドウが表示されます。  
  
## <a name="using-assessment-reports"></a>評価レポートを使用します。  
評価 [レポート] ウィンドウには、3 つのペインが含まれています: エクスプ ローラー、詳細ウィンドウ、およびメッセージ ウィンドウです。  
  
-   エクスプ ローラー ペインを使用して、評価されたオブジェクトを参照できます。 個々 のテーブル、インデックス、およびキーにドリルダウンするには、このペインでアイテムをクリックすることができます。  
  
-   詳細ペインには、選択したオブジェクトの変換統計が表示されます。  
  
-   メッセージ ペインで、エラー、警告、および変換には、情報メッセージを表示し、時間の見積もりを移行し、個々 のエラー修正の手順を実行するため。  
  
評価レポートを再度実行またはスキーマを変換する前に、エラーを修正する必要があります。 エラーを検出する をクリックして、**エラー**メッセージ ウィンドウで、ボタンをクリックし、エラーが発生したオブジェクトの一覧を表示するには、各エラーの順に展開します。 [メッセージ] ウィンドウ内のオブジェクトをクリックすると、すべてのエラーとそのオブジェクトの警告の詳細ウィンドウで表示されます。  
  
## <a name="next-step"></a>次の手順  
[Access データベース オブジェクトの変換](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
