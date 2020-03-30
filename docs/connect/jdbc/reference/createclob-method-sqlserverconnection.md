---
title: createClob メソッド (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 58b0865a-1cde-4046-9761-51e471294023
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 417a5048d809cb4498c543c589324e151a843a18
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67955391"
---
# <a name="createclob-method-sqlserverconnection"></a>createClob メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データが含まれていない Clob オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Clob createClob()  
```  
  
## <a name="return-value"></a>戻り値  
 Clob オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この createClob メソッドは、java.sql.Connection インターフェイスの createClob メソッドで指定されています。  
  
 このメソッドにより、[SQLServerClob コンストラクター &#40;SQLServerConnection, java.lang.String&#41;](../../../connect/jdbc/reference/sqlserverclob-constructor-sqlserverconnection-java-lang-string.md) は必要なくなります。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
