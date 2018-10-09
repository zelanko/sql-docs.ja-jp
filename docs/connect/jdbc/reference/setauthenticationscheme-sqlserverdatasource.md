---
title: (SQLServerDataSource) 場合、setAuthenticationScheme |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: d513ac4f8ca0e2cbdda575c9e110dcae3b1d45c5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47736170"
---
# <a name="setauthenticationscheme-sqlserverdatasource"></a>setAuthenticationScheme (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  アプリケーションで使用する統合セキュリティの種類を示します。  
  
## <a name="syntax"></a>構文  
  
```vb  
public void setAuthenticationScheme(String authenticationScheme);  
```  
  
#### <a name="parameters"></a>パラメーター  
 authenticationScheme  
  
 値は **"java Kerberos"** と既定 **"NativeAuthentication"** します。 詳細については、「[Kerberos 統合認証による SQL Server への接続](../../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
