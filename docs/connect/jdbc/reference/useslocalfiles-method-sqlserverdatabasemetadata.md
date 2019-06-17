---
title: usesLocalFiles メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.usesLocalFiles
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 69afb3a9-ed56-4191-88b8-bc46c03b817b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9fdbdf51d97a8b28bb7b357ea45cee09dc40133c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66788952"
---
# <a name="useslocalfiles-method-sqlserverdatabasemetadata"></a>usesLocalFiles メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースがテーブルをローカル ファイルに格納するかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean usesLocalFiles()  
```  
  
## <a name="return-value"></a>戻り値  
 データベースがローカル ファイルを使用する場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この usesLocalFiles メソッドは、java.sql.DatabaseMetaData インターフェイスで usesLocalFiles メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
