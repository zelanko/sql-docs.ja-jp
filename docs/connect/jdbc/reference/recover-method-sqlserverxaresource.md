---
title: recover メソッド (SQLServerXAResource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.recover
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 840ecfcf-0dd3-4b7b-976f-dc9a96cd1464
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b78165b8c199a04d716d18614e6fb56232eca429
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923121"
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
  
 次の値のいずれかを受け取る可能性がある **int** 値。XAResource.TMSTARTRSCAN または XAResource.TMENDRSCAN または XAResource.TMNOFLAGS または XAResource.TMSTARTTRSCAN | XAResource.TMENDRSCAN。  
  
## <a name="return-value"></a>戻り値  
 Xid オブジェクト。  
  
## <a name="exceptions"></a>例外  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>解説  
 この recover メソッドは、javax.transaction.xa.XAResource インターフェイスの recover メソッドで規定されています。  
  
 パラメーター **flag** が XAResource.TMSTARTRSCAN または XAResource.TMSTARTRSCAN | XAResource.TMENDRSCAN ではない場合、回復スキャンは進行中です。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAResource のメソッド](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource のメンバー](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource クラス](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
