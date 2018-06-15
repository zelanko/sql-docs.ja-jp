---
title: SQLServerException のコンス トラクター (java.lang.Object, java.lang.String, java.lang.String, StreamError, boolean) |Microsoft ドキュメント
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
ms.openlocfilehash: f8c2f8664e7d97c7bc197b3053e515a6fb121ebd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845757"
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-streamerror-boolean"></a>SQLServerException のコンス トラクター (java.lang.Object, java.lang.String, java.lang.String, StreamError, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  新しいインスタンスを初期化、 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)クラスの指定した場合、**オブジェクト**、**文字列**オブジェクト、**文字列**オブジェクト、 **StreamError**オブジェクト、および**ブール**です。

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
  
 例外を生成した IO バッファー。

 *errText*  
  
 エラー テキストを含む文字列。
  
 *sqlState*  
  
 SQL の状態を含む列挙オブジェクト。
 
 *streamError*  
  
 エラーに関する詳細を含む StreamError オブジェクトです。
 
 *bStack*  
  
 スタック トレースを生成するかどうかを示すブール値。
  
## <a name="see-also"></a>参照  
 [SQLServerException のコンス トラクター](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException のメンバー](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException クラス](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
