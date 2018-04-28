---
title: ownUpdatesAreVisible メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
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
apiname:
- SQLServerDatabaseMetaData.ownUpdatesAreVisible
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eacbb1a8-ac9a-4f44-832e-ae0af476522e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bea017f0af48d0cdc1c3a2e7b39e20f8d0178b9b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ownupdatesarevisible-method-sqlserverdatabasemetadata"></a>ownUpdatesAreVisible メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  結果セット自体の更新が可視であるかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean othersUpdatesAreVisible(int type)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *type*  
  
 結果セットの種類を示す整数です。java.sql.ResultSet または SQLServerResultSet での定義に従って、次のいずれかの値を指定します。  
  
## <a name="javasqlresultset-types"></a>java.sql.ResultSet の種類  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>SQLServerResultSet の種類  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
## <a name="return-value"></a>戻り値  
 **true**場合は、更新プログラムが表示されます。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この ownUpdatesAreVisible メソッドは、java.sql.DatabaseMetaData インターフェイスの ownUpdatesAreVisible メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
