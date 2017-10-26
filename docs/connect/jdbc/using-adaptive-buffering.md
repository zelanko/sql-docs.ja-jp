---
title: "アダプティブ バッファリングの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92d4e3be-c3e9-4732-9a60-b57f4d0f7cb7
caps.latest.revision: 53
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 80944d5ebb5ec8c9f6ba98d9c520b10a0c4ade30
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-adaptive-buffering"></a>アダプティブ バッファリングの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  アダプティブ バッファリングは、サーバー カーソルのオーバーヘッドを発生させることなく、あらゆる種類の大きな値のデータを取得できるように設計されています。 アプリケーションはすべてのバージョンのでアダプティブ バッファリング機能を使用することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ドライバーによってサポートされています。  
  
 通常、ときに、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]クエリを実行する、すべての結果、サーバーからメモリに取り出しますアプリケーションです。 この方法でリソースの消費量を最小限に抑えられますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、OutOfMemoryError、非常に大きな結果を生成するクエリの JDBC アプリケーションでスローされることができます。  
  
 アプリケーションが、非常に大きな結果を処理できるようにするために、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]アダプティブ バッファリングを提供します。 アダプティブ バッファリングとドライバーがからステートメントの実行結果を取得、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]一度にはなく、アプリケーションの必要に応じて、します。 また、アプリケーションからアクセスできなくなった結果は、ドライバーによって直ちに破棄されます。 アダプティブ バッファリングは次のような場合に効果的です。  
  
-   **クエリが非常に大きな結果セットを生成:**アプリケーションは、アプリケーションがメモリに格納できるよりも、複数の行を生成する SELECT ステートメントを実行できます。 以前のリリースで、アプリケーションは、OutOfMemoryError を避けるために、サーバー カーソルを使用する必要があります。 アダプティブ バッファリングは、サーバー カーソルを使用することなく、任意の大きな結果セットを順方向専用かつ読み取り専用で渡せるようにします。  
  
-   **クエリが非常に大きな**[SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)**列または**[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)**OUT パラメーター値。**アプリケーションが 1 つの値を取得できます (列または OUT パラメーター) が大きすぎてすべてアプリケーションのメモリ内に収まりません。         アダプティブ バッファリングにより、クライアント アプリケーションを getAsciiStream、getBinaryStream または getCharacterStream メソッドを使用して、ストリームとして、このような値を取得します。 アプリケーションから値を取得、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ように、ストリームから読み取ります。  
  
> [!NOTE]  
>  アダプティブ バッファリングでは、必要な量のデータだけが、JDBC ドライバーによってバッファリングされます。 ドライバーにバッファーのサイズを制御したり制限したりするためのパブリック メソッドは備わっていません。  
  
## <a name="setting-adaptive-buffering"></a>アダプティブ バッファリングの設定  
 以降では、JDBC driver version 2.0 では、ドライバーの既定の動作は"**アダプティブ**"です。 つまり、アプリケーションから明示的に要求しなくても、アダプティブ バッファリングの動作が適用されます。 バージョン 1.2 リリースでは、バッファリング モードが"**完全**"既定では、アプリケーションは、明示的にアダプティブ バッファリング モードを要求する必要があります。  
  
 アプリケーションがステートメントの実行でアダプティブ バッファリングを使用するように要求できる方法は 3 つあります。  
  
-   アプリケーションは、接続プロパティを設定できる**responseBuffering**を"adaptive"です。 接続プロパティの設定の詳細については、次を参照してください。[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。  
  
-   アプリケーションを使用して、 [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)のメソッド、 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)応答バッファリング モードを使用して作成したすべての接続を設定するオブジェクト[SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクト。  
  
-   アプリケーションを使用して、 [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)応答バッファリング モードの特定のステートメント オブジェクトを設定するクラス。  
  
 JDBC Driver version 1.2、statement オブジェクトをキャストするために必要なアプリケーションを使用する場合、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)クラスを使用する、 [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)メソッドです。 コード例で、[読み取り大規模なデータ サンプル](../../connect/jdbc/reading-large-data-sample.md)と[ストアド プロシージャのサンプルを使用して大規模なデータの読み取り](../../connect/jdbc/reading-large-data-with-stored-procedures-sample.md)この古い使用法を説明します。  
  
 ただし、JDBC driver version 2.0 では、アプリケーションを使用、 [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)メソッドおよび[unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)に関する想定せずベンダー固有の機能にアクセスする方法、実装クラスの階層構造です。 コード例を参照してください、[大規模なデータの更新のサンプル](../../connect/jdbc/updating-large-data-sample.md)トピックです。  
  
## <a name="retrieving-large-data-with-adaptive-buffering"></a>アダプティブ バッファリングによる大きなデータの取得  
 ときに、大きな値は get を使用して、1 回読み取り\<型 > Stream メソッド、および ResultSet 列および CallableStatement OUT パラメーターがによって返される順序でアクセス、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]アプリケーションを最小限にアダプティブ バッファリング結果を処理するときにメモリ使用量 アダプティブ バッファリングを使用すると、次のようになります。  
  
-   Get\<型 > で定義されているメソッドをストリーム、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)と[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)場合は、ストリームをリセットすることができますが、クラスが既定では、1 回だけ読み取りストリームを返すアプリケーションによってマークされます。 アプリケーションがする場合は`reset`を呼び出すが、ストリーム、`mark`にメソッドが最初にストリームします。  
  
