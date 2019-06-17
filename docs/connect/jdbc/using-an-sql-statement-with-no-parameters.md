---
title: パラメーターなしの SQL ステートメントを使って |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4b0728bd-059b-4b71-895c-999335bc7427
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d63b7195e2de73292e56f9a63dcce561ca3b906e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66790220"
---
# <a name="using-an-sql-statement-with-no-parameters"></a>パラメータのない SQL ステートメントの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

パラメーターを含まない SQL ステートメントを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのデータを処理する場合は、[SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) クラスの [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) メソッドを使用して、要求されたデータを含む [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) を取得することができます。 この場合、最初に [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) クラスの [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) メソッドを使用して、SQLServerStatement オブジェクトを作成する必要があります。

次の例は、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースに対して開いている接続を関数に渡して SQL ステートメントを作成および実行し、その結果を結果セットから読み取って出力します。

[!code[JDBC#UsingSQLWithNoParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_0_1.java)]

結果セットの使用に関する詳細については、次を参照してください。 [JDBC ドライバーでの結果セットの管理](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)します。

## <a name="see-also"></a>参照

[SQL でのステートメントの使用](../../connect/jdbc/using-statements-with-sql.md)
