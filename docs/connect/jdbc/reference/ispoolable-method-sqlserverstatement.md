---
title: isPoolable メソッド (SQLServerStatement) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b8a12ac5-57cb-4288-9973-c7d5cebd197c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 593edaa8718e66afa7b748f2b07cfade4531be62
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ispoolable-method-sqlserverstatement"></a>isPoolable メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  ユーザー指定のステートメント プールにステートメントを追加できるかどうかを示す値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isPoolable() throws SQLException  
```  
  
## <a name="return-value"></a>戻り値  
 **true**ステートメントは、ユーザー指定のステートメント プールに追加できる場合**false**それ以外の場合。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 [setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)プール オブジェクトの動作を変更します。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
