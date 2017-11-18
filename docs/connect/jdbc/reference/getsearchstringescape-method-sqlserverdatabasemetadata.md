---
title: "getSearchStringEscape メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
apiname:
- SQLServerDatabaseMetaData.getSearchStringEscape
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ea0f95d0-0238-4dc8-9f26-7ff9b65f30c3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f1008cd0fdec7aa60d9d66c62cfb08ad84ca1cd5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getsearchstringescape-method-sqlserverdatabasemetadata"></a>getSearchStringEscape メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  取得、**文字列**ワイルドカード文字をエスケープするために使用できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getSearchStringEscape()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**ワイルドカード文字のエスケープ文字列を格納しています。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getSearchStringEscape メソッドは、java.sql.DatabaseMetaData インターフェイスの getSearchStringEscape メソッドによって指定されます。  
  
 このメソッドは、メタデータのパターン検索にだけ使用されます。 返されます"\\"です。 A**文字列**検索パターンには、ワイルドカード (「%」および「_」) をエスケープし、バック スラッシュを付加することによってリテラルとして提供します。 解釈されます"\\%"を「[%]」と"\\\_"を"[\_]"です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

