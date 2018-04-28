---
title: 各国語文字セットのサポート |Microsoft ドキュメント
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
ms.assetid: 4fceacfd-df4f-40cd-b7a2-5e5e58a5979f
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eb6c55580a3162de11db16f36ca03b4f0289d29b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="national-character-set-support"></a>各国語文字セットのサポート
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  JDBC ドライバーは JDBC 4.0 API をサポートし、新しく各国語文字セットの変換 API メソッドが追加されています。 このサポートには、新しい setter、getter、および updater メソッドが含まれています。 **NCHAR**、 **NVARCHAR**、 **LONGNVARCHAR**、および**NCLOB** JDBC の型。  
  
 以下は、各国語文字セットの変換をサポートする新しい getter、setter、および updater メソッドの一覧です。  
  
-   [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md): [setNString](../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md)、 [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md)、 [setNClob](../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)です。  
  
-   [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)、 [getNString](../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)、 [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md)、 [setNString](../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md)、 [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)、 [setNClob](../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)です。  
  
-   [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md)、 [getNString](../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md)、 [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)、 [updateNClob](../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)、 [updateNString](../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)、 [updateNCharacterStream](../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)です。  
  
> [!NOTE]  
>  アプリケーション内でこれらのメソッドを使用するには、sqljdbc4.jar ファイルをインクルードするためのクラスパスを設定する必要があります。  
  
 文字列パラメーターを Unicode 形式でサーバーを送信するために、アプリケーションを使用か JDBC 4.0 の新しい national character メソッド;設定または、 **sendStringParametersAsUnicode**接続プロパティを"**true**"非 national character メソッドを使用する場合。 できる限り、JDBC 4.0 の新しい National Character メソッドを使用することをお勧めします。 詳細については、 **sendStringParametersAsUnicode**接続プロパティを参照してください[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーのデータ型について](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
