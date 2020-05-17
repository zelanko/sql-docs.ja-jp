---
title: executeQuery メソッド (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeQuery
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 599cf463-e19f-4baa-bacb-513cad7c6cd8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d66ceda5c9afee28240de5af9fe833acd4e25bbb
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67954774"
---
# <a name="executequery-method-sqlserverstatement"></a>executeQuery メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された SQL ステートメントを実行し、1 つの [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sql*  
  
 SQL ステートメントを含む**文字列**です。  
  
## <a name="return-value"></a>戻り値  
 SQLServerResultSet オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この executeQuery メソッドは、java.sql.Statement インターフェイスの executeQuery メソッドで規定されています。  
  
 渡された SQL ステートメントによって 1 つの [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverexception-class.md) オブジェクト以外のものが生成された場合は、[SQLServerException](../../../connect/jdbc/reference/sqlserverresultset-class.md) がスローされます。  
  
 更新数が 1 より大きくなる (または複数の結果セットが生成される) ストアド プロシージャは [execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) メソッドを使用して実行してください。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
