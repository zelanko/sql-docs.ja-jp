---
title: getUnicodeStream メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
- SQLServerResultSet.getUnicodeStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0dd61865-663b-47e2-b417-e9df418894cc
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6c4de8b8cc9c073fee348c20f49f782e692a3240
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getunicodestream-method-sqlserverresultset"></a>getUnicodeStream メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) Unicode 文字のストリームとしてオブジェクト。  
  
> [!NOTE]  
>  このメソッドは、JDBC 仕様で非推奨とされます。このメソッドを呼び出すと、"未実装" 例外がスローされます。 代わりに、使用する必要があります、 [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)メソッドです。  
  
## <a name="overload-list"></a>オーバーロードの一覧  
  
|名前|Description|  
|----------|-----------------|  
|[getUnicodeStream メソッド&#40;int&#41;](../../../connect/jdbc/reference/getunicodestream-method-int.md)|この現在の行に指定された列インデックスの値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) Unicode 文字のストリームとしてオブジェクト。|  
|[getUnicodeStream メソッド&#40;java.lang.String&#41;](../../../connect/jdbc/reference/getunicodestream-method-java-lang-string.md)|この現在の行に指定された列名の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) Unicode 文字のストリームとしてオブジェクト。|  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
