---
title: SQLServerException コンストラクター (java.lang.Object, java.lang.String, java.lang.String, int, boolean) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fc2706f903178404f775b559cfb5f5cff00125d3
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80902748"
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-int-boolean"></a>SQLServerException コンストラクター (java.lang.Object, java.lang.String, java.lang.String, int, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [object](../../../connect/jdbc/reference/sqlserverexception-class.md)、**string** オブジェクト、**string** オブジェクト、**int**、および **boolean** が渡されたときに、**SQLServerException** クラスの新しいインスタンスが初期化されます。

## <a name="syntax"></a>構文  
  
```  

public SQLServerException(java.lang.Object obj,
            java.lang.String errText,
            java.lang.String errState,
            int errNum,
            boolean bStack)

            
```  
  
#### <a name="parameters"></a>パラメーター  
 *obj*  
  
 例外を生成した IO バッファー。

 *errText*  
  
 エラー テキストを含む文字列。
  
 *sqlState*  
  
 SQL 状態を含む列挙型オブジェクト。
 
 *errNum*  
  
 例外のエラー コードを含む整数。
 
 *bStack*  
  
 スタック トレースの生成が必要かどうかを示すブール値。
  
## <a name="see-also"></a>参照  
 [SQLServerException のコンストラクター](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException のメンバー](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException クラス](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
