---
title: getQueryTimeout メソッド (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getQueryTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8dff954f-b458-4fa6-abe6-be62ff75e2b9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 03f1833cff6bb65551c4a9c02dd72cb758a555c4
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925174"
---
# <a name="getquerytimeout-method-sqlserverstatement"></a>getQueryTimeout メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] が [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトの実行を待つ秒数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final int getQueryTimeout()  
```  
  
## <a name="return-value"></a>戻り値  
 JDBC ドライバーが待つ秒数を示す **int** です。制限しない場合は 0 です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getQueryTimeout メソッドは、java.sql.Statement インターフェイスの getQueryTimeout メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
