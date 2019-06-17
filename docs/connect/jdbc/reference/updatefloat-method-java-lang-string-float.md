---
title: updateFloat メソッド (java.lang.String, float) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateFloat (java.lang.String, float)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 19a6164f-f560-4304-8466-e55f0667a3d4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e348f9c51b68063867a13b9d9bfe6db3e7053645
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66804173"
---
# <a name="updatefloat-method-javalangstring-float"></a>updateFloat (java.lang.String, float) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された列名を使用して、指定された列を **float** 値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateFloat(java.lang.String columnName,  
                        float x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 列名を含む**文字列**です。  
  
 *x*  
  
 A **float**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この updateFloat メソッドは、java.sql.ResultSet インターフェイスの updateFloat メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [updateFloat メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatefloat-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
