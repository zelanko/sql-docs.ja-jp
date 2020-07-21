---
title: setInt メソッド (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setInt
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5e46b129-9fe1-469f-b2e8-7ce7fb832996
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 805029884b1fdc51bda3d07038839eff4941ffdc
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922213"
---
# <a name="setint-method-sqlserverpreparedstatement"></a>setInt メソッド (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、渡された **int** 値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setInt(int n,  
                         int value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *n*  
  
 パラメーターの番号を示す **int** です。  
  
 *value*  
  
 **int** 値です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setInt メソッドは、java.sql.PreparedStatement インターフェイスの setInt メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
