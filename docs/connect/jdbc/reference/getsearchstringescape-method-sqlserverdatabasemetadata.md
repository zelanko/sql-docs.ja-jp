---
title: getSearchStringEscape メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSearchStringEscape
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ea0f95d0-0238-4dc8-9f26-7ff9b65f30c3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0eb3fd98c42615dba674e31ed2007fbcfc22f4ac
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
  
  
