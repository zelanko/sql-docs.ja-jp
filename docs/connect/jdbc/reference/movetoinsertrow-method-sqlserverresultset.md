---
title: moveToInsertRow メソッド (SQLServerResultSet) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerResultSet.moveToInsertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f3c54bfe-d5b7-4f6e-ae6c-3e8954e5b1c9
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1f39608188e9de998c5f431561cf1482f5d50b3f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="movetoinsertrow-method-sqlserverresultset"></a>moveToInsertRow メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  カーソルを挿入行に移動します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void moveToInsertRow()  
```  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この moveToInsertRow メソッドは、java.sql.ResultSet インターフェイスの moveToInsertRow メソッドによって指定されます。  
  
 カーソルが挿入行に置かれている間、現在のカーソルの位置は記憶されています。 挿入行は、更新可能な結果セットに関連付けられている特殊な行です。 挿入行とは、本質的には、行を結果セットに追加する前に updater メソッドを呼び出すことによって新しい行を作成できるバッファーです。  
  
 Updater、getter、のみと[insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md)挿入行にカーソルがある場合、メソッドを呼び出すことができます。 結果セット内のすべての列は、このメソッドが呼び出されるたびに値を指定し、insertRow を呼び出す前にする必要があります。 列の値で getter メソッドを呼び出す前に、updater メソッドを呼び出す必要があります。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
