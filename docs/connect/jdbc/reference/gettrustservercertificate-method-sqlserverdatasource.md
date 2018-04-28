---
title: getTrustServerCertificate メソッド (SQLServerDataSource) |Microsoft ドキュメント
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
apiname:
- getTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- getTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: e4f443cc-b5d7-4859-81df-836a8642ed07
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fc7678ab661973525fab4219acbcacd3c874aa34
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="gettrustservercertificate-method-sqlserverdatasource"></a>getTrustServerCertificate メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返します、**ブール**trustServerCertificate プロパティが有効かどうかを示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getTrustServerCertificate()  
```  
  
## <a name="return-value"></a>戻り値  
 **true** trustServerCertificate が有効になっている場合。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 TrustServerCertificate プロパティ設定されている場合**true**、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]通信レイヤーが SSL で暗号化されている場合は、Secure Sockets Layer (SSL) 証明書が自動的に信頼します。 言い換えると、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]は検証されません、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SSL 証明書。 既定値は **false**です。  
  
 TrustServerCertificate プロパティ設定されている場合**false**、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]サーバー SSL 証明書を検証します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
