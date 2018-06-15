---
title: 既存の Analysis Services 表形式サーバーおよびデータベースへの接続 |Microsoft ドキュメント
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
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34040690"
---
# <a name="connect-to-existing-analysis-services-tabular-server-and-database"></a>既存の Analysis Services 表形式サーバーおよびデータベースへの接続します。
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
SQL Server 2016 では、Analysis Services 管理オブジェクト (AMO) には、サーバー接続を設定するために使用できるいくつかの名前空間が含まれています。 この記事より高い互換性レベル、またはモデルおよび 1200 で作成されたデータベースの Microsoft.AnalysisServices.Tabular 名前空間を使用してサーバー接続を確立する方法について説明します。 

Analysis Services サーバーに接続する場合、コードはサーバー オブジェクトをインスタンス化し、それで Connect メソッドを呼び出す必要があります。 接続されると、サーバー オブジェクトのプロパティには、現在の Analysis Services インスタンスの設定が反映されます。 

次のクラスは、最上位レベルの接続に使用できます。 

* Microsoft.AnalysisServices.Server 
* Microsoft.AnalysisServices.Database 
* Microsoft.AnalysisServices.Tabular.Server 
* Microsoft.AnalysisServices.Tabular.Database 

2 つの名前空間がサーバーおよびデータベース オブジェクトへの接続を提供することがわかります。 AMO での元の Microsoft.AnalysisServices 名前空間と TOM の新しいの Microsoft.AnalysisServices.Tabular 名前空間。

理由が同じ操作の 2 つの名前空間ですか? 答はダウン ストリーム、データベースとモデルのレベルで、ここで、オブジェクト階層モード固有になり、モデル ツリーは、Multidimensional または Tabular のいずれかのメタデータで構成されます。 モデル ツリーに呼び出しを行う、サーバーまたはデータベース オブジェクトは両方の種類のモデルの提供されます。

> [!NOTE]  
>  モデルの定義および操作で使用されるメタデータは、2 つのモードに完全に異なります。 2 つの異なる名前空間には、データ定義言語 (DDL) を分割することで、特定のモデル型に必要な API のみのプレゼンテーションを使って開発エクスペリエンスが簡略化されます。 

DDL が異なる場合は、サーバーへの接続が、同じすべてのモード、バージョンおよびエディション間でします。 サーバーといずれかの名前空間を介したデータベース接続をサポートする汎用ツールまたは任意の Analysis Services インスタンスに接続するスクリプトを記述することができますか、データベース、モデルの種類を知らなくても、サーバー上でホストします。  

この柔軟性は、アセンブリ間の依存関係について説明します。 データベース レベル (表形式 1200 データベース内にあるモデルで、またはキューブ、ディメンション、または、Multidimensional または Tabular 1050 ~ 1103 データベース内のメジャー グループ上) の下の呼び出しを行うために AMO TOM に依存しています。 

これに対し、AMO では依存関係 TOM はありません。 TOM は、多次元メタデータ (キューブ) を探索に使用することはできません、ですが、多次元と表形式メタデータの両方を探索する AMO を使用できます。 

このため、プロジェクトの設定の最初の手順では、すべての AMO のアセンブリへの参照を追加する必要があります。 参照してください[インストール、参照、および、TOM クライアント ライブラリを配布](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md)詳細についてはします。 

> [!NOTE]  
>  サーバーとデータベースの接続は、レガシ AMO から継承したクラス MajorObject に基づいています。 表形式モデル ツリーでメジャーおよびマイナー オブジェクトを使用していない MajorObject クラスは、接続のセットアップを使用する API に関係なく、サーバーおよびデータベース オブジェクトの基本クラスとして表示です。  

## <a name="code-example-server-connection"></a>コードの例: サーバー接続 

以下には、ローカル Analysis Services インスタンスに接続し、コンソール ウィンドウにそのプロパティを一覧表示する方法を示します (C#) コード サンプルを示します。 

この例では、サーバー オブジェクトのプロパティの一部のみが、その他のプロパティがある使用可能な ServerMode DefaultCompatibilityLevel など。  

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
このプログラムを実行すると、出力はコンソール ウィンドウでサーバー オブジェクトのプロパティを示します。 

## <a name="authentication-and-authorization"></a>認証と承認 

サーバーまたは Analysis Services への接続をデータベースには、読み取り/書き込み操作、および権限を借用した接続要求を通過の使用の管理アクセス許可が必要です。  

近年非常に特定の条件下でカスタム認証を許可する Analysis Services のセキュリティ インフラストラクチャが拡張され、唯一サポートされている外部の認証方法は Windows 統合セキュリティ。 セキュリティ プリンシパルは、有効な Windows ドメイン ユーザー アカウントまたはグループ アカウントと見なされます。  

Windows 2012 以降では、ドメイン間で委任をフローさせることができます。 Analysis Services で委任は DirectQuery モデルに対してのみ使用します。それ以外の場合、接続は、直接または偽装のいずれかです。 

## <a name="next-steps"></a>次の手順 

接続を確立するには後、論理次の手順は、サーバーに既に存在 ボックスの一覧か既存のデータベースには、または、おそらく新しい空のデータベースを作成します。 次のリンクには、両方の基本的なタスクを示すコード サンプルが含まれます。 

- [作成し、空のデータベースを配置](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-and-deploy-an-empty-database-analysis-services-amo-tom.md)
- [既存のデータベースを一覧表示します。](../../analysis-services/tabular-model-programming-compatibility-level-1200/list-existing-databases-on-a-tabular-server-analysis-services-amo-tom.md)
