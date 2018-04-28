---
title: getPortNumber メソッド (SQLServerDataSource) |Microsoft ドキュメント
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
- SQLServerDataSource.getPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e5dc38d0-4340-4ad7-a56e-1d2a0f0fd846
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7cc115a11669b586a9e8271aad44e4ce11359c91
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getportnumber-method-sqlserverdatasource"></a>getPortNumber メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  通信するために使用される現在のポート番号を返します[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getPortNumber()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**現在のポート番号を含む値です。  
  
## <a name="remarks"></a>解説  
 ポート番号へのソケット接続を開くときに使用される TCP/IP ポート番号は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。 portNumber プロパティが設定されていない場合、getPortNumber メソッドは既定値の 1433 を返します。  
  
> [!NOTE]  
>  [SetPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)メソッドでは、任意の範囲に渡されたポート値のチェックは実行しません。 エラーをトリガーすることがなく 99999 などの無効な番号を渡すことができます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
