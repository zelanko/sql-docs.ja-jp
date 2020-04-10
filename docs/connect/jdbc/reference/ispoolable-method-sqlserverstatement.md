---
title: isPoolable メソッド (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b8a12ac5-57cb-4288-9973-c7d5cebd197c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3f0b0e45e24d1eb8ddf23b3b544d7f6e7b52d728
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925817"
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
  
## <a name="remarks"></a>解説  
 [setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md) により、オブジェクトをプールできるかどうかを変更します。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
