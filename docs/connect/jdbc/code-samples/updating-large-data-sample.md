---
title: "大量のデータ サンプルの更新 |Microsoft ドキュメント"
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
ms.assetid: 76ecc05f-a77d-40a2-bab9-91a7fcf17347
caps.latest.revision: "27"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.openlocfilehash: 4820063233abe12d59ec961ee9b05a63c6547112
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="updating-large-data-sample"></a>大きなデータを更新するサンプル
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これは、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]サンプル アプリケーションは、データベース内の大きな列を更新する方法を示します。  
  
 このサンプルのコード ファイルは updateLargeData.java という名前で、次の場所にあります。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \samples\adaptive  
  
## <a name="requirements"></a>必要条件  
 このサンプル アプリケーションを実行するにはアクセス許可が必要、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]サンプル データベース。 また、クラスパスの設定で sqljdbc4.jar ファイルを追加する必要があります。 クラスパスに sqljdbc4.jar のエントリがない場合、サンプル アプリケーションで "Class not found" という一般的な例外がスローされます。 クラスパスを設定する方法の詳細については、次を参照してください。 [JDBC ドライバーを使用して](../../../connect/jdbc/using-the-jdbc-driver.md)です。  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Sqljdbc.jar、sqljdbc4.jar、sqljdbc41.jar、または sqljdbc42.jar のクラス ライブラリ ファイルを必要な Java ランタイム環境 (JRE) 設定によって使い分けることが用意されています。 このサンプルでは、 [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)と[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)メソッドで、ドライバー固有の応答バッファリング メソッドにアクセスする、JDBC 4.0 API が導入されています。 このサンプルをコンパイルして実行するには、JDBC 4.0 をサポートする sqljdbc4.jar クラス ライブラリが必要となります。 選択する JAR ファイルの詳細については、次を参照してください。 [JDBC Driver のシステム要件](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)です。  
  
## <a name="example"></a>例  
 次の例では、サンプル コードへの接続、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]データベース。 サンプル コードのステートメント オブジェクトを作成しを使用して、 [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) 、Statement オブジェクトが、指定されたラッパーであるかどうかを確認する方法を[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)クラスです。 [Unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)ドライバー固有の応答バッファリング メソッドにアクセスするメソッドを使用します。  
  
 次に、サンプル コードは設定応答バッファリング モードを"**アダプティブ**"を使用して、 [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)クラス、さらにアダプティブ バッファリング モードを取得する方法を示します。  
  
 次に、SQL ステートメントを実行し、更新可能なに返されるデータを配置[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
 最後に、結果セットに格納されているデータ行を反復処理します。 が見つかった場合、空のドキュメント概要の組み合わせを使用して[updateString](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md)と[updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)データの行を更新し、再度データベースに保持できるメソッドです。 使用してデータが既にあるを場合、 [getString](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)に含まれるデータの一部を表示します。  
  
 ドライバーの既定の動作は"**アダプティブ**"。 ただし、順方向専用の更新可能な結果セットと、結果セット内のデータが、アプリケーションのメモリよりも大きい場合は、アプリケーションを使用して明示的にアダプティブ バッファリング モードを設定、 [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)メソッド、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)クラスです。  
  
 [!code[JDBC#UsingAdaptiveBuffering3](../../../connect/jdbc/codesnippet/Java/updating-large-data-sample_1.java)]  
  
## <a name="see-also"></a>参照  
 [大きなデータの処理](../../../connect/jdbc/working-with-large-data.md)  
  
  
