---
title: "setResponseBuffering メソッド (SQLServerStatement) |Microsoft ドキュメント"
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
apiname:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: 9f489835-6cda-4c8c-b139-079639a169cf
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c5af0e179ea15fc4d5a30604b606f5ff45c79a1b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setresponsebuffering-method-sqlserverstatement"></a>setResponseBuffering メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  応答のバッファリング モードを設定[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト大文字と小文字を**文字列完全**または**アダプティブ**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *value*  
  
 A**文字列**応答バッファリング モードを格納しています。 有効なモードには、以下の文字列のいずれかを指定できます:**完全**または**アダプティブ**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 **アダプティブ**必要な場合に、最小の可能なデータをバッファー処理を指定します。  
  
 **完全**実行時に、サーバーから結果全体を読み取ることを示します。  
  
 アダプティブは、JDBC Driver version 2.0 および 3.0 での既定値です。 JDBC Driver version 2.0 よりも前の既定値を完全にしました。  
  
 [SetResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)メソッドをオーバーライドできるように、 **responseBuffering**接続**文字列**現在のプロパティ[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。 応答バッファリング モードの使用に関する詳細については、次を参照してください。[アダプティブ バッファリングを使用して](../../../connect/jdbc/using-adaptive-buffering.md)です。  
  
 アプリケーションに無効なパラメーター値を指定する場合、 [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) 、メソッド、 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)がスローされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)   
 [アダプティブ バッファリングの使用](../../../connect/jdbc/using-adaptive-buffering.md)  
  
  

