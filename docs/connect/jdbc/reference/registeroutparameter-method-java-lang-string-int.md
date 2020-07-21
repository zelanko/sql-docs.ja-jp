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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4b081cef7e687ce54a7e3be4b2e8b3b4a7e1eb8a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80904158"
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
  
  
