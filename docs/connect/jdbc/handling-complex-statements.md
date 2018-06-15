---
title: 複雑なステートメントの処理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6b807a45-a8b5-4b1c-8b7b-d8175c710ce0
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 28d97ab51a98204d76b8a4f765103f0b4b096894
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32828647"
---
# <a name="handling-complex-statements"></a>複雑なステートメントの処理
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  使用すると、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]、実行時に動的に生成されるステートメントなど、複雑なステートメントを処理する必要があります。 複雑なステートメントは、更新、挿入、および削除などのさまざまなタスクを頻繁に実行します。 これらの種類のステートメントは、複数の結果セットや出力パラメーターを返すこともあります。 こうした状況では、ステートメントを実行する Java コードが、返されるデータやオブジェクトの型および数について事前に知らない場合があります。  
  
 複雑なステートメントを効率的に処理するため、JDBC ドライバーでは、返されるオブジェクトやデータをクエリし、アプリケーションがそれらを正しく処理するための多くのメソッドが用意されています。 複雑なステートメントを処理するキーは、[実行](../../connect/jdbc/reference/execute-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)クラスです。 このメソッドが戻る、**ブール**値。 値が true の場合、ステートメントから返される最初の結果は結果セットです。 値が false の場合、返される最初の結果は更新数です。  
  
 オブジェクトまたは返されたデータの型がわかっている場合に、いずれかを使用できる、 [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)または[getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)そのデータを処理するメソッド。 続行するには次のオブジェクトまたは複雑なステートメントから返されるデータを呼び出すことができます、 [getMoreResults](../../connect/jdbc/reference/getmoreresults-method.md)メソッドです。  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベースに渡して、関数、ストアド プロシージャの呼び出しでは、SQL ステートメントと組み合わせて複雑なステートメントが構築された、ステートメントを実行すると、し、`do`ループがあります。すべての結果セットおよび返されるカウントが更新を処理するために使用します。  
  
 [!code[JDBC#HandlingComplexStatements1](../../connect/jdbc/codesnippet/Java/handling-complex-statements_1.java)]  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーでのステートメントの使用](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
