---
title: "setCatalog メソッド (SQLServerConnection) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerConnection.setCatalog
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 553c0603-c07d-436a-86eb-3ba6b51bd696
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 44420fcaa6ecc0ab97dcb44344688b0cf92c9645
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setcatalog-method-sqlserverconnection"></a>setCatalog メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このサブ空間を選択する特定のカタログ名を設定[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトのデータベースの作業を行う。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setCatalog(java.lang.String catalog)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *カタログ*  
  
 A**文字列**カタログ名を格納しています。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setCatalog メソッドは、java.sql.Connection インターフェイスの setCatalog メソッドによって指定されます。  
  
 *カタログ*引数はエスケープ、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]自動的にします。 このメソッドを使用して、接続オブジェクトのカタログのプロパティを設定します。 このプロパティは、他の方法で暗黙的に設定されることはありません。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
