---
title: "テストに移行したデータベース オブジェクト (OracleToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f03ef5e1-66e6-4c84-ada2-252dd5ada82f
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e32dfd7db190884d20ae97c8b00d57a7b6683c30
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="testing-migrated-database-objects-oracletosql"></a>移行されたデータベース オブジェクト (OracleToSQL) のテスト
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant の Oracle Tester (SSMA テスター) は、データベース オブジェクトへの変換と SSMA によって行われたデータの移行を自動的にテストします。 SSMA のすべての移行手順が完了したら後、は、SSMA Tester を使用して、変換したオブジェクトが同じように動作し、すべてのデータが正常に転送されることを確認してください。  
  
SSMA Tester では、次のオブジェクトの種類をテストできます。  
  
-   テーブル  
  
-   ストアド プロシージャは、パッケージ化されたプロシージャを含むです。  
  
-   ユーザー定義関数、関数を含むパッケージ。  
  
-   表示モード。  
  
-   スタンドアロンのステートメント。  
  
SSMA テスターは、Oracle との対応するテスト用に選択されたオブジェクトを実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 その後、次の条件に基づいて結果を比較します。  
  
-   変更テーブル データと同じですか。  
  
-   プロシージャおよび関数の出力パラメーターの値が同じですか。  
  
-   関数は同じ結果を返します。  
  
-   結果セットと同じですか。  
  
> [!NOTE]  
> 注意してください。 実稼働システムでは、SSMA Tester を使用しないでください。 テストの実行中に、送信元スキーマとデータが変更されます。 一方で、元の状態の完全な復元はテスト対象コードの種類によって可能なでない可能性があります。  
  
## <a name="prerequisites"></a>前提条件  
SSMA Tester を使用する場合は、SSMA Oracle 拡張機能パックをインストール、 **Tester データベースのインストール**オプションをオンにします。  
  
結果として得られるテーブル データの比較を有効にするために次のように設定します。、**生成 ROWID 列**オプションを**はい**スキーマの変換を開始する前にします。 SSMA の実行中にすべてのテーブルに ROWID 列を追加するが、**変換スキーマ**コマンド。  
  
さらに、次の点を確認します。  
  
-   Oracle クライアント ツールがコンピューターにインストールされている場所[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を実行します。  
  
-   共通言語ランタイム (CLR) 統合を有効になっている、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース エンジン。  
  
SSMA テスターの現在のバージョンによって、同じソースまたはターゲット サーバーに複数のユーザーによって並列実行がサポートされていないことに注意します。  
  
## <a name="getting-started"></a>作業の開始  
[作成するテスト_ケース &#40;OracleToSQL"&"#41;](../../ssma/oracle/creating-test-cases-oracletosql.md)  
  
## <a name="see-also"></a>参照  
[SQL Server &#40;OracleToSQL"&"#41; SSMA コンポーネントをインストールします。](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[プロジェクトの設定 &#40;です。変換"&"#41;&#40; OracleToSQL &#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)  
  