-   Get\<型 > で定義されているメソッドをストリーム、 [SQLServerClob](../../connect/jdbc/reference/sqlserverclob-class.md)と[SQLServerBlob](../../connect/jdbc/reference/sqlserverblob-class.md)クラスでは、常に位置を変更できるストリームを返すことがなく、ストリームの開始位置を呼び出す、`mark`メソッドです。  
  
 アプリケーションがアダプティブ バッファリングを使用する場合、get で取得した値\<型 > Stream メソッドは、1 回だけ取得できます。 場合は、get を呼び出すしようとする\<型 > メソッド パラメーター、get の呼び出し後に、同じ列に\<型 >、メッセージのストリーム、同じ、オブジェクトのメソッドで例外がスローされます、"データへのアクセスがこれには使用できません列またはパラメーター"です。  
  
> [!NOTE]
> 結果セットの処理の途中で ResultSet.close() への呼び出しには、読み取りし、残りのすべてのパケットを破棄する SQL Server の Microsoft JDBC Driver が必要です。 クエリに大きなデータ セットが返される場合、およびネットワーク接続速度が遅い場合は特に、かなりの時間がかかります。     
  
## <a name="guidelines-for-using-adaptive-buffering"></a>アダプティブ バッファリングを使用するうえでのガイドライン  
 アプリケーションによるメモリ使用量を最小限に抑えるには、開発者は次の重要なガイドラインに従う必要があります。  
  
-   接続文字列プロパティは使用しないでください**selectMethod = cursor**非常に大きな結果を処理するアプリケーションを許可する設定。 アダプティブ バッファリング機能を使用すると、アプリケーションがサーバー カーソルを使用することなく、非常に大きな順方向専用の読み取り専用結果セットを処理することが可能になります。 設定するときに注意してください**selectMethod = cursor**、前方参照専用すべてその接続によって生成された読み取り専用の結果セットに影響があります。 つまり、アプリケーションは、わずかな行数の短い結果セットを定期的に処理する場合の作成、読み取り、および各結果セットは、クライアント側とサーバー側の両方でよりも多くのリソースを使用するために、サーバー カーソルを閉じる場所、 **selectMethod**に設定されていない**カーソル**です。  
  
-   大きなテキストまたはバイナリ値を getBlob または getClob メソッドではなく、getAsciiStream、getBinaryStream または getCharacterStream メソッドを使用して、ストリームとして読み取ります。 バージョン 1.2 リリース以降で、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスは、新しい get\<型 > この目的のためのメソッドをストリーム配信します。  
  
-   可能性のある大きな値を含む列が SELECT ステートメントで列の一覧に最後に配置されることを確認、get\<型 > のメソッドをストリーム、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)内の列にアクセスするため、選択された順序です。  
  
-   OUT 可能性のある大きな値を含むパラメーターは最後で宣言を作成するために使用する SQL のパラメーターの一覧で、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)です。 さらに、いることを確認、get\<型 > のメソッドをストリーム、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)宣言された順序で OUT パラメーターにアクセスするために使用します。  
  
-   同じ接続で複数のステートメントを同時に実行しないでください。 前のステートメントの結果を処理する前に別のステートメントを実行すると、処理されない結果がアプリケーションのメモリにバッファリングされることがあります。  
  
-   場合がありますを使用して、 **selectMethod = cursor**の代わりに**responseBuffering = adaptive**など、複数の利点があります。  
  
    -   読み取り専用の結果セットの一部のユーザー入力を使用して後各行を読み取るなどが遅い、処理される場合、アプリケーション、順方向専用、 **selectMethod = cursor**の代わりに**responseBuffering = adaptive**可能性がありますによるリソース使用量を減らす[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
    -   使用して、アプリケーションでは、2 つを処理するかより順方向専用、読み取り専用の結果セットを同じ接続で同時に場合、 **selectMethod = cursor**の代わりに**responseBuffering = adaptive**役立つ場合がありますこれらの結果セットの処理中に、ドライバーで必要なメモリの量を減らします。  
  
     どちらのケースも、サーバー カーソルを作成し、読み取って、閉じるという処理のオーバーヘッドを考慮する必要があります。  
  
 スクロール可能な結果セットと順方向専用の更新可能な結果セットの推奨事項を以下に補足します。  
  
-   スクロール可能な結果セットをフェッチする場合の行のブロック ドライバー常にメモリにによって示される行の数、 [getFetchSize](../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト、場合でも、アダプティブ バッファリングが有効になっているとします。 スクロール、OutOfMemoryError 発生すると、呼び出すことによってフェッチされた行の数を減らすことができます、 [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)フェッチ サイズを小さく行数に設定するオブジェクト必要な場合は、1 行にもダウンします。 これができない、OutOfMemoryError 場合、は、スクロール可能な結果セットで非常に大きな列を含むしないでください。  
  
-   順方向専用の更新可能な結果セットをフェッチする場合の行のブロック ドライバー通常メモリにによって示される行の数、 [getFetchSize](../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトアダプティブ バッファリングが有効な場合でも、接続でします。 呼び出す場合、[次](../../connect/jdbc/reference/next-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) 、OutOfMemoryError でオブジェクトの結果、呼び出すことによってフェッチされた行の数を減らすことができます、 [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md)メソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)必要な場合でも、行数を 1 までの行のより小さい数に、フェッチ サイズを設定するオブジェクト。 呼び出して、行のバッファリングがドライバーを強制することも、 [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトを"**アダプティブ**"の前にパラメーターステートメントを実行します。 結果セットは、アプリケーション、get のいずれかを使用して大きな列の値にアクセスする場合はスクロールできないため\<型 > Stream メソッドをドライバーは値を破棄、アプリケーションが読み取りは順方向専用の場合と同様とすぐに読み取り専用結果を設定します。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによるパフォーマンスと信頼性を向上させる](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  

