---
title: recover メソッド (SQLServerXAResource) |Microsoft ドキュメント
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
- SQLServerXAResource.recover
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 840ecfcf-0dd3-4b7b-976f-dc9a96cd1464
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ae101421d8ea82742a631b9f8908aa075a99920
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="recover-method-sqlserverxaresource"></a>recover メソッド (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  準備されたトランザクション ブランチの一覧を、リソース マネージャーから取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public javax.transaction.xa.Xid[] recover(int flags)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *flags*  
  
 **Int**値は次のいずれかを実行値: XAResource.TMSTARTRSCAN または XAResource.TMENDRSCAN または XAResource.TMNOFLAGS XAResource.TMSTARTTRSCAN |XAResource.TMENDRSCAN です。  
  
## <a name="return-value"></a>戻り値  
 Xid オブジェクト。  
  
## <a name="exceptions"></a>例外  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>解説  
 この回復方法は、回復、javax.transaction.xa.XAResource インターフェイスのメソッドでによって指定されます。  
  
 場合、パラメーター**フラグ**XAResource.TMSTARTRSCAN または XAResource.TMSTARTRSCAN ではありません |XAResource.TMENDRSCAN、リカバリ スキャンが進行中でなければなりません。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAResource のメソッド](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource のメンバー](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource クラス](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
