---
title: GEOMETRY、GEOGRAPHY、および HIERARCHYID のクライアント側の使用状況についての警告 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 500ee6b3-2154-45d2-a3cf-8760166d9413
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 02748f9dca8e4f9f29c7c94658d2a4068b1ba65e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177448"
---
# <a name="warning-about-client-side-usage-of-geometry-geography-and-hierarchyid"></a>幾何学、地理学、HIERARCHYID のクライアント側の使用に関する警告
  アセンブリ**Microsoft.SqlServer.Types.dll**、バージョン 11.0 に、バージョン 10.0 からアップグレードされたが、空間データ型が含まれています。 このアセンブリを参照するカスタム アプリケーションは、特定の条件に該当する場合に失敗します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 アセンブリ**Microsoft.SqlServer.Types.dll**、バージョン 11.0 に、バージョン 10.0 からアップグレードされたが、空間データ型が含まれています。 このアセンブリを参照するカスタム アプリケーションは、次の条件に該当する場合に失敗します。  
  
-   移動すると、カスタム アプリケーション、コンピューターを[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]のみいるコンピューターにインストールされた[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]がインストールされているアプリケーションは失敗ための参照されるバージョン 10.0、 **SqlTypes**アセンブリ存在しません。 この場合、次のエラー メッセージが返されることがあります: `“Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified.”`  
  
-   参照するとき、 **SqlTypes**アセンブリ バージョン 11.0、バージョン 10.0 もインストールし、このエラー メッセージを表示することがあります。 `“System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'.”`  
  
-   参照する場合、 **SqlTypes**アセンブリ バージョン 11.0 を .NET 3.5、4、または 4.5 を対象とするカスタム アプリケーションから、アプリケーションが失敗 SqlClient が仕様によってバージョン 10.0 のアセンブリを読み込むためです。 このエラーは、アプリケーションが次のいずれかのメソッドを呼び出したときに発生します。  
  
    -   `GetValue` クラスの `SqlDataReader` メソッド  
  
    -   `GetValues` クラスの `SqlDataReader` メソッド  
  
    -   `SqlDataReader` クラスの角かっこインデックス演算子 []  
  
    -   `ExecuteScalar` クラスの `SqlCommand` メソッド  
  
## <a name="corrective-action"></a>修正措置  
 この問題は、次のいずれかの方法を使用して回避できます。  
  
-   この問題を回避するには、コード内で、上にリストされている Get メソッドの代わりに `GetSqlBytes` メソッドを呼び出して、CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム型を取得します。次に例を示します。  
  
    ```csharp  
    string query = "SELECT [SpatialColumn] FROM [SpatialTable]";  
          using (SqlConnection conn = new SqlConnection("..."))  
          {  
                SqlCommand cmd = new SqlCommand(query, conn);  
  
                conn.Open();  
                SqlDataReader reader = cmd.ExecuteReader();  
  
                while (reader.Read())  
                {  
                      // In version 11.0 only  
                      SqlGeometry g =   
    SqlGeometry.Deserialize(reader.GetSqlBytes(0));  
  
                      // In version 10.0 or 11.0  
                      SqlGeometry g2 = new SqlGeometry();  
                      g.Read(new BinaryReader(reader.GetSqlBytes(0).Stream));  
                }  
          }  
    ```  
  
-   この問題を回避するには、アプリケーション構成ファイル内でアセンブリのリダイレクトを使用します。次に例を示します。  
  
    ```xml  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
        ...  
        <dependentAssembly>  
            <assemblyIdentity name="Microsoft.SqlServer.Types" publicKeyToken="89845dcd8080cc91" culture="neutral" />  
            <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />  
        </dependentAssembly>  
        ...  
    </assemblyBinding>  
    ```  
  
-   この問題を回避するには、接続文字列内で、"Type System Version" 属性の値を "SQL Server 2012" と指定することにより、SqlClient がバージョン 11.0 のアセンブリを読み込むようにします。 この接続文字列属性は、.NET 4.5 以上でのみ使用可能です。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
