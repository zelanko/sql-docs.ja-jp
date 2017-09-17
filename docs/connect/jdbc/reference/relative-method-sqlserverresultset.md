---
title: "relative メソッド (SQLServerResultSet) |Microsoft ドキュメント"
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
- SQLServerResultSet.relative
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2bcdbb69-95fd-4ae8-8488-1a75a91fe2e0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 36db05ec89818195c4b710591f1d0db71e091fe0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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
  
  
