---
title: 複数の結果セットの使用 |Microsoft ドキュメント
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
ms.topic: article
ms.assetid: ab6a3cfa-073b-44e9-afca-a8675cfe5fd1
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1710bcf725939955b0064490bcfbe23928576430
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-multiple-result-sets"></a>複数の結果セットの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  インライン SQL を使用する場合または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]1 つ以上の結果セットを返すストアド プロシージャ、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]提供、 [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)メソッドで、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)クラス返されるデータの各セットを取得しています。 さらに、ステートメントを実行するには、1 つ以上の結果セットが返される、ときに行うこともできます、[実行](../../connect/jdbc/reference/execute-method-sqlserverstatement.md)SQLServerStatement のメソッドのクラスを返すため、**ブール**場合を示す値、返される値は、結果セットを更新数。  
  
 Execute メソッドが返された場合**true**、実行されたステートメントには、1 つまたは複数の結果セットが返されました。 最初の結果セットの getResultSet メソッドを呼び出すことによってアクセスできます。 結果セットが使用可能な場合を呼び出すことができますを決定する、 [getMoreResults](../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)を返すメソッド、**ブール**の値**true**の結果セットがある場合。 次の結果セットが使用可能な場合は、すべての結果セットが処理されるまで、処理を続行にアクセスし、もう一度 getResultSet メソッドを呼び出すことができます。 GetMoreResults メソッドを返す場合**false**プロセスにない複数の結果セットがあります。  
  
 Execute メソッドが返された場合**false**、実行されたステートメントには、呼び出すことによって取得できる更新カウント値が返される、 [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)メソッドです。  
  
> [!NOTE]  
>  更新数の詳細については、次を参照してください。[ストアド プロシージャを使用して、更新数を含む](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md)です。  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベースが関数に渡され、SQL ステートメントを作成、実行すると、セットを返す 2 つの結果。  
  
 [!code[JDBC#UsingMultipleResultSets1](../../connect/jdbc/codesnippet/Java/using-multiple-result-sets_1.java)]  
  
 この例では、返される結果セット数は 2 であることがわかっています。 ただし、ストアド プロシージャを呼び出す場合のように、返される結果セット数が不明でも、すべての結果セットが処理されるようにコードが作成されています。 複数の結果セットと更新数を返すストアド プロシージャの呼び出しの例を参照してください[複雑なステートメントの処理](../../connect/jdbc/handling-complex-statements.md)です。  
  
> [!NOTE]  
>  GetMoreResults、SQLServerStatement クラスのメソッドの呼び出しを行うと、前に返された結果セットは暗黙的に閉じられます。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーでのステートメントの使用](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
