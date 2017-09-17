---
title: "プロシージャのサンプルが格納されていると大規模なデータを読み取る |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58c76635-a117-4661-8781-d6cb231c5809
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c3ec50f3fcff4098f8a5fe544b4f49b432455782
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="reading-large-data-with-stored-procedures-sample"></a>ストアド プロシージャで大きなデータを読み取るサンプル
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これは、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]サンプル アプリケーションは、ストアド プロシージャから大きな OUT パラメーターを取得する方法を示します。  
  
 このサンプルのコード ファイルは executeStoredProcedure.java という名前で、次の場所にあります。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \samples\adaptive  
  
## <a name="requirements"></a>必要条件  
 このサンプル アプリケーションを実行するにはアクセス許可が必要、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]サンプル データベース。 また、クラスパスの設定で sqljdbc.jar ファイルまたは sqljdbc4.jar ファイルを追加する必要があります。 クラスパスに sqljdbc.jar または sqljdbc4.jar のエントリがない場合、サンプル アプリケーションで "Class not found" という一般的な例外がスローされます。 クラスパスを設定する方法の詳細については、次を参照してください。 [JDBC ドライバーを使用して](../../../connect/jdbc/using-the-jdbc-driver.md)です。  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Sqljdbc.jar と sqljdbc4.jar な Java ランタイム環境 (JRE) 設定によって使用されるクラス ライブラリ ファイルを提供します。 選択する JAR ファイルの詳細については、次を参照してください。 [JDBC Driver のシステム要件](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)です。  
  
 次のストアド プロシージャを作成することも必要があります、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
CREATE PROCEDURE GetLargeDataValue   
  (@Document_ID int,   
   @Document_ID_out int OUTPUT,   
   @Document_Title varchar(50) OUTPUT,  
   @Document_Summary nvarchar(max) OUTPUT)  
  
AS   
BEGIN    
   SELECT @Document_ID_out = DocumentID,   
          @Document_Title = Title,  
          @Document_Summary = DocumentSummary   
    FROM  Production.Document  
    WHERE DocumentID = @Document_ID  
END  
```  
  
## <a name="example"></a>例  
 次の例では、サンプル コードへの接続、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]データベース。 次に、サンプル データを作成し、パラメーター化クエリを使用して Production.Document テーブルを更新します。 サンプル コードが使用して、アダプティブ バッファリング モードを取得し、 [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)クラスし、GetLargeDataValue ストアド プロシージャを実行します。 JDBC Driver Version 2.0 リリース以降では、responseBuffering 接続プロパティが既定で "adaptive" に設定されていることに注意してください。  
  
 最後に、サンプル コードは、OUT パラメーターで返されるデータを表示し、使用する方法も示します、`mark`と`reset`メソッドには、データの任意の部分を再読み込みします。  
  
 [!code[JDBC#UsingAdaptiveBuffering2](../../../connect/jdbc/codesnippet/Java/reading-large-data-with-_1_1.java)]  
  
## <a name="see-also"></a>参照  
 [大きなデータの処理](../../../connect/jdbc/working-with-large-data.md)  
  
  
