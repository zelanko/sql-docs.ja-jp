---
title: getResponseBuffering メソッド (SQLServerStatement) |Microsoft ドキュメント
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
- SQLServerStatement.getResponseBuffering()
apilocation:
- SQLServerStatement.getResponseBuffering()
apitype: Assembly
ms.assetid: a9a9ffdd-7ce3-4e0a-907c-34d6a54e6865
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d0946f0aba47904f8ceb0f02d84a741504fafc7e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getresponsebuffering-method-sqlserverstatement"></a>getResponseBuffering メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  応答のバッファリング モードを取得[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**小文字を格納している**完全**または**アダプティブ**です。  
  
## <a name="remarks"></a>解説  
 **アダプティブ**必要な場合に、最小の可能なデータをバッファー処理を指定します。  
  
 **完全**実行時に、サーバーから結果全体を読み取ることを示します。  
  
 **アダプティブ**JDBC Driver version 2.0 および 3.0 での既定値です。 **完全**が JDBC Driver version 2.0 よりも前の既定値です。  
  
 応答バッファリング モードの使用に関する詳細については、次を参照してください。[アダプティブ バッファリングを使用して](../../../connect/jdbc/using-adaptive-buffering.md)です。  
  
## <a name="see-also"></a>参照  
 [setResponseBuffering メソッド&#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
