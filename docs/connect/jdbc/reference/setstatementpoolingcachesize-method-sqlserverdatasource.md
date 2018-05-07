---
title: setStatementPoolingCacheSize メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8821174afbe7189eb445ac6722f0665b75eb991e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="setstatementpoolingcachesize-method-sqlserverdatasource"></a>setStatementPoolingCacheSize メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この接続の準備されたステートメント キャッシュのサイズを設定します。 DisableStatementPooling が false と値 > 0 に設定されている場合は動作します。
  
## <a name="syntax"></a>構文  
  
```

public void setStatementPoolingCacheSize(boolean statementPoolingCacheSize);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *statementPoolingCacheSize*  
  
 新しい値、 **statementPoolingCacheSize**接続プロパティです。  

## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>解説  
 このメソッドは、JDBC ドライバーのバージョン 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
