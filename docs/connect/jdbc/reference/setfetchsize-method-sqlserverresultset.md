---
title: setFetchSize メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
apiname:
- SQLServerResultSet.setFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 233bf4f8-4758-42d0-a80b-33e34fa78027
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2344b1701a66621665a4ea1179e74b602141918d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="setfetchsize-method-sqlserverresultset"></a>setFetchSize メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  複数の行は、この必要な場合に、データベースからフェッチする必要があります行の数についてのヒントを JDBC ドライバーに提供[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setFetchSize(int rows)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *rows*  
  
 **Int**をフェッチする行の数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setFetchSize メソッドは、java.sql.ResultSet インターフェイスの setFetchSize メソッドによって指定されます。  
  
 指定されたフェッチ サイズが 0 の場合、JDBC ドライバーはこの値を無視し、必要となるフェッチ サイズを推測します。 既定値によって設定されます、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)結果セットを作成するオブジェクト。 フェッチ サイズはいつでも変更できます。  
  
 このメソッドは、サーバー カーソルのブロック フェッチ サイズを変更します。この効果は、次回 JDBC ドライバーで sp_cursorfetch の呼び出しが必要となったときに有効となります。 フェッチ サイズを 0 に設定すると、現在使用しているカーソルの種類の既定のフェッチ サイズが復元されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
