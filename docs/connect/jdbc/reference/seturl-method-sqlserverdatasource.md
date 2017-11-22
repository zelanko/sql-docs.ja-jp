---
title: "setURL メソッド (SQLServerDataSource) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDataSource.setURL
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: bea70100-ac98-4625-8748-ef7cc0b111ea
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 222948f40537e84e0c294f05fd8d953b61f53f65
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="seturl-method-sqlserverdatasource"></a>setURL メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データ ソースへの接続に使用される URL を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setURL(java.lang.String url)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *url*  
  
 A**文字列**URL を格納しています。  
  
## <a name="remarks"></a>解説  
 セキュリティ上の理由から、setURL メソッドに渡された URL でいないパスワードを含める必要があります。 これは、サードパーティの Java アプリケーション サーバーでは、データ ソースの構成用ユーザー インターフェイスに、URL プロパティの値セットが表示されることが非常に多いためです。 代わりに、使用、 [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)パスワードの値を設定します。 Java アプリケーション サーバーで、データ ソース内に設定されたパスワードが構成用ユーザー インターフェイスに表示されなくなります。  
  
> [!NOTE]  
>  呼び出しの前に、setURL メソッドが呼び出されない場合、 [getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)メソッド、getURL、既定値を返しますの"jdbc:sqlserver://"です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
