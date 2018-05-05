---
title: getPrecision メソッド (SQLServerParameterMetaData) |Microsoft ドキュメント
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
- SQLServerParameterMetaData.getPrecision
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8bd79484-bab6-423b-978f-d7ec7132ebeb
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aaedd40b28aabcfda5ebf5526cf6921807876054
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getprecision-method-sqlserverparametermetadata"></a>getPrecision メソッド (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターの 10 進数字の数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getPrecision(int param)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *param*  
  
 **Int**パラメーター インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 **Int**を示す、指定されたパラメーターの有効桁数です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getPrecision メソッドは、java.sql.ParameterMetaData インターフェイスの getPrecision メソッドによって指定されます。  
  
 数値型の場合、このメソッドは 10 進の桁数を取得します。 文字型の場合は、最大文字列長を取得します。 バイナリ型の場合は、最大長をバイト単位で取得します。 桁数が不明である場合、このメソッドは "0" を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerParameterMetaData のメソッド](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData のメンバー](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData クラス](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
