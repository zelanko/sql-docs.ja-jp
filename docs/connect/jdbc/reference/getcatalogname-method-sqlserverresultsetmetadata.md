---
title: getCatalogName メソッド (SQLServerResultSetMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.getCatalogName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 64f62569-5d8e-411f-a98d-ddc52798391e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dcf7c0b513726db49615b8ab85e99493b8a7cb41
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730492"
---
# <a name="getcatalogname-method-sqlserverresultsetmetadata"></a>getCatalogName メソッド (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定した列が含まれるテーブルのカタログ名を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getCatalogName(int column)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *column*  
  
 列インデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 カタログ名を含む**文字列**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getCatalogName メソッドは、java.sql.ResultSetMetaData インターフェイスで getCatalogName メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSetMetaData メソッド](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData メンバー](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
