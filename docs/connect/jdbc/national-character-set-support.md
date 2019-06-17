---
title: 各国語文字セットのサポート |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4fceacfd-df4f-40cd-b7a2-5e5e58a5979f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ab17d9e60752b1aea747b03947d235b7d5f91605
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801809"
---
# <a name="national-character-set-support"></a>各国語文字セットのサポート
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  JDBC ドライバーは JDBC 4.0 API をサポートし、新しく各国語文字セットの変換 API メソッドが追加されています。 このサポートには、新しい setter、getter、および updater メソッドが含まれています**NCHAR**、 **NVARCHAR**、 **LONGNVARCHAR**、および**NCLOB** JDBC の型。  
  
 以下は、各国語文字セットの変換をサポートする新しい getter、setter、および updater メソッドの一覧です。  
  
-   [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md): [setNString](../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md)、[setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md)、[setNClob](../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)。  
  
-   [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)、[getNString](../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)、[getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md)、[setNString](../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md)、[setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)、[setNClob](../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)。  
  
-   [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md)、[getNString](../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md)、[getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)、[updateNClob](../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)、[updateNString](../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)、[updateNCharacterStream](../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)。  
  
> [!NOTE]  
>  アプリケーション内でこれらのメソッドを使用するには、sqljdbc4.jar ファイルをインクルードするためのクラスパスを設定する必要があります。  
  
 アプリケーションからサーバーに対し文字列パラメーターを Unicode 形式で送信するには、JDBC 4.0 の新しい National Character メソッドを使用する必要があります。National Character メソッド以外のメソッドを使用する場合は、**sendStringParametersAsUnicode** 接続プロパティを "**true**" に設定する必要があります。 できる限り、JDBC 4.0 の新しい National Character メソッドを使用することをお勧めします。 **sendStringParametersAsUnicode** 接続プロパティについて詳しくは、「[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーのデータ型について](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
