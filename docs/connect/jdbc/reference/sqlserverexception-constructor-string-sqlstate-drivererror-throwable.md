---
title: SQLServerException コンストラクター (java.lang.String、SQLState、DriverError、java.lang.Throwable) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 13b0e3aea694b0cedb3594cb76650ca7c938eb55
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67971092"
---
# <a name="sqlserverexception-constructor-javalangstring-sqlstate-drivererror-javalangthrowable"></a>SQLServerException コンストラクター (java.lang.String、SQLState、DriverError、java.lang.Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  **string** オブジェクト、**sqlstate** オブジェクト、**drivererror** オブジェクト、および **throwable** オブジェクトが渡されたときに、[SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) クラスの新しいインスタンスが初期化されます。

## <a name="syntax"></a>構文  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState sqlState,
            DriverError driverError,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>パラメーター  
 *errText*  
  
 エラー テキストを保持する文字列。
  
 *sqlState*  
  
 SQL 状態を保持する列挙型オブジェクト。
 
 *driverError*  
  
 ドライバー エラーを保持する列挙型オブジェクト。
 
 *cause*  
  
 例外の原因を保持する throwable オブジェクト。
  
## <a name="see-also"></a>参照  
 [SQLServerException のコンストラクター](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException のメンバー](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException クラス](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
