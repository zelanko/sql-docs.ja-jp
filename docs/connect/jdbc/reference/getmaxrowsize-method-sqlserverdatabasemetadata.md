---
title: getMaxRowSize メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxRowSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: abb5a204-76ff-4381-ab2b-896a19b202f3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 52a8c0cb991a30ad7327edea8823b9307e56fc81
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66792479"
---
# <a name="getmaxrowsize-method-sqlserverdatabasemetadata"></a>getMaxRowSize メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースで許容される 1 行の最大バイト数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getMaxRowSize()  
```  
  
## <a name="return-value"></a>戻り値  
 許容される最大バイト数を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getMaxRowSize メソッドは、java.sql.DatabaseMetaData インターフェイスで getMaxRowSize メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
