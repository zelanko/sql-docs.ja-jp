---
title: getSendStringParametersAsUnicode メソッド (SQLServerDataSource) |Microsoft ドキュメント
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
- SQLServerDataSource.getSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3836d0ab-c3fb-41ff-bb89-10389594ae51
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8286a658b12df7466c2eec2d702c1fc3e005f06f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getsendstringparametersasunicode-method-sqlserverdatasource"></a>getSendStringParametersAsUnicode メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返します、**ブール**文字列パラメーターを UNICODE 形式でサーバーに送信が有効かどうかを示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getSendStringParametersAsUnicode()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**文字列パラメーターが UNICODE 形式でサーバーに送信された場合。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 SendStringParametersAsUnicode プロパティ設定されている場合**true**既定値は、文字列パラメーターが UNICODE 形式でサーバーに送信されます。 SendStringParametersAsUnicode に設定されている場合**false**、文字列パラメーターは、UNICODE ではなく ASCII/MBCS 形式でサーバーに送信されます。 SendStringParametersAsUnicode が設定されていない場合、getSendStringParametersAsUnicode の既定値を返します**true**です。  
  
 SendStringParametersAsUnicode 接続プロパティの詳細については、次を参照してください。[接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
