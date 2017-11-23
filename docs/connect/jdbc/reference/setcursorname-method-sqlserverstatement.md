---
title: "setCursorName メソッド (SQLServerStatement) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerStatement.setCursorName
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3f3ec4f2-103a-4e16-9206-c5bd8639f946
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6b0e86545f58b67d5a8552c6de8f77faa35c087e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setcursorname-method-sqlserverstatement"></a>setCursorName メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  SQL カーソル名を、渡された文字列に設定します。この文字列は、後に続く実行 (execute) メソッドによって使用されます。  
  
> [!NOTE]  
>  このメソッドは現在サポートされていません、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]です。 このメソッドを呼び出しても、何も効果はありません。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setCursorName(java.lang.String name)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *name*  
  
 A**文字列**カーソル名を格納しています。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setCursorName メソッドは、java.sql.Statement インターフェイスの setCursorName メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
