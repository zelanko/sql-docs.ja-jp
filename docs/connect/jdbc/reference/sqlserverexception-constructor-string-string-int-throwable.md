---
title: "SQLServerException のコンス トラクター (java.lang.String、java.lang.String、int、java.lang.Throwable) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2018
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
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 98606e1dfa903c49ecd1152e49ca7d16406b167a
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="sqlserverexception-constructor-javalangstring-javalangstring-int-javalangthrowable"></a>SQLServerException のコンス トラクター (java.lang.String、java.lang.String、int、java.lang.Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  新しいインスタンスを初期化、 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)クラスの指定した場合、**文字列**オブジェクト、**文字列**オブジェクト、 **int**、および、 **スロー対象**オブジェクト。

## <a name="syntax"></a>構文  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState errState,
            int errNum,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>パラメーター  
 *errText*  
  
 エラー テキストを含む文字列。
  
 *errState*  
  
 エラーの状態を含む文字列。
 
 *errNum*  
  
 例外のエラー コードを含む int です。
 
 *cause*  
  
 例外の原因を含むスロー対象オブジェクト。
  
## <a name="see-also"></a>参照  
 [SQLServerException のコンス トラクター](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException のメンバー](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException クラス](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
