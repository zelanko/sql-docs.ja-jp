---
title: getParameterCount メソッド (SQLServerParameterMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getParameterCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7dbbdacb-74ef-42e7-9bdc-a3229505dad8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 74c2228b944dce2f9c59f4f8fcfc4bc0ac2e5753
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67980992"
---
# <a name="getparametercount-method-sqlserverparametermetadata"></a>getParameterCount メソッド (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) オブジェクトに情報が含まれる [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md) オブジェクトのパラメーター数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getParameterCount()  
```  
  
## <a name="return-value"></a>戻り値  
 パラメーターの数を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getParameterCount メソッドは、java.sql.ParameterMetaData インターフェイスの getParameterCount メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerParameterMetaData のメソッド](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData のメンバー](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData クラス](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
