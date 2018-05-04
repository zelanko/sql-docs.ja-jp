---
title: close メソッド (SQLServerResultSet) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8f3adf5b-874e-4cf2-b4ef-672dda42d77a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: deea90b13bb4bb99c504f5eaa344babdf4a1c680
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="close-method-sqlserverresultset"></a>close メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このリリース[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトのデータベースと JDBC リソースを待たずにすぐに自動的に閉じられているときにします。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 このメソッドは、java.sql.ResultSet インターフェイスの close メソッドによって指定されます。  
  
 SQLServerResultSet オブジェクトがによって自動的に閉じられる、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)それを生成した SQLServerStatement オブジェクトが閉じられている、再実行するために使用のいずれかの取得時に次の結果複数の結果のシーケンスからオブジェクト. SQLServerResultSet オブジェクトはガベージ コレクションである場合にも自動的に閉じられます。  
  
 順方向専用、読み取り専用の大きな結果セットを 1 つだけ生成するようなステートメントを実行する場合、必要な行は、返された結果セットのうち、先頭のいくつかの行だけであるケースが少なくありません。 この場合、アプリケーションが呼び出す可能性があります、[キャンセル](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)残りの不要な行を破棄するために必要な処理時間を最小限に抑えるために、結果を閉じる前に、関連するステートメント オブジェクトのメソッドを設定します。 この手法を用いるかどうかは、短縮できる処理時間と、実行の取り消しに伴って生じる、サーバーに対するラウンド トリップ時間とのトレードオフを考慮したうえで判断することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
