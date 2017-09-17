---
title: "cancel メソッド (SQLServerStatement) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerStatement.cancel
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 276bd9c1-9329-4fc9-9622-ed673c83a12d
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b906ee23d28e42ff105d5d9bb919453193d90f68
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="cancel-method-sqlserverstatement"></a>cancel メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これによって現在実行されている SQL ステートメントを取り消します[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void cancel()  
```  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この cancel メソッドは、java.sql.Statement インターフェイスのキャンセル メソッドによって指定されます。  
  
 順方向専用、読み取り専用の大きな結果セットを 1 つだけ生成するようなステートメントを実行する場合、必要な行は、返された結果セットのうち、先頭のいくつかの行だけであるケースが少なくありません。 この場合、アプリケーションが呼び出す可能性があります、[キャンセル](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)残りの不要な行を破棄するために必要な処理時間を最小限に抑えるために、結果を閉じる前に、関連するステートメント オブジェクトのメソッドを設定します。 この手法を用いるかどうかは、短縮できる処理時間と、実行の取り消しに伴って生じる、サーバーに対するラウンド トリップ時間とのトレードオフを考慮したうえで判断することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
