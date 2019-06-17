---
title: nullPlusNonNullIsNull メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.nullPlusNonNullIsNull
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c594736f-3a9b-463f-bbd8-eaf9221230ea
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 096113ec5fa76be364dcf7e51fd3d457a2a76f1f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779517"
---
# <a name="nullplusnonnullisnull-method-sqlserverdatabasemetadata"></a>nullPlusNonNullIsNull メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  NULL 値と NULL 以外の値の連結を NULL とすることを、データベースがサポートするかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean nullPlusNonNullIsNull()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**連結がサポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この nullPlusNonNullIsNull メソッドは、java.sql.DatabaseMetaData インターフェイスで nullPlusNonNullIsNull メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
