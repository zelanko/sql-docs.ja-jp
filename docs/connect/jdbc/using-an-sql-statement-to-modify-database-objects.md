---
title: "データベース オブジェクトを変更する SQL ステートメントの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d5b94ff83ef6cea934efb66f6efb9394d2fa2501
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>SQL ステートメントを使用したデータベース オブジェクトの変更
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  変更する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]できますを使用する SQL ステートメントを使用して、データベース オブジェクト、 [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)クラスです。 ExecuteUpdate メソッドは、処理にデータベースに SQL ステートメントを渡すし、影響を受けた行がないため、値 0 を返します。  
  
 これを行うには、作成する必要が最初に、SQLServerStatement オブジェクトを使用して、 [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。  
  
> [!NOTE]  
>  データベース内のオブジェクトを変更する SQL ステートメントは、データ定義言語 (DDL) ステートメントと呼ばれます。 これらには、CREATE TABLE、DROP TABLE、CREATE INDEX、DROP INDEX などのステートメントが含まれます。 サポートされている DDL ステートメントの種類の詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を参照してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]関数に渡し、サンプル データベース、SQL ステートメントが作成されて、データベースで単純な TestTable を作成するが、ステートメントを実行し、戻り値が表示されます。  
  
 [!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]  
  
## <a name="see-also"></a>参照  
 [Sql ステートメントを使用します。](../../connect/jdbc/using-statements-with-sql.md)  
  
  
