---
title: setAuthenticationScheme (SQLServerDataSource) |Microsoft ドキュメント
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
ms.topic: article
ms.assetid: b942f78e-7ce1-44ef-923d-a7c3d7c76b83
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2d02caf7bda1ab337bed7682db3e5bafd2c8e946
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="setauthenticationscheme-sqlserverdatasource"></a>setAuthenticationScheme (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  アプリケーションで使用する統合セキュリティの種類を示します。  
  
## <a name="syntax"></a>構文  
  
```vb  
public void setAuthenticationScheme(String authenticationScheme);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *authenticationScheme*  
  
 値は **"java Kerberos"** と既定 **"NativeAuthentication"** です。 詳細については、次を参照してください。[を使用して Kerberos 統合認証を SQL Server への接続](../../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
