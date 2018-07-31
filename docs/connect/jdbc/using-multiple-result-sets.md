---
title: 複数の結果セットの使用 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ab6a3cfa-073b-44e9-afca-a8675cfe5fd1
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b4f3c8b75d18b598bfe43a48969f098022893c8b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37978734"
---
# <a name="using-multiple-result-sets"></a>複数の結果セットの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  複数の結果セットを返すインライン SQL または [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ストアド プロシージャを処理する場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] では返される各データのセットを取得するために、[SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) クラスの [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md) メソッドを提供します。 また、複数の結果セットを返すステートメントの実行時には、SQLServerStatement クラスの [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) メソッドを使用できます。これは、返される値が結果セットと更新数のどちらであるかを示す **boolean** 値を返せるためです。  
  
 execute メソッドから **true** が返された場合、実行されたステートメントから返されるのは 1 つ以上の結果セットです。 最初の結果セットには、getResultSet メソッドを呼び出すことでアクセスできます。 他にも使用可能な結果セットがあるかどうかを判断するには、[getMoreResults](../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md) メソッドを呼び出すことができます。このメソッドでは、他にも使用可能な結果セットがある場合、**boolean** 値として **true** が返されます。 他にも結果セットが使用可能な場合は、getResultSet メソッドを再度呼び出して結果セットにアクセスし、すべての結果セットが処理されるまで続けます。 GetMoreResults メソッドを返す場合**false**、処理するない複数の結果セットがあります。  
  
 execute メソッドから **false** が返された場合、実行されたステートメントから返されるのは更新数の値です。更新数の値は、[getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) メソッドを呼び出すことで取得できます。  
  
> [!NOTE]  
>  更新数の詳細については、次を参照してください。[更新数は、ストアド プロシージャを使用して](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md)します。  
  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースに対して開いている接続が関数に渡され、実行時に 2 つの結果セットを返す SQL ステートメントが作成されています。  
  
 [!code[JDBC#UsingMultipleResultSets1](../../connect/jdbc/codesnippet/Java/using-multiple-result-sets_1.java)]  
  
 この例では、返される結果セット数は 2 であることがわかっています。 ただし、ストアド プロシージャを呼び出す場合のように、返される結果セット数が不明でも、すべての結果セットが処理されるようにコードが作成されています。 複数の結果セットと更新数を返すストアド プロシージャを呼び出す例については、「[複雑なステートメントの処理](../../connect/jdbc/handling-complex-statements.md)」を参照してください。  
  
> [!NOTE]  
>  SQLServerStatement クラスの getMoreResults メソッドの呼び出しを行った場合に、前に返された結果セットは暗黙的に閉じられます。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーでのステートメントの使用](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
