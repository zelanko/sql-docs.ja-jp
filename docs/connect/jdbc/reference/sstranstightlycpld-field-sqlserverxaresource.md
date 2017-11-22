---
title: "SSTRANSTIGHTLYCPLD フィールド (SQLServerXAResource) |Microsoft ドキュメント"
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
apiname: SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apilocation: SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apitype: Assembly
ms.assetid: 379857c3-9de1-4964-8782-32df317cbfbb
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 88a6ea09e8809ac028b45e2bd0fd2035b095430b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="sstranstightlycpld-field-sqlserverxaresource"></a>SSTRANSTIGHTLYCPLD フィールド (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  XA ブランチ トランザクション ID (XID) は異なるが、グローバル トランザクション ID (GTRID) が同じである、密に結合された XA トランザクションを許可するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## <a name="field-value"></a>フィールド値  
 **Int** 32768 の値。  
  
## <a name="remarks"></a>解説  
 各トランザクションは、XA ブランチ トランザクション ID (XID) およびグローバル トランザクション ID (GTRID) によって識別されます。 異なる Xid できますが、同じ GTRID 密に結合された XA トランザクションを使用するアプリケーションを許可するために設定する必要があります、 [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) XAResource.start メソッドのパラメーターのフラグ。 このフラグを使用する方法の詳細については、次を参照してください。 [XA トランザクションについて](../../../connect/jdbc/understanding-xa-transactions.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAResource のフィールド](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [SQLServerXAResource のメンバー](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource クラス](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
