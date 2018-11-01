---
title: getFetchDirection メソッド (SQLServerStatement) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ceb4ae68-decc-46d3-83f1-0bbd23aaf58c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3944990d8b6f551ba70545e5cacf42179e7b68ec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47617090"
---
# <a name="getfetchdirection-method-sqlserverstatement"></a>getFetchDirection メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  行をフェッチする方向をデータベース テーブルから取得します。この方向は、[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトから生成される結果セットの既定の方向となります。  
  
> [!NOTE]  
>  このメソッドは、現在 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] では実装されていません。 そのため、このメソッドは常に FETCH_UNKNOWN を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final int getFetchDirection()  
```  
  
## <a name="return-value"></a>戻り値  
 [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md) メソッドによって指定されるフェッチ方向を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getFetchDirection メソッドは、java.sql.Statement インターフェイスの getFetchDirection メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
