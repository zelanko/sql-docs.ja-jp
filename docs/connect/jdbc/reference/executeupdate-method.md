---
title: executeUpdate メソッド () |Microsoft ドキュメント
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
- SQLServerPreparedStatement.executeUpdate ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ca534c6b-ef4d-4ae8-8cc3-514728623cff
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a4d3caaa9cad0b1e9c47edece18015e6d270f1b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="executeupdate-method-"></a>executeUpdate () メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この SQL ステートメントを実行します。 [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)オブジェクトを、SQL の INSERT、UPDATE、MERGE、または DELETE ステートメントまたは DDL ステートメントなど、何を返す SQL ステートメントがあります。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int executeUpdate()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int** DDL ステートメントを使用する場合、影響を受ける行または 0 の数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この executeUpdate メソッドは、java.sql.PreparedStatement インターフェイスの executeUpdate メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [executeUpdate メソッド&#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
