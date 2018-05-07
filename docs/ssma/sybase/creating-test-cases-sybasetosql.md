---
title: テスト_ケース (SybaseToSQL) の作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Tester component,Test Case Wizard
ms.assetid: b52dfd93-95af-4299-bc8f-83f2a7a6a518
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 36155da5abac07730c93096e506553f2cd4b8bf5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="creating-test-cases-sybasetosql"></a>テスト_ケース (SybaseToSQL) の作成
テストを作成するのにには、テスト ケース ウィザードを使用します。 このウィザードでは、テストおよび検証済みのオブジェクトを選択して、テストのパラメーターを指定して、テスト_ケースを作成できます。  
  
## <a name="starting-the-test-case-wizard"></a>テスト ケース ウィザードの開始  
テスト_ケースのウィザードを起動する**新しいテスト_ケースしています.** **Tester**メニュー。  
  
起動すると、ウィザードはデータベース ssmatester2005db またはソース Sybase サーバーにもよりますが、プロジェクトの種類) ssmatester2008db を探します。 テスト担当者拡張機能のスキーマの補助オブジェクトの格納に使用することをお勧めします。 テスト ケース ウィザード ssmatester2005db または ssmatester2008db が見つからない場合は、テスト担当者の拡張機能のデータベースを作成することを提案するダイアログ ウィンドウが表示されます。 (この状況で通常実行される SSMA テスターの最初の実行中にします。)  
  
ダイアログ ウィンドウが表示された場合にクリックして**はい**移行元サーバーに Sybase tester データベースを作成します。 新しいダイアログ ウィンドウでは、テスト担当者の新しいデータベースを配置する 1 つまたは複数のデバイスを追加する必要があるされます。 をクリックして**追加**デバイスを追加します。 **Tester データベースの割り当て領域**ダイアログは、デバイスを選択し、テスト担当者のデータベースで使用されるサイズを指定します。 さらに、データベースのログを別のデバイスを設定することができます。 データベースを作成する Sybase 特権が必要に注意してください。  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>ウィザードを使用してテスト_ケースの作成の概要  
テスト_ケースを作成するプロセスは、5 つの手順で構成されます。  
  
1.  [テスト_ケースの初期化&#40;SybaseToSQL&#41;](../../ssma/sybase/initializing-test-cases-sybasetosql.md)です。  
  
2.  [選択して、テストするオブジェクトを構成&#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md)です。  
  
3.  [影響を受けたオブジェクトの選択と構成&#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)です。  
  
4.  [呼び出し順序のカスタマイズ&#40;SybaseToSQL&#41;](../../ssma/sybase/customizing-calls-order-sybasetosql.md)です。  
  
5.  [テスト_ケース準備を完了&#40;SybaseToSQL&#41;](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md)です。  
  
## <a name="see-also"></a>参照  
[データベース オブジェクトを移行テスト&#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
