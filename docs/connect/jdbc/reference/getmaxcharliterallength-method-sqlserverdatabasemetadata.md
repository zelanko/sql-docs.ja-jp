---
title: getMaxCharLiteralLength メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
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
- SQLServerDatabaseMetaData.getMaxCharLiteralLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 44e6e9df-4724-4c86-bbd2-ca750c248333
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 59e2a3d543e8fd6346b42fa602032e7241d6c357
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getmaxcharliterallength-method-sqlserverdatabasemetadata"></a>getMaxCharLiteralLength メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースで文字リテラルに許容される最大文字数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getMaxCharLiteralLength()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**許可される文字の最大数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getMaxCharLiteralLength メソッドは、java.sql.DatabaseMetaData インターフェイスの getMaxCharLiteralLength メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
