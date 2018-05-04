---
title: isCurrency メソッド (SQLServerResultSetMetaData) |Microsoft ドキュメント
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
- SQLServerResultSetMetaData.isCurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7fe25d90-693c-4d3b-9dd2-0f8351c5a9ed
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 885e7a8f8f1e32822530b4afa414415e2b667db6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="iscurrency-method-sqlserverresultsetmetadata"></a>isCurrency メソッド (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列がキャッシュの値かどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isCurrency(int column)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *column*  
  
 列インデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 **true**列がキャッシュの値である場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この isCurrency メソッドは、java.sql.ResultSetMetaData インターフェイスの isCurrency メソッドによって指定されます。  
  
 このメソッドは**true**でのみ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]money および smallmoney データ型。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSetMetaData のメソッド](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData のメンバー](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
