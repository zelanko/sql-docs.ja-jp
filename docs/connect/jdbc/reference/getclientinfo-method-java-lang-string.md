---
title: getClientInfo (java.lang.String) メソッド |Microsoft ドキュメント
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
ms.assetid: e8e632c4-d6cc-4c5e-b6ad-873579343b19
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9bac4333e779c2a9db9b201c3df3e2846b7c40ef
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getclientinfo-method-javalangstring"></a>getClientInfo (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたクライアント情報のプロパティの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getClientInfo (java.lang.String name)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *name*  
  
 取得するクライアント情報のプロパティの名前を表す文字列。  
  
## <a name="return-value"></a>戻り値  
 クライアント情報のプロパティの値を含む文字列です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getClientInfo メソッドは、java.sql.Connection インターフェイスの getClientInfo メソッドによって指定されます。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]クライアント情報のプロパティをサポートしていません。 その結果、このメソッドが戻る**null**です。  
  
 同様に、アプリケーションを使用して、 [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md)のメソッド、 [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)ドライバーがサポートするクライアント情報のプロパティの一覧を取得するクラス。 [GetClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md)メソッドが空の結果セットを返します。  
  
## <a name="see-also"></a>参照  
 [getClientInfo メソッド&#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
