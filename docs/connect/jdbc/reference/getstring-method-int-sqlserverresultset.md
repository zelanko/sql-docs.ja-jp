---
title: getString (int) メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
- SQLServerResultSet.getString (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bfa493c4-fe07-449b-b4d0-384e1a1fce48
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 51332e0e8d3b09723130585b770fff3d9d4b6e80
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32837827"
---
# <a name="getstring-method-int-sqlserverresultset"></a>getString (int) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列インデックスの値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、**文字列**java プログラミング言語です。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getString(int columnIndex)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 列インデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 A**文字列**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getString メソッドは、java.sql.ResultSet インターフェイスの getString メソッドによって指定されます。  
  
 すべての列[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]を文字列として返されることができます。 つまり、**文字列**すべての数値ベースし、文字ベースの型の表現および binary、varbinary、varbinary (max)、イメージ、timestamp、uniqueidentifier などのバイナリ列の 16 進数文字列形式を指定できます返されます。  
  
 Money、smallmoney、datetime、smalldatetime、float、real、decimal、および numeric などの場所に依存した型では、型の基になる値の標準の toString() 形式を返します。  
  
 ユーザー定義型は 16 進数として返されます**文字列**値。  
  
## <a name="see-also"></a>参照  
 [getString メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
