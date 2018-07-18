---
title: 既存の Analysis Services 表形式サーバーとデータベースへの接続 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 13900e4aaad52d39a2691fb40d0e419f55f660fc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38033392"
---
# <a name="connect-to-existing-analysis-services-tabular-server-and-database"></a>既存の Analysis Services 表形式サーバーとデータベースへの接続します。
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
SQL Server 2016 では、Analysis Services 管理オブジェクト (AMO) には、サーバー接続を設定するために使用するいくつかの名前空間が含まれています。 この記事より高い互換性レベルまたは Microsoft.AnalysisServices.Tabular 名前空間を使用して、モデル 1200 で作成されたデータベース用のサーバー接続を確立する方法について説明します。 

Analysis Services サーバーに接続するには、コードはサーバー オブジェクトをインスタンス化し、Connect メソッドを呼び出す必要があります。、 接続されると、サーバー オブジェクトのプロパティには、現在の Analysis Services インスタンスの設定が反映されます。 

次のクラスは、最上位レベルの接続に使用できます。 

* Microsoft.AnalysisServices.Server 
* Microsoft.AnalysisServices.Database 
* Microsoft.AnalysisServices.Tabular.Server 
* Microsoft.AnalysisServices.Tabular.Database 

2 つの名前空間がサーバーおよびデータベース オブジェクトへの接続を提供して、ご覧のとおり: AMO の元の Microsoft.AnalysisServices 名前空間および TOM の新しい Microsoft.AnalysisServices.Tabular 名前空間。

なぜ 2 つの名前空間と同じ操作のでしょうか。 その答は、ダウン ストリーム、データベースとモデルのレベルで、オブジェクト階層モード固有になり、モデル ツリーは多次元または表形式のいずれかのメタデータで構成されます。 モデル ツリーに呼び出しを行う、サーバーまたはデータベース オブジェクトは、両方のモデルの種類に対して提供されます。

> [!NOTE]  
>  モデルの定義と操作で使用されるメタデータは、2 つのモードに完全に異なります。 2 つの異なる名前空間には、データ定義言語 (DDL) を分離して、開発エクスペリエンスは、特定のモデル型に必要な API のみのプレゼンテーションを単純化されます。 

DDL が異なる場合は、サーバーへの接続は、同じすべてのモードのバージョンおよびエディション間で。 サーバーといずれかの名前空間を介したデータベース接続をサポートしている汎用ツールまたは任意の Analysis Services インスタンスに接続するスクリプトを記述することができますか、データベース、モデルの種類を知らなくてもサーバーでホストされて。  

このような柔軟性では、アセンブリ間の依存関係について説明します。 (表形式 1200 データベース内でモデルにはたとえば、またはキューブ、ディメンション、または多次元またはテーブル 1050 ~ 1103 データベース内のメジャー グループ上) は、データベース レベルの下の呼び出しを行うために AMO TOM に依存しています。 

これに対し、AMO では依存関係 TOM はありません。 TOM は、多次元メタデータ (キューブ) の詳細を使用することはできません、多次元と表形式メタデータの両方を探索する AMO を使用できます。 

このため、プロジェクトの設定の最初の手順では、すべての AMO アセンブリへの参照を追加する必要があります。 参照してください[TOM クライアント ライブラリを配布し、インストールして、参照](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md)詳細についてはします。 

> [!NOTE]  
>  サーバーとデータベースの接続は、MajorObject を継承するレガシ AMO クラスに基づいています。 表形式モデルのツリーで、メジャーおよびマイナー オブジェクトは使用されません、MajorObject クラスは、接続のセットアップを使用する API に関係なく、サーバーおよびデータベース オブジェクトの基本クラスとして表示です。  

## <a name="code-example-server-connection"></a>コード例: サーバー接続 

ローカルの Analysis Services インスタンスに接続し、コンソール ウィンドウでそのプロパティを一覧表示する方法を示す c# コード サンプルを次に示します。 

この例では、サーバー オブジェクトのプロパティの一部のみが、その他のプロパティを使用可能な ServerMode DefaultCompatibilityLevel などがあります。  

```
using System; 
using Microsoft.AnalysisServices.Tabular; 

namespace TOMSamples 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            // 
            // Connect to the local default instance of Analysis Services 
            // 
            string ConnectionString = "DataSource=localhost"; 


            // 
            // The using syntax ensures the correct use of the 
            // Microsoft.AnalysisServices.Tabular.Server object. 
            // 
            using (Server server = new Server()) 
            { 
                server.Connect(ConnectionString); 

 
                Console.WriteLine("Connection established successfully."); 
                Console.WriteLine(); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                Console.WriteLine("Server name:\t\t{0}", server.Name); 
                Console.WriteLine("Server product name:\t{0}", server.ProductName); 
                Console.WriteLine("Server product level:\t{0}", server.ProductLevel); 
                Console.WriteLine("Server version:\t\t{0}", server.Version); 
                Console.ResetColor(); 
                Console.WriteLine(); 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```
このプログラムを実行すると、出力は、コンソール ウィンドウ内のサーバー オブジェクトのプロパティを示します。 

## <a name="authentication-and-authorization"></a>認証と承認 

サーバーまたは Analysis Services へのデータベース接続、読み取り/書き込み操作と権限を借用した接続要求を通過の使用、管理アクセス許可が必要です。  

近年非常に特定の条件下でカスタム認証を許可する Analysis Services のセキュリティ インフラストラクチャが拡張され、唯一サポートされている外部認証メソッドで Windows 統合セキュリティが。 セキュリティ プリンシパルは、有効な Windows ドメイン ユーザー アカウントまたはグループ アカウントと見なされます。  

Windows 2012 以降、委任がドメイン間でフローさせることができます。 Analysis Services では、DirectQuery モデル以外の場合のみ委任を使用します。それ以外の場合、接続は、直接または権限を借用したです。 

## <a name="next-steps"></a>次のステップ 

接続を確立した後は、論理次の手順は、サーバー上に既に一覧か既存のデータベースには、か、おそらく新しい空のデータベースを作成します。 次のリンクには、両方の基本的なタスクを示すコード サンプルが含まれます。 

- [作成し、空のデータベースのデプロイ](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-and-deploy-an-empty-database-analysis-services-amo-tom.md)
- [既存のデータベースを一覧表示します。](../../analysis-services/tabular-model-programming-compatibility-level-1200/list-existing-databases-on-a-tabular-server-analysis-services-amo-tom.md)
