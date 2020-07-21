---
title: moveToInsertRow メソッド (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.moveToInsertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f3c54bfe-d5b7-4f6e-ae6c-3e8954e5b1c9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 285bbb91734132f1ca74d739ec2a63394ace5108
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80914798"
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
  
 カーソルが挿入行にあるときに呼び出すことができるメソッドは、updater、getter、および [insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md) だけです。 このメソッドを呼び出すたびに、insertRow を呼び出す前に、結果セット内のすべての列に値を指定する必要があります。 列の値で getter メソッドを呼び出す前に、updater メソッドを呼び出す必要があります。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
