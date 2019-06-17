---
title: getServerPreparedStatementDiscardThreshold メソッド (SQLServerConnection) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getServerPreparedStatementDiscardThreshold
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 22f7bf637d20b42a7dadd3397e84c826fa277a22
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66791920"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>getServerPreparedStatementDiscardThreshold メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 値を返します**serverPreparedStatementDiscardThreshold**接続プロパティです。 この設定は、数未処理準備操作 (sp_unprepare) は、サーバー上で未処理のハンドルをクリーンアップする呼び出しが実行される前に 1 接続あたりの未処理できますステートメントの破棄を制御します。 設定の場合 < = 1、unprepare 準備のステートメントを閉じる操作が直ちに実行されます。 > 1 に設定されている場合の頻度が高すぎる sp_unprepare の呼び出しのオーバーヘッドを回避するためにこれらの呼び出しはまとめてバッチします。 このオプションの既定値は、呼び出し元 getDefaultServerPreparedStatementDiscardThreshold() で変更できます。

## <a name="syntax"></a>構文  
  
```  
  
public int getServerPreparedStatementDiscardThreshold()  
```  

## <a name="return-value"></a>戻り値
 **Int**の値を格納している**serverPreparedStatementDiscardThreshold**接続プロパティです。

## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 このメソッドは、JDBC driver 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
