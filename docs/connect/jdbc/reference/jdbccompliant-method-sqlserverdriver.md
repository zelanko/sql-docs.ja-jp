---
title: jdbcCompliant メソッド (SQLServerDriver) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.jdbcCompliant
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b299b20d-d1cd-45b3-91dc-dcf579498570
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c36d7980355eed1e1a1e8f42fb53c75fdb70d0ed
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67976950"
---
# <a name="jdbccompliant-method-sqlserverdriver"></a>jdbcCompliant メソッド (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] が JDBC 仕様に準拠しているかどうかを確認します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean jdbcCompliant()  
```  
  
## <a name="return-value"></a>戻り値  
 JDBC ドライバーが最低限の要件を満たしている場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 この jdbcCompliant メソッドは、java.sql.Driver インターフェイスの jdbcCompliant メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerDriver のメソッド](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver のメンバー](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver クラス](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
