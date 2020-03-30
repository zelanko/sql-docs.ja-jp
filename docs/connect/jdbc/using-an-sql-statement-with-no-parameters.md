---
title: パラメーターのない SQL ステートメントの使用 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4b0728bd-059b-4b71-895c-999335bc7427
author: MightyPen
ms.author: genemi
ms.openlocfilehash: da4342b8640e89a0183a3f80889dd27ecfb1a76e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "69026541"
---
# <a name="using-an-sql-statement-with-no-parameters"></a>パラメーターのない SQL ステートメントの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

パラメーターを含まない SQL ステートメントを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのデータを処理する場合は、[SQLServerStatement](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) クラスの [executeQuery](../../connect/jdbc/reference/sqlserverstatement-class.md) メソッドを使用して、要求されたデータを含む [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) を取得することができます。 この場合、最初に [SQLServerConnection](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) クラスの [createStatement](../../connect/jdbc/reference/sqlserverconnection-class.md) メソッドを使用して、SQLServerStatement オブジェクトを作成する必要があります。

次の例は、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースに対して開いている接続を関数に渡して SQL ステートメントを作成および実行し、その結果を結果セットから読み取って出力します。

[!code[JDBC#UsingSQLWithNoParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_0_1.java)]

結果セットの使用方法の詳細については、「[JDBC ドライバーによる結果セットの管理](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)」を参照してください。

## <a name="see-also"></a>参照

[SQL でのステートメントの使用](../../connect/jdbc/using-statements-with-sql.md)
