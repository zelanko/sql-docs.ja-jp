---
title: getResultSetConcurrency メソッド (SQLServerStatement) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getResultSetConcurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 47ef6547-5ec7-4cf5-a4d4-e34cbeec72eb
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7e776aaff34a88554a34f00f360e8c871e701cbf
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66762686"
---
# <a name="getresultsetconcurrency-method-sqlserverstatement"></a>getResultSetConcurrency メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトによって生成された [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの結果セットのコンカレンシーを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final int getResultSetConcurrency()  
```  
  
## <a name="return-value"></a>戻り値  
 結果セットのコンカレンシーの種類を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getResultSetConcurrency メソッドは、java.sql.Statement インターフェイス内 getResultSetConcurrency メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
