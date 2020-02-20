---
title: registerOutParameter メソッド to type | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d00242c-4d9c-42cc-86bb-b76f5ef876b8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cdd197be6327b84a6c299239f1198fe005dff0f0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67975901"
---
# <a name="registeroutparameter-method-javalangstring-int"></a>registerOutParameter (java.lang.String, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された名前の OUT パラメーターを、渡された JDBC 型に登録します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *s*  
  
 パラメーターの名前を含む**文字列**です。  
  
 *n*  
  
 java.sql.Types で定義されている JDBC 型コード。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この registerOutParameter メソッドは、java.sql.CallableStatement インターフェイスの registerOutParameter メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [registerOutParameter メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
