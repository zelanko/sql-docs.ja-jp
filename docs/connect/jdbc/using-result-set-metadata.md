---
title: 結果セットのメタデータを使用する |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 86e41f52ed8296c46cfd7b167407b10fc9f0b285
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68005942"
---
# <a name="using-result-set-metadata"></a>結果セットのメタデータの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

結果セットに格納されている列の情報をクエリするために、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] には、[SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) クラスが実装されています。 このクラスには、単一値の形式で情報を返すメソッドが多数存在します。

SQLServerResultSetMetaData オブジェクトを作成するには、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラスの[getmetadata](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md)メソッドを使用します。

次の例では、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプルデータベースに対して開いている接続を関数に渡し、SQLServerResultSet クラスの getmetadata メソッドを使用して SQLServerResultSetMetaData オブジェクトを返します。その後、SQLServerResultSetMetaData オブジェクトは、結果セット内に含まれる列の名前とデータ型に関する情報を表示するために使用されます。

[!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]

## <a name="see-also"></a>参照

[JDBC ドライバーによるメタデータの処理](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
