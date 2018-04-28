---
title: getClientConnectionID メソッド (SQLServerConnection) |Microsoft ドキュメント
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
ms.assetid: bee39c11-733a-461f-92cc-33efcb2af87d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1f9e8ff7cd298030613b0158a8b8ae6468c1c273
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getclientconnectionid-method-sqlserverconnection"></a>getClientConnectionID メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  接続に成功したか失敗したかにかかわらず、直近に試行された接続の ID を取得します。  
  
## <a name="syntax"></a>構文  
  
``` 
public Java.util.UUID SQLServerConnection.getClientConnectionID();  
```  
  
## <a name="return-value"></a>戻り値  
 直近に試行された接続の ID を表す、16 バイトの GUID。 接続要求の開始後にエラーが発生し、ログイン前ハンドシェイクに失敗した場合は NULL。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 拡張イベント ログの診断情報にアクセスする方法の詳細については、次を参照してください。[診断の情報を拡張イベント ログへのアクセス](../../../connect/jdbc/accessing-diagnostic-information-in-the-extended-events-log.md)です。  
  
 次のサンプルは、接続 ID の取得方法を示しています。  
  
```  
Connection con = DriverManager.getConnection(connectionUrl);  
UUID id = ((ISQLServerConnection)con).getClientConnectionId();  
```  
  
 次のサンプルは、接続 ID を取得する別の方法を示しています。  
  
```  
SQLServerConnectionPoolDataSource ds = new SQLServerConnectionPoolDataSource();  
ds.setUser("…");  
ds.setPassword("…");  
ds.setServerName("…");  
PooledConnection pcon= ds.getPooledConnection();  
Connection cn = pcon.getConnection();  
UUID conid = ((ISQLServerConnection)cn).getClientConnectionId();  
```  
  
 **getClientConnectionID**に接続するサーバーのバージョンに関係なく動作は、拡張イベント ログおよび接続リング バッファー エラーに関するエントリが存在していない[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]2008 R2 以前のバージョン。  
  
 接続 ID のログ記録に関する拡張イベントが有効になっている場合は、拡張イベント ログ内で接続 ID を探し、エラーがサーバー上のものであるかどうかを確認できます。 接続リング バッファーに、接続 ID を検索することもできます ([、接続リング バッファーによる SQL Server 2008 の接続のトラブルシューティング](http://go.microsoft.com/fwlink/?LinkId=207752)) 特定の接続エラーです。 接続 ID が接続リング バッファー内にない場合は、ネットワーク エラーであると考えることができます。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
