---
title: パラメーターを使用して SQL ステートメントの使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3202b88f-ce13-44dd-982c-c6a3b0260378
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c18852f5f1d30378e97c7754b074dd965b7325d0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-an-sql-statement-with-parameters"></a>パラメータがある SQL ステートメントの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  内のデータを使用する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース パラメーターを含む SQL ステートメントを使用すると、使用することができます、 [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)のメソッド、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)を返す、クラス[SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)要求されたデータが含まれる。 これを行うには、作成する必要が最初の SQLServerPreparedStatement オブジェクトを使用して、 [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。  
  
 SQL ステートメントを作成する場合、IN パラメータは ?  (疑問符) 文字で指定します。これはパラメータ値のプレースホルダになり、後で SQL ステートメントに渡されます。 パラメーターの値を指定するには、SQLServerPreparedStatement クラスの setter メソッドのいずれかを行うこともできます。 使用する setter メソッドは、SQL ステートメントに渡す値のデータ型によって決定されます。  
  
 setter メソッドに値を渡す場合は、SQL ステートメントで使用する実際の値だけでなく、SQL ステートメント内のパラメータの順序も指定する必要があります。 たとえば、SQL ステートメントに 1 つのパラメーターが含まれている場合、その序数値は、1 をなります。 ステートメントに 2 つのパラメーターが含まれている場合、最初の序数値 1 である中、2 番目の序数値は 2 になります。  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]関数に渡し、サンプル データベース、およびし、結果を結果セットから読み取って、準備された SQL ステートメントが構築され、1 つの文字列パラメーター値を使用して実行します。  
  
 [!code[JDBC#UsingSQLWithParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_1_1.java)]  
  
## <a name="see-also"></a>参照  
 [SQL でのステートメントの使用](../../connect/jdbc/using-statements-with-sql.md)  
  
  
