---
title: updateLong (java.lang.String, long) メソッド |Microsoft ドキュメント
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
- SQLServerResultSet.updateLong (java.lang.String, long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6003706-35de-42b1-8f23-899a388adb5b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43aa49344c78cea040ce068a412dddfd440ab70b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32849007"
---
# <a name="updatelong-method-javalangstring-long"></a>updateLong (java.lang.String, long) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列の更新、**長い**列の名前を指定された値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateLong(java.lang.String columnName,  
                       long x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 A**文字列**列の名前を格納しています。  
  
 *x*  
  
 A**長い**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateLong メソッドは、java.sql.ResultSet インターフェイスの updateLong メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [updateLong メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatelong-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
