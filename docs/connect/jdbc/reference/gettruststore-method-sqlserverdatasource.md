---
title: getTrustStore メソッド (SQLServerDataSource) |Microsoft ドキュメント
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
- getTrustStore Method (SQLServerDataSource)
apilocation:
- getTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 8f5850e4-8627-49a8-ba0e-b1f4014322a5
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d221abb34dbae1c2152602cf3f0bafee39e126c6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="gettruststore-method-sqlserverdatasource"></a>getTrustStore メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  証明書の trustStore ファイルへのパス (ファイル名を含む) を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getTrustStore()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**値が設定されていない場合、証明書の trustStore ファイル、または null へのパス (ファイル名を含む) を含むです。  
  
## <a name="remarks"></a>解説  
 TrustStore プロパティが設定されていない場合、 [getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md) null が返されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
