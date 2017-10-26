---
title: "getParameterCount メソッド (SQLServerParameterMetaData) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerParameterMetaData.getParameterCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7dbbdacb-74ef-42e7-9bdc-a3229505dad8
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5928f7a848a887078f102b010f3e92d6d900f231
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getparametercount-method-sqlserverparametermetadata"></a>getParameterCount メソッド (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  内のパラメーターの数を取得、 [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)対象のオブジェクト[SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)オブジェクト情報を格納します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getParameterCount()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**パラメーターの数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getParameterCount メソッドは、java.sql.ParameterMetaData インターフェイスの getParameterCount メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerParameterMetaData のメソッド](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData のメンバー](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData クラス](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  

