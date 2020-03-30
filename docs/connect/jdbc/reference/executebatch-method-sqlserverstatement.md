---
title: executeBatch メソッド (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeBatch
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fb034f63-2532-4da8-a1b0-bc125734585a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1d05b367901aae7a37e10b0a2091a268c3a78a7b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67954836"
---
# <a name="executebatch-method-sqlserverstatement"></a>executeBatch メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  実行するコマンド バッチをデータベースに送信します。 すべてのコマンドが正常に実行されている場合は、更新数の配列が返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int[] executeBatch()  
```  
  
## <a name="return-value"></a>戻り値  
 更新数を含む **int** の配列です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
 java.sql.BatchUpdateException  
  
## <a name="remarks"></a>解説  
 この executeBatch メソッドは、java.sql.Statement インターフェイスの executeBatch メソッドで規定されています。  
  
 コマンドをデータベースに送信した後、このメソッドはバッチ内のすべてのコマンドをクリアします。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
