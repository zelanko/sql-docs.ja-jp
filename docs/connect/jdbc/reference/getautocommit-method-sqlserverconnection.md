---
title: getAutoCommit メソッド (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getAutoCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: af1f67f4-f568-4e58-abcc-5c809a89b547
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7d9e5545e0b7ed2953ba89b2351c09ae0fd3700a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920926"
---
# <a name="getautocommit-method-sqlserverconnection"></a>getAutoCommit メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) オブジェクトの現在の自動コミット モードを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getAutoCommit()  
```  
  
## <a name="return-value"></a>戻り値  
 自動コミット モードが有効な場合は **true**、有効でない場合は **false** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getAutoCommit メソッドは、java.sql.Connection インターフェイスの getAutoCommit メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
