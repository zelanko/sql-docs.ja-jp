---
title: 変換 (AccessToSQL) のデータベース オブジェクトへのアクセスを評価する |Microsoft ドキュメント
ms.prod: sql
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
- assessing SQL
- assessing syntax
- assessment reports
- creating assessment reports
- estimating migration effort
- reports
- SQL, assessing
- syntax, assessing
ms.assetid: 8b9e23d6-da62-437a-8c05-8ad2628b9441
caps.latest.revision: 16
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: bf85577996a6dc1e4d3e4f3f1f353b0952aece54
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773258"
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
  
