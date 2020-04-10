---
title: setServerName メソッド (SQLServerDataSource) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f2a3c3c33fec8e36b799150dbe74dc69248e200d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920314"
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
  
## <a name="remarks"></a>解説  
 サーバー名は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を実行している、ターゲット コンピューターのホスト名です。 serverName プロパティが設定されていない場合、[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md) は既定値の null が返されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
