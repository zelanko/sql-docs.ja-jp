---
title: isWrapperFor メソッド (SQLServerDataSource) |Microsoft ドキュメント
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
ms.assetid: f77af027-c021-4a17-b264-1ee592bfdd84
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8b687a5d3f05484eb906e14773dd0b519d387215
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="iswrapperfor-method-sqlserverdatasource"></a>isWrapperFor メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データ ソース オブジェクトが指定されたインターフェイスのラッパーであるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *iface*  
  
 A**クラス**インターフェイスを定義します。  
  
## <a name="return-value"></a>戻り値  
 **true**か、このオブジェクト インターフェイスを実装するインターフェイスを実装するオブジェクトをラップします。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 [IsWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)メソッドおよび[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)メソッドは、JDBC 4.0 仕様で導入された java.sql.Wrapper インターフェイスによって定義されます。  
  
 このメソッドは、true を返します場合、呼び出し元[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)同じ引数では成功します。  
  
 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)です。  
  
## <a name="see-also"></a>参照  
 [unwrap メソッド&#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)   
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
