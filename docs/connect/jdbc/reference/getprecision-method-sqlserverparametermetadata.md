---
title: getPrecision メソッド (SQLServerParameterMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getPrecision
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8bd79484-bab6-423b-978f-d7ec7132ebeb
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4f7959476f092389f22f2d7720927907b8f59d69
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66771352"
---
# <a name="getprecision-method-sqlserverparametermetadata"></a>getPrecision メソッド (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターの 10 進の桁数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getPrecision(int param)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *param*  
  
 パラメーターのインデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 指定されたパラメーターの有効桁数を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getPrecision メソッドは、java.sql.ParameterMetaData インターフェイスで getPrecision メソッドによって指定されます。  
  
 数値型の場合、このメソッドは 10 進の桁数を取得します。 文字型の場合は、最大文字列長を取得します。 バイナリ型の場合は、最大長をバイト単位で取得します。 桁数が不明である場合、このメソッドは "0" を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerParameterMetaData のメソッド](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData のメンバー](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData クラス](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
