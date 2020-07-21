---
title: getUpdateCount メソッド (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e9570228-4500-44b6-b2f1-84ac050b5112
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f0dcd2b67ef5dcfed234e7fe54ce5c3c5e368d2f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80910798"
---
# <a name="getupdatecount-method-sqlserverstatement"></a>getUpdateCount メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  現在の結果を更新数として取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final int getUpdateCount()  
```  
  
## <a name="return-value"></a>戻り値  
 更新数を含む **int** です。 返された結果が結果セット オブジェクトである場合、または結果がなくなった場合は、-1 が返されます。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getUpdateCount メソッドは、java.sql.Statement インターフェイスの getUpdateCount メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
