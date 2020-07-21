---
title: setBoolean メソッド (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setBoolean
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 63397a19-03a2-44bb-b661-7d62c95b6e4e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9742112df6732618eeef07c477af98ff033368fc
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928806"
---
# <a name="setboolean-method-sqlserverpreparedstatement"></a>setBoolean メソッド (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、渡された **boolean** 値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setBoolean(int n,  
                             boolean x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *n*  
  
 パラメーターの番号を示す **int** です。  
  
 *x*  
  
 **boolean** 値。**true** または **false**。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setboolean メソッドは、java.sql.PreparedStatement インターフェイスの setboolean メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
