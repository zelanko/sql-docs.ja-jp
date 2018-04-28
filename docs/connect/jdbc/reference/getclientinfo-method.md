---
title: getClientInfo メソッド () |Microsoft ドキュメント
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
ms.assetid: b06a5ced-b760-4c78-b17e-854ce95a1a5c
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 25637769596d157d9d6067746e16a9c748c6f109
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getclientinfo-method-"></a>getClientInfo () メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  JDBC ドライバーでサポートされている、各クライアント情報のプロパティの名前と現在の値を含む一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.util.Properties getClientInfo()  
```  
  
## <a name="return-value"></a>戻り値  
 各ドライバーでサポートされるクライアント情報プロパティの現在の値と名前を格納するプロパティ オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getClientInfo メソッドは、java.sql.Connection インターフェイスの getClientInfo メソッドによって指定されます。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]クライアント情報のプロパティをサポートしていません。 その結果、このメソッドは、空のプロパティ オブジェクトを返します。  
  
 同様に、アプリケーションを使用して、 [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md)のメソッド、 [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)ドライバーがサポートするクライアント情報のプロパティの一覧を取得するクラス。 [GetClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md)メソッドが空の結果セットを返します。  
  
## <a name="see-also"></a>参照  
 [getClientInfo メソッド&#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
