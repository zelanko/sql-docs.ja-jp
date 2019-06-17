---
title: setCursorName メソッド (SQLServerStatement) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setCursorName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3f3ec4f2-103a-4e16-9206-c5bd8639f946
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 35039fae2f3e3215a0df254f7b1d4619e97d3634
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794002"
---
# <a name="setcursorname-method-sqlserverstatement"></a>setCursorName メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  SQL カーソル名を、渡された文字列に設定します。この文字列は、後に続く実行 (execute) メソッドによって使用されます。  
  
> [!NOTE]  
>  このメソッドは、現在 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ではサポートされていません。 このメソッドを呼び出しても、何も効果はありません。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setCursorName(java.lang.String name)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *name*  
  
 カーソル名を含む **String** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この setCursorName メソッドは、java.sql.Statement インターフェイスの setCursorName メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
