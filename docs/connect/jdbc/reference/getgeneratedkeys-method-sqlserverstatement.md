---
title: getGeneratedKeys メソッド (SQLServerStatement) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getGeneratedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a3325950-0e81-4ae8-aa0c-e1f6d371adcd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e81fe589ed70f4d3f230713290f1d7f9b338ea67
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66774652"
---
# <a name="getgeneratedkeys-method-sqlserverstatement"></a>getGeneratedKeys メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトを実行した結果作成される自動生成キーを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.sql.ResultSet getGeneratedKeys()  
```  
  
## <a name="return-value"></a>戻り値  
 結果セット オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getGeneratedKeys メソッドは、java.sql.Statement インターフェイスの getGeneratedKeys メソッドによって指定されます。  
  
 このメソッドを使用する方法の詳細については、次を参照してください。[を使用して自動生成キー](../../../connect/jdbc/using-auto-generated-keys.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
