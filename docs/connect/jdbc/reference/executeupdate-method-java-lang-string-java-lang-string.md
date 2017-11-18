---
title: "executeUpdate (java.lang.String, java.lang.String) メソッド |Microsoft ドキュメント"
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
- SQLServerStatement.executeUpdate (java.lang.String[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2f44a689-65c8-4c94-9574-e9c08ea7918e
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 53682225a680d9913fd03e4e7a52beee729eecbc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="executeupdate-method-javalangstring-javalangstring"></a>executeUpdate (java.lang.String, java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された SQL ステートメントと信号実行[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]自動生成キーが指定された配列に示されるが利用できるように取得するためです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final int executeUpdate(java.lang.String sql,  
                               java.lang.String[] columnNames)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sql*  
  
 A**文字列**SQL ステートメントを含むです。  
  
 *columnNames*  
  
 型の配列**文字列**のど自動生成キーの列名を可能にするかを示すです。  
  
## <a name="return-value"></a>戻り値  
 **Int**を示す行の数、影響を受ける 0 DDL ステートメントを使用する場合。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この executeUpdate メソッドは、java.sql.Statement インターフェイスの executeUpdate メソッドによって指定されます。  
  
 更新数、1 より大きいかを使用して、1 つ以上の結果セットを生成する結果がストアド プロシージャを実行する場合、[実行](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)ストアド プロシージャを実行するメソッド。  
  
## <a name="see-also"></a>参照  
 [executeUpdate メソッド & #40 です。SQLServerStatement &#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

