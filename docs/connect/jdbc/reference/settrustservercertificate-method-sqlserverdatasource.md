---
title: setTrustServerCertificate メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- setTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- setTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 6c37b518-147e-4cd9-9eff-b48a3f5888c6
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9883077d2cb947f2c57e54439566f1936badbe5
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785316"
---
# <a name="settrustservercertificate-method-sqlserverdatasource"></a>setTrustServerCertificate メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  セットを**ブール**trustServerCertificate プロパティが有効になっているかどうかを示す値です。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setTrustServerCertificate(boolean trustServerCertificate)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *trustServerCertificate*  
  
 通信レイヤーが SSL で暗号化されているときに、サーバーの SSL (Secure Sockets Layer) 証明書が自動的に信頼されるようにする場合は、**true** です。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>Remarks  
 trustServerCertificate プロパティが **true** に設定されている場合、通信レイヤーが SSL で暗号化されているときに、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の SSL 証明書が自動的に信頼されます。 つまり、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] によって [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の SSL 証明書は検証されません。 既定値は **false**です。  
  
 trustServerCertificate プロパティが **false** に設定されている場合は、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] によってサーバーの SSL 証明書が検証されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
