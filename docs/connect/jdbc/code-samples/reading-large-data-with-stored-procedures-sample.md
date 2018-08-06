---
title: ストアド プロシージャで大きなデータを読み取るサンプル | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 58c76635-a117-4661-8781-d6cb231c5809
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fcbeba3d535450001c15ab3168df9da59f7dceb2
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279034"
---
# <a name="reading-large-data-with-stored-procedures-sample"></a>ストアド プロシージャで大きなデータを読み取るサンプル
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] サンプル アプリケーションは、ストアド プロシージャから大きな OUT パラメーターを取得する方法を示しています。  
  
 このサンプルのコード ファイルは ExecuteStoredProcedure.java という名前で、次の場所にあります。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \samples\adaptive  
  
## <a name="requirements"></a>必要条件  
 このサンプル アプリケーションを実行するには、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] サンプル データベースへのアクセス権が必要です。 また mssql jdbc jar ファイルをインクルードするためのクラスパスを設定します。 クラスパスを設定する方法の詳細については、次を参照してください。 [JDBC ドライバーを使用して](../../../connect/jdbc/using-the-jdbc-driver.md)します。  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] には、必要な Java ランタイム環境 (JRE) 設定に応じて使用される mssql-jdbc クラス ライブラリ ファイルが用意されています。 選択する JAR ファイルの詳細については、次を参照してください。 [JDBC Driver のシステム要件](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)します。  
  
 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] サンプル データベースで次のストアド プロシージャを作成します。  
  
```sql
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
 次の例のサンプル コードでは、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] データベースへの接続を行います。 次に、サンプル データを作成し、パラメーター化クエリを使用して Production.Document テーブルを更新します。 さらに、[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) クラスの [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) メソッドを使用してアダプティブ バッファリング モードを取得し、GetLargeDataValue ストアド プロシージャを実行します。 JDBC Driver Version 2.0 リリース以降では、responseBuffering 接続プロパティが既定で "adaptive" に設定されていることに注意してください。  
  
 最後に、OUT パラメーターで返されたデータを表示します。また、ストリームに対して `mark` メソッドと `reset` メソッドを使用して、データの任意の部分を再度読み取る方法も示しています。  
  
 [!code[JDBC#UsingAdaptiveBuffering2](../../../connect/jdbc/codesnippet/Java/reading-large-data-with-_1_1.java)]  
  
## <a name="see-also"></a>参照  
 [大きなデータの処理](../../../connect/jdbc/working-with-large-data.md)  
  
  
