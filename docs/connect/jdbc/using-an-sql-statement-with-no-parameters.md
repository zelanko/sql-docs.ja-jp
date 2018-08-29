---
title: パラメーターなしの SQL ステートメントを使って |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4b0728bd-059b-4b71-895c-999335bc7427
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14e4ab50614783ff3b89d83fcf9b81bef7a7e579
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42787266"
---
# <a name="using-an-sql-statement-with-no-parameters"></a>パラメータのない SQL ステートメントの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

パラメーターを含まない SQL ステートメントを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのデータを処理する場合は、[SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) クラスの [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) メソッドを使用して、要求されたデータを含む [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) を取得することができます。 この場合、最初に [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) クラスの [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) メソッドを使用して、SQLServerStatement オブジェクトを作成する必要があります。

次の例は、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースに対して開いている接続を関数に渡して SQL ステートメントを作成および実行し、その結果を結果セットから読み取って出力します。

[!code[JDBC#UsingSQLWithNoParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_0_1.java)]

結果セットの使用に関する詳細については、次を参照してください。 [JDBC ドライバーでの結果セットの管理](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)します。

## <a name="see-also"></a>参照

[SQL でのステートメントの使用](../../connect/jdbc/using-statements-with-sql.md)
