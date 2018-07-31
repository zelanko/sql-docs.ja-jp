---
title: SQL ステートメントを使用したデータベース オブジェクトの変更 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b126fb0b5a72688c1801cf8854d8035763c8245f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38040580"
---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>SQL ステートメントを使用したデータベース オブジェクトの変更
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  SQL ステートメントを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベース オブジェクトを変更するには、[SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) クラスの [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) メソッドを使用します。 executeUpdate メソッドは、SQL ステートメントをデータベースに渡して処理し、影響を受けた行がないために値 0 を返します。  
  
 この場合、最初に [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) クラスの [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) メソッドを使用して、SQLServerStatement オブジェクトを作成する必要があります。  
  
> [!NOTE]  
>  データベース内のオブジェクトを変更する SQL ステートメントは、データ定義言語 (DDL) ステートメントと呼ばれます。 これらには、CREATE TABLE、DROP TABLE、CREATE INDEX、DROP INDEX などのステートメントが含まれます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] でサポートされる DDL ステートメントの種類の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] オンライン ブックを参照してください。  
  
 次の例は、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースに対して開いている接続を関数に渡して、データベースにシンプルな TestTable を作成する SQL ステートメントを作成および実行し、戻り値を出力します。  
  
 [!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]  
  
## <a name="see-also"></a>参照  
 [SQL でのステートメントの使用](../../connect/jdbc/using-statements-with-sql.md)  
  
  
