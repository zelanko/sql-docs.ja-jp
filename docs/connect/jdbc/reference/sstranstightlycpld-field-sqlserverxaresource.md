---
title: SSTRANSTIGHTLYCPLD フィールド (SQLServerXAResource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apilocation:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apitype: Assembly
ms.assetid: 379857c3-9de1-4964-8782-32df317cbfbb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8129cf30a7ba95c39281c9ff4bd2a5c0eac4183c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818420"
---
# <a name="sstranstightlycpld-field-sqlserverxaresource"></a>SSTRANSTIGHTLYCPLD フィールド (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  XA ブランチ トランザクション ID (XID) は異なるが、グローバル トランザクション ID (GTRID) が同じである、密に結合された XA トランザクションを許可するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## <a name="field-value"></a>フィールド値  
 **Int**値 32768 です。  
  
## <a name="remarks"></a>Remarks  
 各トランザクションは、XA ブランチ トランザクション ID (XID) およびグローバル トランザクション ID (GTRID) によって識別されます。 XID は異なるが GTRID が同じである、密に結合された XA トランザクションをアプリケーションで使用できるようにするには、XAResource.start メソッドの flags パラメーターに [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) を設定する必要があります。 このフラグを使用する方法の詳細については、次を参照してください。 [XA トランザクションの概要](../../../connect/jdbc/understanding-xa-transactions.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAResource のフィールド](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [SQLServerXAResource のメンバー](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource クラス](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
