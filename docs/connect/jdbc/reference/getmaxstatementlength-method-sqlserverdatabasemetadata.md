---
title: getMaxStatementLength メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxStatementLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f45fcf45-b9e7-4d14-a90a-ebc542ac7755
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b007954bacff570760e46b1563e59a5323dfd670
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66792426"
---
# <a name="getmaxstatementlength-method-sqlserverdatabasemetadata"></a>getMaxStatementLength メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースで SQL ステートメントに許容される最大文字数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getMaxStatementLength()  
```  
  
## <a name="return-value"></a>戻り値  
 許容される最大文字数を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getMaxStatementLength メソッドは、java.sql.DatabaseMetaData インターフェイスで getMaxStatementLength メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
