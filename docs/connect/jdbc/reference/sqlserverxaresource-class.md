---
title: "SQLServerXAResource クラス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4c5e0cb02544e0ea96c29758f7c50179de48cf7a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverxaresource-class"></a>SQLServerXAResource クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  XA の XAResource を表しますは分散トランザクション管理です。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** java.lang.Object  
  
 **実装:** javax.transaction.xa.XAResource  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerXAResource  
```  
  
## <a name="remarks"></a>解説  
 XA トランザクションがで実装された[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]を使用して[!INCLUDE[msCoName](../../../includes/msconame_md.md)]分散トランザクション マネージャー (DTC)。 SQLServerXAResource クラスへの呼び出しを使用する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]インターフェイス DTC になる sqljdbc_xa.dll という名前の dll を拡張します。 XA 呼び出し (XA_START、XA_END、XA_PREPARE など) の SQLServerXAResource で受信したが、対応する DTC 関数呼び出しにマップされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAResource のメンバー](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [JDBC ドライバー API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

