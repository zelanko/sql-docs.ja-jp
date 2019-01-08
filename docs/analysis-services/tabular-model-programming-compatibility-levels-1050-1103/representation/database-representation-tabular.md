---
title: データベース表現 (テーブル) |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 807e1f2c864f4e6574188e3f3d717e9bdf571c93
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52525670"
---
# <a name="database-representationtabular"></a>データベース表現 (テーブル)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  表形式モードでは、データベースは、表形式モデルのすべてのオブジェクトのコンテナーです。  
  
## <a name="database-representation"></a>データベース表現  
 データベースは、テーブル モデルを構成するすべてのオブジェクトが格納される場所です。 開発者は、データベースに含まれる、接続、テーブル、ロール、およびさらに多くのようなオブジェクトを検索します。  
  
### <a name="database-in-amo"></a>AMO 内のデータベース  
 AMO を使用してテーブル モデル データベースを管理する場合、AMO 内の <xref:Microsoft.AnalysisServices.Database> オブジェクトは、テーブル モデル内のデータベース論理オブジェクトと一対一で対応します。  
  
> [!NOTE]  
>  AMO 内でデータベース オブジェクトにアクセスするには、ユーザーがサーバー オブジェクトに対するアクセス権を得て、そこに接続する必要があります。  
  
### <a name="database-in-adomdnet"></a>ADOMD.Net 内のデータベース  
 ADOMD を使用してテーブル モデル データベースを参照してクエリを実行する場合は、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトを使用して、特定のデータベースへの接続を取得します。  
  
 次のコード スニペットを使用して、特定のデータベースに直接接続することができます。  
  
```csharp  
using ADOMD = Microsoft.AnalysisServices.AdomdClient;  
...  
   ADOMD.AdomdConnection currrentCnx = new ADOMD.AdomdConnection("Data Source=<<server\instance>>;Catalog=<<database>>");  
   currrentCnx.Open();  
...  
  
```  
  
 また、次のコード スニペットを使用すると、既存の接続オブジェクト (閉じられていないもの) を利用して、現在のデータベースを別のデータベースに変更することができます。  
  
```csharp  
currentCnx.ChangeDatabase("myOtherDatabase");  
  
```  
  
## <a name="database-in-amo"></a>AMO 内のデータベース  
 AMO を使用してデータベース オブジェクトを管理する場合は、<xref:Microsoft.AnalysisServices.Server> オブジェクトの作業を開始します。 その後、データベース コレクション内でデータベースを検索するか、コレクションに 1 つのデータベースを追加して新しいデータベースを作成します。  
  
 オンにした後、データベースが存在しない、次のコード スニペットが、サーバーに接続し、空のデータベースを作成する手順を示しています。  
  
```  
  
AMO.Server CurrentServer = new AMO.Server();  
try  
{  
    CurrentServer.Connect(currentServerName);  
}  
catch (Exception cnxException)  
{  
    MessageBox.Show(string.Format("Error while trying to connect to server: [{0}]\nError message: {1}", currentServerName, cnxException.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    return;  
}  
newDatabaseName = DatabaseName.Text;  
if (CurrentServer.Databases.Contains(newDatabaseName))  
{  
    return;  
}  
try  
{  
    AMO.Database newDatabase = CurrentServer.Databases.Add(newDatabaseName);  
  
    CurrentServer.Update();  
}  
catch (Exception createDBxc)  
{  
    MessageBox.Show(String.Format("Database [{0}] couldn't be created.\n{1}", newDatabaseName, createDBxc.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    newDatabaseAvailable = false;  
}  
  
```  
  
 AMO を使用して作成してデータベース表現を操作する方法については、実用的な理解 Tabular AMO 2012 サンプル; 内のソース コードを参照してください。具体的には、次のソース ファイルで確認します。Database.cs の内容に注意してください。 このサンプルは、Codeplex から入手できます。 サンプル コードは、ここで説明する論理的概念をサポートする目的でのみ提供されるものであり、運用環境では使用しないでください。  
  
  
