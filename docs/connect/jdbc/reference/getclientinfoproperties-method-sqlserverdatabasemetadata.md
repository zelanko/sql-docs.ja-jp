---
title: "getClientInfoProperties メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1568aef4-f4c4-40a0-a1ab-9c106905bd92
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 022f09c50d0a47851e375fcbb617ee40266dbb38
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getclientinfoproperties-method-sqlserverdatabasemetadata"></a>getClientInfoProperties メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  ドライバーがサポートしているクライアント情報のプロパティの一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getClientInfoProperties()  
```  
  
## <a name="return-value"></a>戻り値  
 結果セット オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getClientInfoProperties メソッドは、java.sql.DatabaseMetaData インターフェイスの getClientInfoProperties メソッドによって指定されます。  
  
> [!NOTE]  
>  このメソッドでは、空の結果セットが返されます。 ドライバーは、設定のみをサポートしています、 **applicationName**設定と、 **applicationName**接続時にのみです。 SQL Server では、接続が確立された後のクライアント アプリケーション情報の更新はサポートされていません。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

