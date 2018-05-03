---
title: setFetchDirection メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
ms.topic: conceptual
apiname:
- SQLServerResultSet.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ee82290-508d-4bff-a5c5-8a56338deef8
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c52272d3bceb80993420b13846d8357b2fed1a0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="setfetchdirection-method-sqlserverresultset"></a>setFetchDirection メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  方向についてのヒントは、この行[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトが処理されます。  
  
> [!NOTE]  
>  このメソッドは現在サポートされていません、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]です。 このメソッドを使用すると、JDBC ドライバーに設定が保存されますが、現時点ではドライバーはその設定に従って動作しません。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setFetchDirection(int direction)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *方向*  
  
 **Int**推奨されるフェッチ方向を示すです。 次の値のいずれかです。  
  
 ResultSet.FETCH_FORWARD  
  
 ResultSet.FETCH_REVERSE  
  
 ResultSet.FETCH_UNKNOWN  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setFetchDirection メソッドは、java.sql.ResultSet インターフェイスの setFetchDirection メソッドによって指定されます。  
  
 このメソッドの初期値がによって決まりますが、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)を SQLServerResultSet オブジェクトを生成したオブジェクト。 フェッチ方向はいつでも変更できます。  
  
> [!NOTE]  
>  カーソルの種類が順方向専用の場合にこのメソッドを使用しても、効果はありません。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
