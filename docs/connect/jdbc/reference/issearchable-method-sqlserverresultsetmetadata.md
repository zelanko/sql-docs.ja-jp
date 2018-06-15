---
title: isSearchable メソッド (SQLServerResultSetMetaData) |Microsoft ドキュメント
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
- SQLServerResultSetMetaData.isSearchable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 10cf54f9-ef42-475e-8397-790306934573
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d11c732b5b75b79c7016f6affebab0a8db49e774
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32843667"
---
# <a name="issearchable-method-sqlserverresultsetmetadata"></a>isSearchable メソッド (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列を SQL の WHERE 句で使用できるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isSearchable(int column)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *column*  
  
 列インデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 **true**場合は、列は、WHERE 句で使用できます。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この isSearchable メソッドは、java.sql.ResultSetMetaData インターフェイスの isSearchable メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSetMetaData のメソッド](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData のメンバー](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
