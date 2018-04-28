---
title: relative メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
- SQLServerResultSet.relative
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2bcdbb69-95fd-4ae8-8488-1a75a91fe2e0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d210c40ac0c288ef57e74f37218515e21148fdb3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="relative-method-sqlserverresultset"></a>relative メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  カーソルを指定された行数分、現在の行を基準に正または負の方向に移動します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean relative(int nRows)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *nRows*  
  
 **Int**を移動する行の数を示すです。  
  
## <a name="return-value"></a>戻り値  
 **true**カーソルの行がある場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この相対メソッドは、java.sql.ResultSet インターフェイスの相対的なメソッドによって指定されます。  
  
 結果セット内の先頭行または最終行を越えて移動しようとすると、先頭行の前または最終行の後にカーソルが配置されます。 呼び出す`relative(0)`が有効では、カーソルの位置を変更しません。  
  
 メソッドを呼び出す`relative(1)`を呼び出すことと同じ、[次](../../../connect/jdbc/reference/next-method-sqlserverresultset.md)メソッドです。 メソッドを呼び出す`relative(-1)`を呼び出すことと同じ、[以前](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md)メソッドです。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
