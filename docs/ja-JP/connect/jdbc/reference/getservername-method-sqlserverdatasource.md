---
title: getServerName メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.getServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3004ed22-5d69-4dd0-8761-d39f0b7dde13
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f52990aa15bc059c1da3b34e203a9bea1ccaf0f9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getservername-method-sqlserverdatasource"></a>getServerName メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  名前を返します、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getServerName()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**を格納しているサーバー名または null 値が設定されていない場合。  
  
## <a name="remarks"></a>解説  
 サーバー名を実行しているターゲット コンピューターのホスト名[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。 GetServerName プロパティが設定されていない場合、getServerName は既定値は null を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
