---
title: "テスト リポジトリ (OracleToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Test Cases Repository
- Test Results Repository
ms.assetid: f941cce4-d3e3-4aeb-a88a-4f101a97a9f4
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c3d2c6665c6d1852b291e69d2494343b5000ac06
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="using-test-repositories-oracletosql"></a>テスト リポジトリ (OracleToSQL) を使用します。
SSMA テスト リポジトリ ストア SSMA Tester テスト_ケースとテスト結果を後で使用します。 リポジトリのデータは、SQL Server テーブルに保存されます**TestCaseRepository**と**RunTestCaseResultRepository**スキーマ**ssma_oracle_utilities**の**ssmatesterdb**データベース。  
  
次のボタンは、[テスト_ケース リポジトリ] ダイアログ ボックスを使用できます。  
  
-   クリックして、**更新**テスト_ケースまたはテスト結果の一覧を更新するボタンをクリックします。  
  
-   をクリックして、**閉じる**テスト_ケース リポジトリ ダイアログ ボックスを閉じるボタンをクリックします。  
  
## <a name="test-cases-repository"></a>テスト_ケース リポジトリ  
クリックして、Test Cases リポジトリを表示する**テスト_ケースしています.** **Tester**メニュー。 SSMA は、表示、**テスト_ケース リポジトリ**ダイアログ ウィンドウに保存されているテスト_ケースのリストを持つ、**テスト_ケース**ページ。  
  
グリッドは、各テスト・ケースは、次の情報を示しています。  
  
-   名前: テスト_ケース名。  
  
-   作成されます。 テスト_ケース作成日。  
  
-   更新日時: テスト_ケース最終変更日。  
  
-   説明: テスト ケース説明です。  
  
テスト_ケース ページで、次のボタンがあります。  
  
-   クリックして、**追加**テスト_ケース ウィザードを実行し、新しいテストを作成するボタンをクリックします。  
  
-   をクリックして、**削除**リポジトリから、選択したテストを削除するボタンをクリックします。テスト_ケースを削除すると、関連するすべてのテスト結果も削除されます。  
  
-   をクリックして、**編集**テスト_ケース ウィザードを実行し、選択したテストを変更するボタンをクリックします。  
  
-   をクリックして、**実行** を開きます、[を実行しているテスト_ケース (OracleToSQL)](http://msdn.microsoft.com/en-us/fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02)ダイアログと、選択したテストを実行します。  
  
## <a name="test-results-repository"></a>テストの結果リポジトリ  
テストの結果リポジトリを表示することができます、**テスト結果**のページ、**テスト_ケース リポジトリ**ウィンドウです。 クリックして開く**テスト結果しています.** **Tester**メニュー。  
  
2 つのフィルターを使用するには**テスト結果**ページ。  
  
-   名前のテスト ケース フィルター: テスト_ケース名でテスト結果を選択できます。 このフィルターの**すべてのテスト_ケース**値により、すべてのテスト_ケースのテスト結果を表示します。  
  
-   テスト_ケースの実行の日付フィルター: 保存の日付でテスト結果をフィルターします。このフィルターの**すべて期間**保存の任意の日付のテスト結果を表示する値を使用します。  
  
テスト結果に関する次の情報がグリッドに表示されます。  
  
-   [名前]: テスト_ケースの名前。  
  
-   保存されます。 保存のケースの日付をテストします。  
  
-   結果: (このセルのツールヒントには、テストの実行の全体的な概要が表示されます) テスト実行の概要です。  
  
次のボタンは、テスト結果 ページで入手できます。  
  
-   クリックして、**ビュー**を開くボタン[テスト_ケース レポートを表示する (&) #40";"OracleToSQL"&"#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md)テスト_ケースの結果を現在の。  
  
-   クリックして、**削除**を選択したテスト結果を削除するボタン  
  
## <a name="see-also"></a>参照  
[実行するテスト_ケース (&) #40";"OracleToSQL"&"#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[データベース オブジェクト (&) #40";"OracleToSQL"&"#41; 移行テスト](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  

