---
title: getBoolean (int) メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
- SQLServerResultSet.getBoolean (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 50fcc0c3-36a1-47b2-b18c-7aa2ac9b27d3
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c574cd8ec1e49f6c049775cf1a35f7d63fce7a84
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getboolean-method-int-sqlserverresultset"></a>getBoolean (int) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列インデックスの値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、**ブール**Java プログラミング言語でします。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getBoolean(int columnIndex)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 **Int**列インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 A**ブール**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getBoolean メソッドは、java.sql.ResultSet インターフェイスの getBoolean メソッドによって指定されます。  
  
 このメソッドは、数値データ型および文字データ型のみでサポートされます。 1、「1」の値に変換と"**true**"に**true**、および値「0」で 0、および"**false**"に**false**です。 他の値については、動作が定義されていません。  
  
## <a name="see-also"></a>参照  
 [getBoolean メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getboolean-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
