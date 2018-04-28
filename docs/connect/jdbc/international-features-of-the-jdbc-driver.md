---
title: JDBC ドライバーの国際化機能 |Microsoft ドキュメント
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
ms.assetid: bbb74a1d-9278-401f-9530-7b5f45aa79de
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7a9960483a410875f4c91d2b809b27f5c74c7d4b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="international-features-of-the-jdbc-driver"></a>JDBC ドライバーの国際対応機能」を参照してください。
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  国際化機能、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]次のとおりです。  
  
-   同じ言語に完全にローカライズされたサービスのサポート [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]  
  
-   ロケール依存型の Java 言語変換をサポート[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ  
  
-   オペレーティング システムに関係なく、世界中の言語に対応  
  
-   世界中のドメイン名に対応 (Microsoft JDBC Driver 6.0 for SQL Server より)  
  
## <a name="handling-of-character-data"></a>文字データの処理  
 Java の文字データは、既定では Unicode として処理されます。Java**文字列**オブジェクトは Unicode 文字データを表します。 JDBC ドライバーにおいてこの規則の唯一の例外となるのは、ASCII ストリームの getter メソッドと setter メソッドです。暗黙の仮定で既知のコード ページの 1 つ (ASCII) によるバイト ストリームが使用されるため、これは特殊なケースです。  
  
 さらに、JDBC driver は、 **sendStringParametersAsUnicode**接続文字列プロパティです。 このプロパティを使用して、文字データに対して準備されたパラメーターを Unicode ではなく ASCII またはマルチバイト文字セット (MBCS) で送信するように指定できます。 詳細については、 **sendStringParametersAsUnicode**接続文字列プロパティを参照してください[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。  
  
### <a name="driver-incoming-conversions"></a>ドライバーの受信変換  
 サーバーから受信する Unicode テキスト データは、変換する必要はありません。 データは Unicode として直接渡されます。 サーバーから受信する Unicode 以外のデータは、データベースまたは列レベルでデータのコード ページから Unicode に変換されます。 JDBC ドライバーは、Java 仮想マシン (JVM) 変換ルーチンを使用してこのような変換を実行します。 変換は、あらゆる型の文字列および文字のストリームの getter メソッドで実行されます。  
  
 JVM がデータベースのデータに対して適切なコード ページをサポートしていない場合、JDBC ドライバーは、"XXX コード ページは Java 環境ではサポートされていません。" という例外をスローします。 この問題を回避するには、その JVM でサポートする必要のある国際的な文字を完全にインストールする必要があります。 詳細については、Sun Microsystems の Web サイトの「サポートされているエンコーディング」を参照してください。  
  
### <a name="driver-outgoing-conversions"></a>ドライバーの送信変換  
 ドライバーからサーバーへ送信される文字データは、ASCII または Unicode です。 など、新しい JDBC 4.0 national character メソッド、setNString、setNCharacterStream、setNClob 方法など[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)と[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラス常にパラメーター値を Unicode では、サーバーに送信します。  
  
 その一方で、非 national character API メソッドのなどの setString、setCharacterStream、setClob メソッド[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)と[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラス値が Unicode でサーバーに送信される場合にのみ、 **sendStringParametersAsUnicode**プロパティが"true"には、既定値に設定します。  
  
## <a name="non-unicode-parameters"></a>Unicode 以外のパラメーター  
 パフォーマンスを最適化**CHAR**、 **VARCHAR**または**LONGVARCHAR** Unicode 以外のパラメーターの型、設定、 **sendStringParametersAsUnicode**接続文字列を"false"のプロパティと非 national character メソッドを使用します。  
  
## <a name="formatting-issues"></a>書式設定に関する問題  
 日付、時刻、通貨、ローカライズされたデータのすべての書式設定で実行されます。 ロケール オブジェクトを使用して、Java 言語レベルさまざまな書式設定メソッド**日付**、**カレンダー**、および**数**データ型。 JDBC ドライバーがロケールに依存するデータをローカライズされた書式で渡す必要があることはまれですが、このような場合は既定の JVM ロケールを使用して適切なフォーマッタが使用されます。  
  
## <a name="collation-support"></a>照合順序のサポート  
 JDBC Driver 3.0 でサポートされているすべての照合順序をサポートしている[!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)]、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)]、新しい照合順序や新しいバージョンの Windows 照合順序名がで導入された[!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)]です。  
  
 照合順序の詳細については、次を参照してください。 [Collation and Unicode Support](http://go.microsoft.com/fwlink/?LinkId=131366)と[Windows 照合順序名 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=131367)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="using-international-domain-names-idn"></a>国際ドメイン名 (IDN) の使用  
 JDBC Driver 6.0 for SQL Server では、国際化ドメイン名 (Idn) の使用をサポートしを ASCII 互換エンコーディング (Punycode) の接続中に必要なときに、Unicode serverName を変換することができます。  IDN がドメイン名システム (DNS) に Punycode 形式 (仕様は RFC 3490 で既定) で ASCII 文字列として保存されている場合、serverNameAsACE プロパティを「true」に設定することで Unicode サーバー名を変換できます。  そのように保存されていなければ、DNS サービスが Unicode 文字を使用できるように構成されている場合、serverNameAsACE プロパティを既定の「false」に設定します。  以前のバージョンの JDBC ドライバーでは、可能であればも Punycode を使用して、サーバー名に変換する[Java の IDN.toASCII](http://docs.oracle.com/javase/8/docs/api/java/net/IDN.html)接続のプロパティを設定する前にメソッドです。  
  
> [!NOTE]  
>  Windows プラットフォーム以外のために記述されたリゾルバー ソフトウェアの大半はインターネット DSN 標準に基づき、多くの場合、IDN に Punycode 形式を使用します。一方で、プライベート ネットワークの Windows ベースのDNS サーバーはサーバーごとに UTF-8 文字を使用できるように構成できます。  詳細については、次を参照してください。 [Unicode 文字のサポート](https://technet.microsoft.com/library/cc738403(v=ws.10).aspx)です。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
