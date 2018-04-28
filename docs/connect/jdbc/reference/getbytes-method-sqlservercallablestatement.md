---
title: getBytes メソッド (SQLServerCallableStatement) |Microsoft ドキュメント
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
- SQLServerCallableStatement.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6e88cea-54b3-4d18-a9af-db54abf19f45
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 61f2c6c2ee2c5865d999e0b599568522fa7cd9bf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getbytes-method-sqlservercallablestatement"></a>getBytes メソッド (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターの値を byte 配列として取得します。  
  
## <a name="overload-list"></a>オーバーロードの一覧  
  
|名前|Description|  
|----------|-----------------|  
|[getBytes (int)](../../../connect/jdbc/reference/getbytes-method-int.md)|パラメーターに渡されたインデックスを使用して、指定されたパラメーターの値を byte 配列として取得します。|  
|[getBytes (java.lang.String)](../../../connect/jdbc/reference/getbytes-method-java-lang-string.md)|パラメーターに渡された名前を使用して、指定されたパラメーターの値を byte 配列として取得します。|  
  
## <a name="remarks"></a>解説  
 以前のバージョンので、 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]、SQLServerCallableStatement.getBytes を使用してバイト配列間の変換と[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データ型**日付**、**時間**、 **datetime2**、または**datetimeoffset**です。 新しいバージョンでは、これらのデータ型に対してこのメソッドを使用すると、変換がサポートされていないことを示す例外が発生します。  
  
## <a name="see-also"></a>参照  
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
