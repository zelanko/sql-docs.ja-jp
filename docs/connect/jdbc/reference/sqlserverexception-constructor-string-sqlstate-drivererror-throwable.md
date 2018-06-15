---
title: SQLServerException コンス トラクター (java.lang.String, SQLState、DriverError、java.lang.Throwable) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33f7b15a2f4dd8e83c7e703e96812f29691e6bd6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32846197"
---
# <a name="sqlserverexception-constructor-javalangstring-sqlstate-drivererror-javalangthrowable"></a>SQLServerException コンス トラクター (java.lang.String, SQLState、DriverError、java.lang.Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  新しいインスタンスを初期化、 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)クラスの指定した場合、**文字列**オブジェクト、 **sqlstate**オブジェクト、 **drivererror**オブジェクト、および**スロー対象**オブジェクト。

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
  
 SQL 状態を保持している列挙オブジェクト。
 
 *driverError*  
  
 ドライバー エラーがある列挙オブジェクト。
 
 *cause*  
  
 例外の原因を保持するスロー対象オブジェクト。
  
## <a name="see-also"></a>参照  
 [SQLServerException のコンス トラクター](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException のメンバー](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException クラス](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
