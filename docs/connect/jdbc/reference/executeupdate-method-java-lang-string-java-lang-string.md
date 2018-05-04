---
title: executeUpdate (java.lang.String, java.lang.String) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerStatement.executeUpdate (java.lang.String[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2f44a689-65c8-4c94-9574-e9c08ea7918e
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 81b6cefcc7749704c6bb015fa28a679bb1832e7d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
  
 更新数が 1 より大きくなる (または複数の結果セットが生成される) ストアド プロシージャは [execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) メソッドを使用して実行してください。  
  
## <a name="see-also"></a>参照  
 [executeUpdate メソッド&#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
