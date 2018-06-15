---
title: 戻り値を持つストアド プロシージャを使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4b126e95-8458-41d6-af37-fc6662859f19
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 29bb95c06d86ad4d6e45002da1429f6c7d5a5c9e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32853157"
---
# <a name="using-a-stored-procedure-with-a-return-status"></a>状態の戻り値があるストアド プロシージャの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  A[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ストアド プロシージャを呼び出すことができますが、状態パラメーターまたは結果のパラメーターを返します。 この戻り値は一般的に、ストアド プロシージャの成功または失敗を示すために使用されます。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]提供、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスは、この種類のストアド プロシージャを呼び出すと、返されるデータを処理を行うこともできます。  
  
 JDBC ドライバーを使用してこの種類のストアド プロシージャを呼び出すときに使用する必要が、 `call` SQL エスケープ シーケンスと組み合わせて、 [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラス. 構文、`call`状態の戻り値パラメーターを持つエスケープ シーケンスは、次。  
  
 `{[?=]call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  SQL エスケープ シーケンスの詳細については、次を参照してください。 [SQL エスケープ シーケンスを使用して](../../connect/jdbc/using-sql-escape-sequences.md)です。  
  
 構築する場合、`call`エスケープ シーケンスを使用して、状態の戻り値パラメーターを指定しますか? (疑問符) 文字で指定します。 この文字は、ストアド プロシージャから返されるパラメーター値のプレース ホルダーとして機能します。 状態の戻り値パラメーターの値を指定するを使用して、パラメーターのデータ型を指定する必要があります、 [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)ストアド プロシージャを実行する前に、SQLServerCallableStatement クラスのメソッドです。  
  
> [!NOTE]  
>  を SQL Server データベースと JDBC ドライバーを使用する場合は、registerOutParameter メソッドの戻り値の状態パラメーターに指定した値は、java.sql.Types.INTEGER データ型を使用して指定することができる整数を常になります。  
  
 さらに、状態の戻り値パラメーターの registerOutParameter メソッドに値を渡す場合は、ストアド プロシージャ呼び出しでパラメーターの順序は、パラメーターに使用するデータ型だけでなくを指定する必要があります。 状態の戻り値パラメーターは、ストアド プロシージャの呼び出しにおいて常に最初のパラメーターであるため、位置を示す序数は常に 1 になります。 SQLServerCallableStatement クラスでは、特定のパラメーターを示すために、パラメーターの名前を使用するためのサポートを提供しますが、状態の戻り値パラメーターのパラメーターの序数位置番号だけを使用できます。  
  
 たとえばで次のストアド プロシージャを作成、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
CREATE PROCEDURE CheckContactCity  
   (@cityName CHAR(50))  
AS  
BEGIN  
   IF ((SELECT COUNT(*)  
   FROM Person.Address  
   WHERE City = @cityName) > 1)  
   RETURN 1  
ELSE  
   RETURN 0  
END  
```  
  
 このストアド プロシージャでは、cityName パラメーターで指定された都市名が Person.Address テーブルに存在するかどうかによって、1 または 0 の状態値が返されます。  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベースが、関数に渡されたと[実行](../../connect/jdbc/reference/execute-method-sqlserverstatement.md)CheckContactCity ストアド プロシージャを呼び出すメソッドを使用します。  
  
 [!code[JDBC#UsingSprocWithReturnStatus1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_1_1.java)]  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャでのステートメントの使用](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
