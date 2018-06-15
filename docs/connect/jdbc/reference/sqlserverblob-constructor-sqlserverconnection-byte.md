---
title: SQLServerBlob コンス トラクター (SQLServerConnection, byte) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection, byte[].SQLServerBlob
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9fe573e3-30db-4828-abab-e9346493e931
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d93e5bee03976c5ae9c55247f98ba180e237a4e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32847037"
---
# <a name="sqlserverblob-constructor-sqlserverconnection-byte"></a>SQLServerBlob コンス トラクター (SQLServerConnection, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  新しいインスタンスを初期化、 [SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)クラスの指定した場合、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトおよび**バイト**配列。  
  
> [!NOTE]  
>  このメソッドは、JDBC Driver Version 2.0 では非推奨とされました。 代わりに、使用、 [createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public SQLServerBlob(SQLServerConnection connection,  
                     byte[] data)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *接続*  
  
 SQLServerConnection オブジェクト。  
  
 *data*  
  
 A**バイト**配列。  
  
## <a name="see-also"></a>参照  
 [SQLServerBlob コンス トラクター](../../../connect/jdbc/reference/sqlserverblob-constructors.md)   
 [SQLServerBlob のメンバー](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob クラス](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
