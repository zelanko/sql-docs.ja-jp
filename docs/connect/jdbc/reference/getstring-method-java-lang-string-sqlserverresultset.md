---
title: getString (java.lang.String) メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
- SQLServerResultSet.getString (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8a98c8a8-61d0-40c9-9335-25a87b732dc3
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f615ce3f4f9fcd883ccb9f8ebc380c5e71e1a4eb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32838447"
---
# <a name="getstring-method-javalangstring-sqlserverresultset"></a>getString (java.lang.String) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列名の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、**文字列**java プログラミング言語です。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getString(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 A**文字列**列の名前を格納しています。  
  
## <a name="return-value"></a>戻り値  
 A**文字列**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getString メソッドは、java.sql.ResultSet インターフェイスの getString メソッドによって指定されます。  
  
 SQL Server 内のすべての列を、文字列として返すことができます。 つまり、**文字列**すべての数値ベースし、文字ベースの型の表現および binary、varbinary、varbinary (max)、イメージ、timestamp、uniqueidentifier などのバイナリ列の 16 進数文字列形式を指定できます返されます。  
  
 money、smallmoney、datetime、smalldatetime、float、real、decimal、numeric などの地域依存の型は、その型の基になる値に対する標準の toString() 形式を返します。  
  
 ユーザー定義型は 16 進数として返されます**文字列**値。  
  
## <a name="see-also"></a>参照  
 [getString メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
