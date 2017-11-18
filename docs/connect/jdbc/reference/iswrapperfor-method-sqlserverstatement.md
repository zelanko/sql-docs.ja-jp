---
title: "isWrapperFor メソッド (SQLServerStatement) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53f3291f-d43a-476b-a656-d86168dacf6c
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: abe6782b9cf390431a20db38246184c131f9b1bd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="iswrapperfor-method-sqlserverstatement"></a>isWrapperFor メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  ステートメント オブジェクトが指定されたインターフェイスのラッパーであるかどうかを示します。  
  
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
 [IsWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)メソッドおよび[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)メソッドは、JDBC 4.0 で導入された java.sql.Wrapper インターフェイスによって定義されます。  
  
 このメソッドは、true を返します場合、呼び出し元[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)同じ引数では成功します。  
  
 コード例では、次を参照してください。[大規模なデータの更新のサンプル](../../../connect/jdbc/updating-large-data-sample.md)です。  
  
 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)です。  
  
## <a name="see-also"></a>参照  
 [unwrap メソッド & #40 です。SQLServerStatement &#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

