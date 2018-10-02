---
title: findColumn メソッド (SQLServerResultSet) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.findColumn
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7c29994a-0b53-420b-8a9b-82a9eef08587
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a5ff2173990dabafab5297dd195e617825768aef
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837730"
---
# <a name="findcolumn-method-sqlserverresultset"></a>findColumn メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの指定された列名に一致する、最初の列のインデックスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int findColumn(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 列の名前を含む **String**。  
  
## <a name="return-value"></a>戻り値  
 列インデックスを示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この findColumn メソッドは、java.sql.ResultSet インターフェイスの findColumn メソッドによって指定されます。  
  
 同じ名前の列が複数存在する場合、findColumn メソッドは、大文字と小文字を区別して最初に一致した列を返します。 大文字と小文字を区別して一致する列が存在しない場合は、大文字と小文字の区別に関係なく最初に一致した列を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
