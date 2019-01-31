---
title: setServerName メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 70920828-eda0-4064-be9f-c1e460db8f00
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da3aee4570f579e4a3ed6007412222506ed2e24d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47827960"
---
# <a name="setservername-method-sqlserverdatasource"></a>setServerName メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を実行しているコンピューターの名前を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setServerName(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *serverName*  
  
 サーバー名を含む**文字列**です。  
  
## <a name="remarks"></a>Remarks  
 サーバー名は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を実行している、ターゲット コンピューターのホスト名です。 serverName プロパティが設定されていない場合、[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md) は既定値の null が返されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
