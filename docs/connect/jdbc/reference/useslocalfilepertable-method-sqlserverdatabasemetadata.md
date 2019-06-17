---
title: usesLocalFilePerTable メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.usesLocalFilePerTable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1fafb076-2bb7-4845-9c02-788479f00ca2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ac94bcab076912437e00f24e9f6acababcf01902
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66788886"
---
# <a name="useslocalfilepertable-method-sqlserverdatabasemetadata"></a>usesLocalFilePerTable メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースがテーブルごとにファイルを使用するかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean usesLocalFilePerTable()  
```  
  
## <a name="return-value"></a>戻り値  
 テーブルごとにファイルを使用する場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この usesLocalFilePerTable メソッドは、java.sql.DatabaseMetaData インターフェイスで usesLocalFilePerTable メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
