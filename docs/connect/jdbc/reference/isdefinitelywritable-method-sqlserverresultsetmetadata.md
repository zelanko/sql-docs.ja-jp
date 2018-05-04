---
title: isDefinitelyWritable メソッド (SQLServerResultSetMetaData) |Microsoft ドキュメント
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
- SQLServerResultSetMetaData.isDefinitelyWritable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7650e89a-dc8e-43ca-8eb2-f962f1a4b4ae
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17d20197426efa622efb0be8c8a58b7bfcd9adc7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="isdefinitelywritable-method-sqlserverresultsetmetadata"></a>isDefinitelyWritable メソッド (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列への書き込みが確実に成功するかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isDefinitelyWritable(int column)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *column*  
  
 列インデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 **true**列への書き込みが確実に行われる場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この isDefinitelyWritable メソッドは、java.sql.ResultSetMetaData インターフェイスの isDefinitelyWritable メソッドによって指定されます。  
  
> [!NOTE]  
>  使用する場合、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]で、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データベースでは、このメソッドは常に false を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSetMetaData のメソッド](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData のメンバー](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
