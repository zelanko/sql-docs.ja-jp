---
title: getMaxColumnsInTable メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxColumnsInTable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dbcad2e1-7508-49ff-9f6d-db11200d87b6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2f148968bd005d692871c8a2549687451fc3ee33
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66792675"
---
# <a name="getmaxcolumnsintable-method-sqlserverdatabasemetadata"></a>getMaxColumnsInTable メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースでテーブルに許容される最大の列数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getMaxColumnsInTable()  
```  
  
## <a name="return-value"></a>戻り値  
 許容される最大の列数を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getMaxColumnsInTable メソッドは、java.sql.DatabaseMetaData インターフェイスで getMaxColumnsInTable メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
