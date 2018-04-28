---
title: getMaxProcedureNameLength メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getMaxProcedureNameLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e1c05eb3-8465-46fd-99bc-5e8effcafee5
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f70925075a431156842922ce0c248b8e3be3ea07
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getmaxprocedurenamelength-method-sqlserverdatabasemetadata"></a>getMaxProcedureNameLength メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースでプロシージャ名に許容される最大文字数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getMaxProcedureNameLength()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**許可される文字の最大数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getMaxProcedureNameLength メソッドは、java.sql.DatabaseMetaData インターフェイスの getMaxProcedureNameLength メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
