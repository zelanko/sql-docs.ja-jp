---
title: "テスト_ケース準備 (SybaseToSQL) を終了 |Microsoft ドキュメント"
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
helpviewer_keywords:
- Tester Component,Test Case Settings
ms.assetid: 8b2a49b0-4296-4f3f-9e56-323aa6a6fa8e
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 7568e7a78e0129204a23797cbc589139816ac13e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="finishing-test-case-preparation-sybasetosql"></a>テスト_ケース準備 (SybaseToSQL) の終了
ウィザードの最終ページには、テスト_ケースの説明と、テストに関連するオブジェクトに関する情報が表示されます。 さらに、このページで設定できます、テストの実行オプション。  
  
**テスト_ケースについて**テスト_ケースの名前と説明 セクションを示しています。  
  
**テスト オブジェクト**セクションには、オブジェクトの種類でグループ化されたテスト済みのオブジェクトの名前付きの一覧が含まれています。  
  
**分析するのには影響を受けるオブジェクト**セクションには、テスト対象のオブジェクトの実行後にどのデータの変更と比較するオブジェクトの名前付きの一覧が表示されます。  
  
## <a name="test-case-settings"></a>テスト_ケースの設定  
**テスト_ケース設定**セクション テスト オプションを次の実行に設定します。  
  
### <a name="stop-test-execution-after-first-failure"></a>最初のエラーの後にテストの実行を停止します。  
テストの実行中にエラーが発生した場合、テストを中断するを指定します。  
  
-   選択した場合**はい**エラーが発生する場合は、実行が中断をテストします。  
  
-   選択した場合**いいえ**、エラーが発生したテストの実行が続行されます。  
  
### <a name="perform-data-rollback"></a>データのロールバックを実行します。  
テストの実行後、データの自動ロールバックを有効にします。  
  
-   選択した場合**はい**テストの実行後のデータ変更が失われます。  
  
-   選択した場合**いいえ**、すべてのテストの実行データの変更は保存されます。  
  
### <a name="auxiliary-tables-saving-mode"></a>補助テーブルの保存モード  
テストの実行中に作成された補助テーブルの保存モードを定義します。 内の補助テーブルの説明を参照して、[テスト_ケースの実行 & #40 です。SybaseToSQL &#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)トピックです。  
  
-   選択した場合**は常に保存**、補助テーブル データは、後で使用するため常に格納されます。  
  
-   選択した場合**テーブルの比較に失敗した場合は、保存**エラーが発生する場合にのみの補助テーブルのデータを格納します。  
  
-   選択した場合**をいつでも削除**、常に補助テーブルがテストの実行後に削除されます。  
  
-   選択した場合**テーブルの比較に失敗した場合にユーザーに依頼**ユーザーは、エラーが発生する場合に必要な操作を選択できます。  
  
クリックして、**完了**に準備されたテスト_ケースを保存するボタン[テスト リポジトリの使用 &#40;SybaseToSQL &#41;](../../ssma/sybase/using-test-repositories-sybasetosql.md).  
  
## <a name="see-also"></a>参照  
[テスト リポジトリ &#40; を使用します。SybaseToSQL &#41;](../../ssma/sybase/using-test-repositories-sybasetosql.md)  
[実行中のテスト_ケースと #40 です。SybaseToSQL &#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[データベース オブジェクト &#40; 移行テストSybaseToSQL &#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  

