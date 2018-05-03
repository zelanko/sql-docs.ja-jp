---
title: setMaxRows メソッド (SQLServerStatement) |Microsoft ドキュメント
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
apiname:
- SQLServerStatement.setMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cccc0667-589b-4655-8ea8-14ae8b2eb9dc
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9b0a3c75d6da7805a462df3cd7ff8be8c9c9448
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="setmaxrows-method-sqlserverstatement"></a>setMaxRows メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  行の最大数の上限を設定する[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトは、指定した数値を含めることができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setMaxRows(int max)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *max*  
  
 **Int**制限がない場合は、行、または 0 の最大数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setMaxRows メソッドは、java.sql.Statement インターフェイスの setMaxRows メソッドによって指定されます。  
  
 この setMaxRows メソッドには、動的カーソルのスクロール可能な効果がありません。 大きな結果セットから行が返される可能性がある場合に、返される行数を制限するには、アプリケーションで SELECT TOP N SQL 構文を使用してください。  
  
 SetMaxRows メソッドが呼び出されたときに、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]アプリケーションのクエリを実行するときに、SET ROWCOUNT SQL ステートメントを実行します。 これにより、JDBC ドライバーをすべて影響を受ける行の最大数を制限する、[!INCLUDE[tsql](../../../includes/tsql_md.md)]そのクエリによって返される行の数だけでなく、そのクエリによって実行されるステートメントです。 最上位レベルにのみ制限を設定するアプリケーションに必要なかどうかは[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトの setMaxRows メソッドではなく、クエリ内で SELECT TOP N SQL 構文を使用して必要があります。  
  
 SET ROWCOUNT SQL ステートメントの詳細については、次を参照してください。、"[SET ROWCOUNT (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=139522)」の「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
