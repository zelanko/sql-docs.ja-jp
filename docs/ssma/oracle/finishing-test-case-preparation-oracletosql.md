---
title: "テスト_ケース準備 (OracleToSQL) を終了 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32f38713-7ae4-48d3-980d-74cadc8545a0
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 8448cff10ca1eab050189cffe99b585cb229d60e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="finishing-test-case-preparation-oracletosql"></a>テスト_ケース準備 (OracleToSQL) の終了
ウィザードの最終ページには、テスト_ケースの説明と、テストに関連するオブジェクトに関する情報が表示されます。 さらに、このページで設定できます、テストの実行オプション。  
  
**テスト_ケースについて**テスト_ケースの名前と説明 セクションを示しています。  
  
**オブジェクトを選択するテスト**セクションには、オブジェクトの種類でグループ化されたテスト済みのオブジェクトの名前付きの一覧が含まれています。  
  
**オブジェクトの影響を受けるでテストを分析すること**セクションには、テスト対象のオブジェクトの実行後にどのデータの変更と比較するオブジェクトの名前付きの一覧が表示されます。  
  
## <a name="test-case-settings"></a>テスト_ケースの設定  
**テスト_ケース設定**セクション テスト オプションを次の実行に設定します。  
  
### <a name="stop-test-execution-after-first-failure"></a>最初のエラーの後にテストの実行を停止します。  
テストの実行中にエラーが発生した場合、テストを中断するを指定します。  
  
-   選択した場合**はい**エラーが発生する場合は、実行が中断をテストします。  
  
-   選択した場合**いいえ**、エラーが発生したテストの実行が続行されます。  
  
### <a name="perform-data-rollback"></a>データのロールバックを実行します。  
テストの実行後にデータの自動ロールバックを有効にします。  
  
-   選択した場合**はい**テストの実行後のデータ変更が失われます。  
  
-   選択した場合**いいえ**、すべてのテストの実行データの変更は保存されます。  
  
### <a name="auxiliary-tables-saving-mode"></a>補助テーブルの保存モード  
テストの実行中に作成された補助テーブルの保存モードを定義します。 内の補助テーブルの説明を参照して、[テスト_ケースを実行する &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)トピックです。  
  
-   選択した場合**は常に保存**、補助テーブル データは、後で使用するため常に格納されます。  
  
-   選択した場合**テーブルの比較に失敗した場合は、保存**エラーが発生する場合にのみの補助テーブルのデータを格納します。  
  
-   選択した場合**をいつでも削除**、常に補助テーブルがテストの実行後に削除されます。  
  
-   選択した場合**テーブルの比較に失敗した場合にユーザーに依頼**ユーザーは、エラーが発生する場合に必要な操作を選択できます。  
  
をクリックして、**完了**に準備されたテスト_ケースを保存するボタン[を使用してテスト リポジトリ (OracleToSQL)](http://msdn.microsoft.com/en-us/f941cce4-d3e3-4aeb-a88a-4f101a97a9f4)です。  
  
## <a name="see-also"></a>参照  
[使用してテスト リポジトリ &#40;OracleToSQL&#41;](../../ssma/oracle/using-test-repositories-oracletosql.md)  
[実行するテスト_ケース &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[データベース オブジェクト &#40;OracleToSQL&#41; 移行テスト](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
