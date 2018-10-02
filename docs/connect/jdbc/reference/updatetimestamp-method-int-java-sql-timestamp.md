---
title: updateTimestamp (int, java.sql.Timestamp) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateTimestamp (int, java.sql.Timestamp)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: db83d9d7-137b-4a28-a2ca-d4782e0a256e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 287f5a80d02336df0d78a479f35c51fda8c8f37e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811530"
---
# <a name="updatetimestamp-method-int-javasqltimestamp"></a>updateTimestamp (int, java.sql.Timestamp) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された列インデックスを使用して、指定された列をタイムスタンプ値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateTimestamp(int index,  
                            java.sql.Timestamp x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *index*  
  
 列インデックスを示す **int** です。  
  
 *x*  
  
 タイムスタンプ値です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この updateTimestamp メソッドは、java.sql.ResultSet インターフェイスの updateTimestamp メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [updateTimestamp メソッド (SQLServerResultSet)](../../../connect/jdbc/reference/updatetimestamp-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
