---
title: setFloat メソッド (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setFloat
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 870d0031-6871-4dc0-b03a-fb0a9ff6ab98
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 83221ed88b354eb7b00ae151755129d1a7dc020c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67974229"
---
# <a name="setfloat-method-sqlserverpreparedstatement"></a>setFloat メソッド (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、渡された **float** 値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setFloat(int n,  
                           float x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *n*  
  
 パラメーターの番号を示す **int** です。  
  
 *x*  
  
 **float** 値です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setFloat メソッドは、java.sql.PreparedStatement インターフェイスの setFloat メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
