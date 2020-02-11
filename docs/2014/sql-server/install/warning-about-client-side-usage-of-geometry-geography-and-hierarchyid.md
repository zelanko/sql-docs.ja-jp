---
title: GEOMETRY、GEOGRAPHY、および HIERARCHYID のクライアント側での使用に関する警告Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 500ee6b3-2154-45d2-a3cf-8760166d9413
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 524400e9c9420fb54447220215d4660874ec6d69
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091089"
---
# <a name="warning-about-client-side-usage-of-geometry-geography-and-hierarchyid"></a>幾何学、地理学、HIERARCHYID のクライアント側の使用に関する警告
  空間データ型を含むアセンブリ**Microsoft. SqlServer. .dll**は、バージョン10.0 からバージョン11.0 にアップグレードされました。 このアセンブリを参照するカスタム アプリケーションは、特定の条件に該当する場合に失敗します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>[説明]  
 空間データ型を含むアセンブリ**Microsoft. SqlServer. .dll**は、バージョン10.0 からバージョン11.0 にアップグレードされました。 このアセンブリを参照するカスタム アプリケーションは、次の条件に該当する場合に失敗します。  
  
-   がインストールされているコンピューター [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]から、がインストールされているコンピューターにカスタムアプリケーションを移動すると、参照されているバージョン10.0 の**SqlTypes**アセンブリが存在しないため、アプリケーションは失敗します。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] この場合、次のエラー メッセージが返されることがあります: `"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`  
  
-   **SqlTypes**アセンブリバージョン11.0 を参照するときに、バージョン10.0 もインストールされていると、次のエラーメッセージが表示されることがあります。`"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`  
  
-   .NET 3.5、4、または4.5 を対象とするカスタムアプリケーションから**SqlTypes**アセンブリバージョン11.0 を参照する場合、アプリケーションは失敗します。これは、の仕様では、アセンブリのバージョン10.0 が読み込まれるためです。 このエラーは、アプリケーションが次のいずれかのメソッドを呼び出したときに発生します。  
  
    -   
  `GetValue` クラスの `SqlDataReader` メソッド  
  
    -   
  `GetValues` クラスの `SqlDataReader` メソッド  
  
    -   
  `SqlDataReader` クラスの角かっこインデックス演算子 []  
  
    -   
  `ExecuteScalar` クラスの `SqlCommand` メソッド  
  
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
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md
)  
  
  
