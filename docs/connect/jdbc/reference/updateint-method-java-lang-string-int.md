---
title: updateInt メソッド (java.lang.String, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateInt (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b0aef8f7-057e-4b57-892c-d120f2daed77
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 11ee34cd5281fb7db564e965556ff5ee455fb7d0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67998850"
---
# <a name="updateint-method-javalangstring-int"></a>updateInt (java.lang.String, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された列名を使用して、指定された列を **int** 値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateInt(java.lang.String columnName,  
                      int x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 列名を含む**文字列**です。  
  
 *x*  
  
 **int** 値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateInt メソッドは、java.sql.ResultSet インターフェイスの updateInt メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [updateInt メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateint-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
