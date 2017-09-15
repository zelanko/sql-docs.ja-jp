---
title: "updateBytes メソッド (SQLServerResultSet) |Microsoft ドキュメント"
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
- SQLServerResultSet.updateBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3050c836-fbb3-4475-99e5-05637a48a932
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e20e126945f11a2cba5d4b1171dc762f2a2efbac
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="updatebytes-method-sqlserverresultset"></a>updateBytes メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  配列で指定された列を更新**バイト**値。  
  
## <a name="overload-list"></a>オーバーロードの一覧  
  
|名前|Description|  
|----------|-----------------|  
|[updateBytes (int, バイト & #91、&#93;)](../../../connect/jdbc/reference/updatebytes-method-int-byte.md)|配列で指定された列を更新**バイト**列インデックスの値。|  
|[updateBytes (java.lang.String、バイト & #91、&#93;)](../../../connect/jdbc/reference/updatebytes-method-java-lang-string-byte.md)|配列で指定された列を更新**バイト**値列の名前を指定します。|  
  
## <a name="remarks"></a>解説  
 以前のバージョンで[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]、SQLServerResultSet.updateBytes を使用してバイト配列間の変換と[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データ型**日付**、**時間**、 **datetime2**、または**datetimeoffset**です。 新しいバージョンでは、これらのデータ型に対してこのメソッドを使用すると、変換がサポートされていないことを示す例外が発生します。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
