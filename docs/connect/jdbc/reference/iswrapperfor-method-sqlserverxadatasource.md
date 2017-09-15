---
title: "isWrapperFor メソッド (SQLServerXADataSource) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d612461d-4c3f-46db-b968-ff4c80b2aa7c
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ef878167c0c99be117f03ce6efffca4a9a76159e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="iswrapperfor-method-sqlserverxadatasource"></a>isWrapperFor メソッド (SQLServerXADataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このオブジェクトが指定されたインターフェイスのラッパーであるかどうかを示します。  
  
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
 [IsWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverxadatasource.md)メソッドおよび[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)メソッドは、JDBC 4.0 仕様で導入された java.sql.Wrapper インターフェイスによって定義されます。  
  
 このメソッドは、true を返します場合、呼び出し元[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)同じ引数では成功します。  
  
 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)です。  
  
## <a name="see-also"></a>参照  
 [unwrap メソッド & #40 です。SQLServerXADataSource &#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)   
 [SQLServerXADataSource のメソッド](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [SQLServerXADataSource のメンバー](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [SQLServerXADataSource クラス](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
