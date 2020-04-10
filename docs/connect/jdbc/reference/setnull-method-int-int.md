---
title: setNull メソッド (int, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setNull (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7e7f08e9-278a-495a-8ce3-ca173d055021
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f250113f83ea51c2705d81780c2207f63149a292
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920456"
---
# <a name="setnull-method-int-int"></a>setNull (int, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたパラメーターの型で、指定されたパラメーターを null 値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setNull(int index,  
                          int jdbcType)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 パラメーターの番号を示す **int** です。  
  
 *jdbcType*  
  
 java.sql.Types で定義される JDBC 型のコードです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setNull メソッドは、java.sql.PreparedStatement インターフェイスの setNull メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [setNull メソッド &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setnull-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
