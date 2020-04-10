---
title: getResultSetHoldability メソッド (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getResultSetHoldability
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 053549ee-2018-47ab-9538-789dac2b150a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f9ec0453bc56c0918d4959ec68924eca6e573dc2
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921825"
---
# <a name="getresultsetholdability-method-sqlserverstatement"></a>getResultSetHoldability メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerStatement](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトによって生成された [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトの結果セットの保持機能を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final int getResultSetHoldability()  
```  
  
## <a name="return-value"></a>戻り値  
 結果セットの保持機能を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getResultSetHoldability メソッドは、java.sql.Statement インターフェイスの getResultSetHoldability メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
