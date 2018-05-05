---
title: finalize メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
- SQLServerResultSet.finalize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49bc879d-822b-42da-bc20-2394865f1f0f
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 56c7131bfc0b5f1bb293b7a697f090495f0938f1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="finalize-method-sqlserverresultset"></a>finalize メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これを明示的に閉じる[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void finalize()  
```  
  
## <a name="remarks"></a>解説  
 アプリケーションが閉じていない場合は、結果セットを閉じます。 このメソッドは JDBC 仕様に準拠するためにだけ存在します。 Java 仮想マシン (JVM) ではファイナライザーがいつ実行されるかが保証されないため、明示的に結果セットを閉じてないアプリケーションは、別のステートメント (同じ接続を使用し、行ロックなどの共通のサーバー リソースでブロックされているステートメント) でもデッドロックする可能性があります。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
