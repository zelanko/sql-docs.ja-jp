---
title: getXAConnection メソッド (java.lang.String, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXADataSource.getXAConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 276e0093-3d42-4f73-acc4-2b5b98245b40
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: db13bdb3a1039abf1b07616d4cd94001833e3600
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801706"
---
# <a name="getxaconnection-method-javalangstring-javalangstring"></a>getXAConnection (java.lang.String, java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたユーザー名とパスワードを使用して、物理データベース接続の確立を試みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public javax.sql.XAConnection getXAConnection(java.lang.String user,  
                                              java.lang.String password)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *user*  
  
 ユーザー名を含む**文字列**です。  
  
 *password*  
  
 パスワードを含む**文字列**です。  
  
## <a name="return-value"></a>戻り値  
 XAConnection オブジェクト。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 この getXAConnection メソッドは、javax.sql.XADataSource インターフェイスで getXAConnection メソッドによって指定されます。  
  
> [!NOTE]  
>  このメソッドは、通常 XA 接続プール実装によって呼び出され、標準の JDBC アプリケーション コードからは呼び出されません。  
  
## <a name="see-also"></a>参照  
 [getXAConnection メソッド &#40;SQLServerXADataSource&#41;](../../../connect/jdbc/reference/getxaconnection-method-sqlserverxadatasource.md)   
 [SQLServerXADataSource のメソッド](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [SQLServerXADataSource のメンバー](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [SQLServerXADataSource クラス](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
