---
title: SQLServerException コンス トラクター (java.lang.Object, java.lang.String, java.lang.String, StreamError, boolean) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 89d156ca5024ed49cbc3b5256266c393c897ae12
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47756390"
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-streamerror-boolean"></a>SQLServerException コンストラクター (java.lang.Object, java.lang.String, java.lang.String, StreamError, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  新しいインスタンスを初期化、 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)クラスが指定されると、**オブジェクト**、**文字列**オブジェクト、**文字列**オブジェクト、 **StreamError**オブジェクト、および**ブール**します。

## <a name="syntax"></a>構文  
  
```  

public SQLServerException(java.lang.Object obj,
            java.lang.String errText,
            java.lang.String errState,
            StreamError streamError,
            boolean bStack)

            
```  
  
#### <a name="parameters"></a>パラメーター  
 *obj*  
  
 例外を生成した IO のバッファー。

 *errText*  
  
 エラー テキストを含む文字列。
  
 *sqlState*  
  
 SQL の状態を含む列挙オブジェクト。
 
 *streamError*  
  
 エラーの詳細を含む StreamError オブジェクト。
 
 *bStack*  
  
 スタック トレースを生成するかどうかを示すブール値。
  
## <a name="see-also"></a>参照  
 [SQLServerException のコンストラクター](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException のメンバー](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException クラス](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
