---
title: getParameterTypeName メソッド (SQLServerParameterMetaData) |Microsoft ドキュメント
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
- SQLServerParameterMetaData.getParameterTypeName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ebe7ff0f-3cc0-408e-9503-4ca754c9c37f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ccf9dcb6060bee66379c97cecfd54d3be6c5a384
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getparametertypename-method-sqlserverparametermetadata"></a>getParameterTypeName メソッド (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターのデータベース固有の型名を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getParameterTypeName(int param)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *param*  
  
 **Int**パラメーター インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 A**文字列**型名を格納しています。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getParameterTypeName メソッドは、java.sql.ParameterMetaData インターフェイスの getParameterTypeName メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerParameterMetaData のメソッド](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData のメンバー](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData クラス](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
