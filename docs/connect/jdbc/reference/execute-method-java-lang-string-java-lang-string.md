---
title: "execute (java.lang.String, java.lang.String) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerStatement.execute (java.lang.String.java.lang.String[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9451c7c2-4c0d-4d1e-9b42-a26ff28e3f6a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9dc327a107a8a164e00f2f34f21515c96766e21d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="execute-method-javalangstring-javalangstring"></a>execute (java.lang.String, java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された SQL ステートメントを実行、複数の結果、および信号を返す可能性のある[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]渡された配列に示される自動生成キーを検索可能にする必要があることです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final boolean execute(java.lang.String sql,  
                             java.lang.String[] columnNames)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sql*  
  
 A**文字列**SQL ステートメントを含むです。  
  
 *columnNames*  
  
 検索可能にする自動生成キーの列名を示す文字列の配列です。  
  
## <a name="return-value"></a>戻り値  
 **true**最初の結果が結果セットである場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この execute メソッドは、java.sql.Statement インターフェイスの execute メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [方法 &#40; を実行します。SQLServerStatement &#41;](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

