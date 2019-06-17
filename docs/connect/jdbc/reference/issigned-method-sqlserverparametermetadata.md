---
title: isSigned メソッド (SQLServerParameterMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.isSigned
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1a4af386-e379-4a60-a107-a99e63a490ac
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ccfd2816bf81035b893ea8a7ddf30adebd325840
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796372"
---
# <a name="issigned-method-sqlserverparametermetadata"></a>isSigned メソッド (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターの値が符号付き数値かどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isSigned(int param)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *param*  
  
 パラメーターのインデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 指定されたパラメーターが符号付き数値である場合は、**true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この isSigned メソッドは、java.sql.ParameterMetaData インターフェイスで isSigned メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerParameterMetaData のメソッド](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData のメンバー](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData クラス](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
