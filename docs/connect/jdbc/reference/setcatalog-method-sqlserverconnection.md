---
title: setCatalog メソッド (SQLServerConnection) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 553c0603-c07d-436a-86eb-3ba6b51bd696
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a123f6d8a51bdb20f5a90bec39eb4b44b19f110e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622770"
---
# <a name="setcatalog-method-sqlserverconnection"></a>setCatalog メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたカタログ名を設定し、[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) オブジェクトのデータベースの作業用サブスペースを選択します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setCatalog(java.lang.String catalog)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *catalog*  
  
 カタログ名を含む**文字列**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この setCatalog メソッドは、java.sql.Connection インターフェイスの setCatalog メソッドによって指定されます。  
  
 *カタログ*引数はエスケープ、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]自動的にします。 このメソッドを使用すると、Connection オブジェクトのカタログ プロパティが設定されます。 このプロパティは、他の方法で暗黙的に設定されることはありません。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
