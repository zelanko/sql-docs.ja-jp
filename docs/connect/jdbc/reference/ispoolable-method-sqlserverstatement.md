---
title: isPoolable メソッド (SQLServerStatement) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b8a12ac5-57cb-4288-9973-c7d5cebd197c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a5fcc6d842299884bec758ca66f303bf3e8ed625
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796470"
---
# <a name="ispoolable-method-sqlserverstatement"></a>isPoolable メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  ユーザー指定のステートメント プールにステートメントを追加できるかどうかを示す値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isPoolable() throws SQLException  
```  
  
## <a name="return-value"></a>戻り値  
 ユーザー指定のステートメント プールにステートメントを追加できる場合は **true**、それ以外の場合は **false** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 [setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md) により、オブジェクトをプールできるかどうかを変更します。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
