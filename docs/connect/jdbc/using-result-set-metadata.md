---
title: 結果セットのメタデータの使用 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ed0b1eedcafa1fab59d17f756523fc0fc189200
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026123"
---
# <a name="using-result-set-metadata"></a>結果セットのメタデータの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

結果セットに格納されている列の情報をクエリするために、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] には、[SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) クラスが実装されています。 このクラスには、単一値の形式で情報を返すメソッドが多数存在します。

SQLServerResultSetMetaData オブジェクトを作成するには、[SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) クラスの [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md) メソッドを使用します。

次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースに対して開いている接続を関数に渡し、SQLServerResultSet クラスの getMetaData メソッドを使用して SQLServerResultSetMetaData オブジェクトを取得し、SQLServerResultSetMetaData オブジェクトのさまざまなメソッドを使用して、結果セットに含まれている列の名前およびデータ型の情報を出力します。

[!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]

## <a name="see-also"></a>参照

[JDBC ドライバーによるメタデータの処理](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
