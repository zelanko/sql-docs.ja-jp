---
title: setUser メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setUser
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d2ea7906-2d10-438d-aa51-f576eea923c7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f3953763dc1b8a0d24e4c335b5b465c49707174
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784160"
---
# <a name="setuser-method-sqlserverdatasource"></a>setUser メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データ ソースへの接続に使用されるユーザー名を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setUser(java.lang.String user)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *user*  
  
 ユーザー名を含む**文字列**です。  
  
## <a name="remarks"></a>Remarks  
 setUser メソッドでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] への接続に使用されるユーザー名が設定されます。 ユーザー名の値が設定されていない場合、[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md) メソッドからは既定値の null が返されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
