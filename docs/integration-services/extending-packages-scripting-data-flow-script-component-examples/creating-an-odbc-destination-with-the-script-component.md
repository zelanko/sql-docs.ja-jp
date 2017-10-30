---
title: "スクリプト コンポーネントによる ODBC 変換先を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], destination components
- ODBC destination [Integration Services]
- destinations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: d198c866-78f4-4a50-ae15-333160645815
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5eb539f0d18f473b10ed8d49bcee9c298292fb41
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="creating-an-odbc-destination-with-the-script-component"></a>スクリプト コンポーネントによる ODBC 変換先の作成
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、通常データを保存する odbc 入力先を使用して、[!INCLUDE[vstecado](../../includes/vstecado-md.md)]変換先、および[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]Data Provider for ODBC です。 ただし、単一のパッケージで使用するアドホックな ODBC 変換先を作成することもできます。 このアドホックな ODBC 変換先を作成するには、次の例に示すように、スクリプト コンポーネントを使用します。  
  
> [!NOTE]  
>  複数のデータ フロー タスクおよび複数のパッケージでより簡単に再利用できるコンポーネントを作成する場合は、このスクリプト コンポーネント サンプルのコードを基にした、カスタム データ フロー コンポーネントの作成を検討してください。 詳細については、「 [カスタム データ フロー コンポーネントの開発](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例で、既存の ODBC を使用する変換先コンポーネントにデータ フローのデータを保存する接続マネージャーを作成する方法、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。  
  
 この例は、カスタムの変更済みバージョン[!INCLUDE[vstecado](../../includes/vstecado-md.md)]」で示した先[スクリプト コンポーネントによる変換先の作成](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)です。 ただし、この例のカスタムの [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 変換先は、ODBC 接続マネージャーを使用してデータを ODBC 変換先に保存するように変更されています。 こうした変更には、次の変更も含まれています。  
  
-   呼び出すことはできません、 **AcquireConnection**メソッドから ODBC 接続マネージャーのマネージ コード、ネイティブ オブジェクトを返すためです。 そのため、この例では、接続マネージャーの接続文字列を使用して、マネージ ODBC [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーで直接データ ソースに接続しています。  
  
-   **OdbcCommand**位置指定パラメーターが必要です。 パラメーターの位置は、コマンドのテキストの疑問符 (?) で示されます  (これに対し、 **SqlCommand**名前付きパラメーターが必要です)。  
  
 この例では、 **Person.Address**テーブルに、 **AdventureWorks**サンプル データベース。 例では、最初と 4 番目の列に渡します、  **int*AddressID** * と**nvarchar (30) 市区町村**をデータ フローには、このテーブルの列です。 この同じデータが変換元、変換、および、トピック「変換先の例で使用される[スクリプト コンポーネント種類特定の開発](../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)です。  
  
#### <a name="to-configure-this-script-component-example"></a>このスクリプト コンポーネントの例を構成するには  
  
1.  ODBC 接続接続マネージャーを作成する、 **AdventureWorks**データベース。  
  
2.  次の TRANSACT-SQL コマンドを実行して、変換先テーブルを作成、 **AdventureWorks**データベース。  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換先として構成します。  
  
4.  [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで、上流変換元の出力または変換の出力を変換先コンポーネントに接続します  (変換を介さずに変換元を直接変換先に接続することもできます)。このサンプルは、動作は、上流コンポーネントの出力に含める必要がありますには、少なくとも、 **AddressID**と**市区町村**からの列、 **Person.Address**のテーブル、 **AdventureWorks**サンプル データベース。  
  
5.  開く、**スクリプト変換エディター**です。 **入力列**] ページで、[、 **AddressID**と**市区町村**列です。  
  
6.  **入力と出力**などわかりやすい名前を持つ、入力の名前を変更 ページで、 **MyAddressInput**です。  
  
7.  **接続マネージャー**ページで追加するか、ODBC 接続マネージャーを作成、わかりやすい名前を持つよう**MyODBCConnectionManager**です。  
  
8.  **スクリプト** ページで、をクリックして**スクリプトの編集**、次に示すスクリプトを入力し、 **ScriptMain**クラスです。  
  
9. 閉じるスクリプト開発環境を閉じて、**スクリプト変換エディター**、サンプルを実行します。  
  
    ```vb  
    Imports System.Data.Odbc  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Dim odbcConn As OdbcConnection  
        Dim odbcCmd As OdbcCommand  
        Dim odbcParam As OdbcParameter  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            Dim connectionString As String  
            connectionString = Me.Connections.MyODBCConnectionManager.ConnectionString  
            odbcConn = New OdbcConnection(connectionString)  
            odbcConn.Open()  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
  
            odbcCmd = New OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
                "VALUES(?, ?)", odbcConn)  
            odbcParam = New OdbcParameter("@addressid", OdbcType.Int)  
            odbcCmd.Parameters.Add(odbcParam)  
            odbcParam = New OdbcParameter("@city", OdbcType.NVarChar, 30)  
            odbcCmd.Parameters.Add(odbcParam)  
  
        End Sub  
  
        Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
            With odbcCmd  
                .Parameters("@addressid").Value = Row.AddressID  
                .Parameters("@city").Value = Row.City  
                .ExecuteNonQuery()  
            End With  
  
        End Sub  
  
        Public Overrides Sub ReleaseConnections()  
  
            odbcConn.Close()  
  
        End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System.Data.Odbc;  
    ...  
    public class ScriptMain :  
        UserComponent  
    {  
        OdbcConnection odbcConn;  
        OdbcCommand odbcCmd;  
        OdbcParameter odbcParam;  
  
        public override void AcquireConnections(object Transaction)  
        {  
  
            string connectionString;  
            connectionString = this.Connections.MyODBCConnectionManager.ConnectionString;  
            odbcConn = new OdbcConnection(connectionString);  
            odbcConn.Open();  
  
        }  
  
        public override void PreExecute()  
        {  
  
            odbcCmd = new OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " +  
                "VALUES(?, ?)", odbcConn);  
            odbcParam = new OdbcParameter("@addressid", OdbcType.Int);  
            odbcCmd.Parameters.Add(odbcParam);  
            odbcParam = new OdbcParameter("@city", OdbcType.NVarChar, 30);  
            odbcCmd.Parameters.Add(odbcParam);  
  
        }  
  
        public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
        {  
  
            {  
                odbcCmd.Parameters["@addressid"].Value = Row.AddressID;  
                odbcCmd.Parameters["@city"].Value = Row.City;  
                odbcCmd.ExecuteNonQuery();  
            }  
  
        }  
  
        public override void ReleaseConnections()  
        {  
  
            odbcConn.Close();  
  
        }  
    }  
    ```  
  
## <a name="see-also"></a>参照  
 [スクリプト コンポーネントによる変換先の作成](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
  
  

