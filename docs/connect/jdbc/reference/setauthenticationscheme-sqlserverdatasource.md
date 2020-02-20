---
title: setAuthenticationScheme (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b942f78e-7ce1-44ef-923d-a7c3d7c76b83
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3c728bd32a0aff2549d9e572955c8fb6d889e127
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67975287"
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
  
 値は **"JavaKerberos"** であり、既定値は **"NativeAuthentication"** です。 詳細については、「[Kerberos 統合認証による SQL Server への接続](../../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
