---
title: 保持機能の使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: aa48306c-e7a0-4dcb-af21-9ebb6898e45a
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0bf10226926d3c5df21d546de042095defbbe812
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851787"
---
# <a name="using-holdability"></a>保持機能の使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  既定では、トランザクション内で作成される結果セットは、トランザクションがデータベースにコミットされた後、またはロールバックされるときに開かれたままになります。 ただし、トランザクションがコミットされた後で結果セットを閉じると便利な場合があります。 これを行う、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]結果の使用のセットの保持機能をサポートしています。  
  
 結果セットの保持機能を使用して設定することができます、 [setHoldability](../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。 SetHoldability メソッドを使用して保持機能を設定する場合、結果セットの保持機能の ResultSet.HOLD_CURSORS_OVER_COMMIT 定数または ResultSet.CLOSE_CURSORS_AT_COMMIT を使用することができます。  
  
 JDBC ドライバーも、Statement オブジェクトのいずれか 1 つを作成する場合に、保持機能の設定をサポートします。 結果セットの保持機能パラメーターがあるオーバーロードを持つ Statement オブジェクトを作成する場合、ステートメント オブジェクトの保持機能が接続の保持機能と一致する必要があります。 両者が一致しない場合、例外がスローされます。 これは、SQL Server では接続レベルのみで保持機能がサポートされるからです。  
  
 結果セットの保持機能は、サーバー側のカーソルだけ、結果セットの作成時に時刻に結果セットに関連付けられている SQLServerConnection オブジェクトの保持機能です。 クライアント側のカーソルには適用されません。 クライアント側のカーソルですべての結果セットでは、ResultSet.HOLD_CURSORS_OVER_COMMIT の保持機能値を持つ常にします。  
  
 サーバー側のカーソルについては、SQL Server 2005 以降に接続されている場合に、保持機能の設定が、その接続でこれから作成される新しい結果セットの保持機能にのみ影響を与えます。 つまり、保持機能の設定は、その接続で以前に作成された結果セットや既に開かれている結果セットにはまったく影響を与えません。 ただし、SQL Server 2000 の場合は、保持機能の設定が、既存の結果セットとその接続でこれから作成される新しい結果セットの両方の保持機能に影響を与えます。  
  
 結果セットの保持機能の設定で 2 つのステートメントで構成されるローカル トランザクションの実行中に次の例で、`try`ブロックします。 Production.ScrapReason テーブルに対して、ステートメントを実行、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。 自動コミット設定の例を手動トランザクション モードに切り替えます最初に、 **false**です。 自動コミット モードを無効にすると、SQL ステートメントはコミットされません、アプリケーションが、[コミット](../../connect/jdbc/reference/commit-method-sqlserverconnection.md)メソッドに明示的にします。 catch ブロック内のコードは、例外がスローされた場合にトランザクションをロールバックします。  
  
 [!code[JDBC#UsingHoldability1](../../connect/jdbc/codesnippet/Java/using-holdability_1.java)]  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーを使用したトランザクションの実行](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  
