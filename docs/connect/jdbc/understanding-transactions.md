---
title: トランザクションについて |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d3e0414c-6809-4bb1-93b1-4960507faecc
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6045c482a931329e3d62c49dedea7ea86a14c545
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32852497"
---
# <a name="understanding-transactions"></a>トランザクションについて
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  トランザクションは、一連の操作を結合した論理的な作業単位です。 トランザクションを使用すると、エラーが発生した場合でも、トランザクションの各操作の一貫性と整合性を制御および維持できます。  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]トランザクションは、ローカルまたは分散型のいずれかを指定できます。 トランザクションで分離レベルを使用することもできます。 JDBC ドライバーでサポートされる分離レベルの詳細については、次を参照してください。[分離レベルの理解](../../connect/jdbc/understanding-isolation-levels.md)です。  
  
 アプリケーションからトランザクションを制御する際には、Transact-SQL ステートメントか、JDBC ドライバーに備わっているメソッドのどちらかを使用します。両方を使用することはできません。 同じトランザクションで Transact-SQL ステートメントと JDBC API メソッドの両方を使用した場合、トランザクションを適切なタイミングでコミットできない、突然トランザクションがコミットまたはロールバックされて新しいトランザクションが開始される、"トランザクションを再開できませんでした" という例外が発生するなどの問題が生じる可能性があります。  
  
## <a name="using-local-transactions"></a>ローカル トランザクションの使用  
 単一フェーズであり、データベースによって直接処理されるトランザクションは、ローカル トランザクションであると見なされます。 JDBC ドライバーのさまざまなメソッドを使用して、ローカル トランザクションをサポートする、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスを含む[setAutoCommit](../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md)、[コミット](../../connect/jdbc/reference/commit-method-sqlserverconnection.md)、および[ロールバック](../../connect/jdbc/reference/rollback-method.md)です。 通常、ローカル トランザクションはアプリケーションによって明示的に管理されるか、Java Platform, Enterprise Edition (Java EE) アプリケーション サーバーによって自動的に管理されます。  
  
 次の例の 2 つのステートメントで構成されるローカル トランザクションの実行、`try`ブロックします。 ステートメントは [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベースの Production.ScrapReason テーブルに対して実行され、それらは例外がスローされなかった場合にコミットされます。 例外がスローされた場合、`catch`ブロックのコードがトランザクションをロールバックします。
  
 [!code[JDBC#UnderstandingTransactions1](../../connect/jdbc/codesnippet/Java/understanding-transactions_1.java)]  
  
## <a name="using-distributed-transactions"></a>分散トランザクションの使用  
 分散トランザクションは、トランザクション処理の重要な ACID (原子性、一貫性、分離性、および持続性) のプロパティを維持しながら、ネットワーク上の複数のデータベースのデータを更新します。 分散トランザクションのサポートは、JDBC 2.0 オプション API 仕様で JDBC API に追加されました。 分散トランザクションの管理は、通常、Java EE アプリケーション サーバー環境内で Java Transaction Service (JTS) トランザクション マネージャーによって自動的に実行されます。 ただし、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]任意の Java Transaction API (JTA) 準拠のトランザクション マネージャーで分散トランザクションをサポートします。  
  
 JDBC ドライバーをシームレスに統合[!INCLUDE[msCoName](../../includes/msconame_md.md)]分散トランザクション コーディネーター (MS DTC) は true を提供する分散トランザクション サポート[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 MS DTC によって提供される分散トランザクション機能は、[!INCLUDE[msCoName](../../includes/msconame_md.md)]の[!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows システムです。 MS DTC からの実証済みのトランザクション処理技術を使用して[!INCLUDE[msCoName](../../includes/msconame_md.md)]完全な 2 フェーズ分散コミット プロトコルや分散トランザクションの復旧などの XA 機能をサポートします。  
  
 分散トランザクションを使用する方法の詳細については、次を参照してください。 [XA トランザクションについて](../../connect/jdbc/understanding-xa-transactions.md)です。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーを使用したトランザクションの実行](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  
