---
title: getBigDecimal (java.lang.String, int) メソッド (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBigDecimal (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 572a1799-c232-400f-b8d8-37a5719a8d5e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: db42729446b2007a730c5fda795cf628eea0fc5f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920608"
---
# <a name="getbigdecimal-method-javalangstring-int-sqlserverresultset"></a>getBigDecimal (java.lang.String, int) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの現在の行にある指定された列名の値を、渡された小数点以下桁数を使用して取得します。  
  
> [!NOTE]  
>  このメソッドは、JDBC 仕様では非推奨とされました。 代わりに、[getBigDecimal (java.lang.String)](../../../connect/jdbc/reference/getbigdecimal-method-java-lang-string-sqlserverresultset.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.math.BigDecimal getBigDecimal(java.lang.String columnName,  
                                          int scale)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 列名を含む**文字列**です。  
  
 *scale*  
  
 小数点以下の桁数を示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 BigDecimal オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getBigDecimal メソッドは、java.sql.ResultSet インターフェイスの getBigDecimal メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [getBigDecimal メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbigdecimal-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
