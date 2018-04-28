---
title: getResponseBuffering メソッド (SQLServerDataSource) |Microsoft ドキュメント
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
- SQLServerDataSource.getResponseBuffering()
apilocation:
- SQLServerDataSource.getResponseBuffering()
apitype: Assembly
ms.assetid: 19585a93-88a4-415e-a20e-12ba58cddeaa
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0a3748460c093186c0fde4c96d50d66998505a64
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getresponsebuffering-method-sqlserverdatasource"></a>getResponseBuffering メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このモードをバッファリング応答を返します[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**小文字を格納している**完全**または**アダプティブ**です。  
  
## <a name="remarks"></a>解説  
 **完全**値実行時に、サーバーから結果全体を読み取ることを示します。  
  
 **アダプティブ**値は、必要な場合に、最小の可能なデータをバッファー処理を指定します。 **アダプティブ**値は既定のバッファリング モードです。  
  
 応答バッファリング モードの使用に関する詳細については、次を参照してください。[アダプティブ バッファリングを使用して](../../../connect/jdbc/using-adaptive-buffering.md)です。  
  
## <a name="see-also"></a>参照  
 [setResponseBuffering メソッド&#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)   
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
