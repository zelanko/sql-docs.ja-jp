---
title: "ADOMD.NET クライアント機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: 0f5e16a1-dc2d-4c87-8551-985921bf069b
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 0a1047fbccf3e9437c3160891f502f9e2838c34a
ms.contentlocale: ja-jp
ms.lasthandoff: 10/24/2017

---
# <a name="adomdnet-client-functionality"></a>ADOMD.NET のクライアント機能
  ADOMD.NET は、他の [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework データ プロバイダーと同様、アプリケーションとデータ ソースの間の仲介役となります。 ただし、分析データを扱うという点で、他の .NET Framework データ プロバイダーとは異なります。 分析データを操作する ADOMD.NET では、サポートされている機能が他の .NET Framework データ プロバイダーとは大きく違っています。 データを取得するだけでなく、メタデータを取得したり、分析データ ストアの構造を変更したりすることができます。  
  
 **メタデータの取得**  
 スキーマ行セットまたはオブジェクト モデルを使用してメタデータを取得することにより、データ ソースから取得できるデータについてアプリケーションでより多くの情報を得ることができます。 たとえば、利用可能な各主要業績評価指標 (KPI) の型、キューブのディメンション、マイニング モデルで必要とされるパラメーターなどの情報を入手できます。 メタデータは、最も重要な*動的*を取得するには、型、深さ、およびデータのスコープを決定するユーザー入力を必要とするアプリケーション。 たとえば、クエリ アナライザー、Microsoft Excel、その他のクエリ ツールがこれに該当します。 メタデータを重要度の低い*静的*定義済みの一連の操作を実行するアプリケーション。  
  
 詳細については:[分析データ ソースからメタデータを取得する](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)です。  
  
 **データの取得**  
 データの取得とは、データ ソースに格納されている情報を実際に取得することです。 データ ソースの構造がわかっている "静的" アプリケーションでは、データの取得が主要な機能になります。 また、データの取得は "動的" アプリケーションの最終結果でもあります。 たとえば、特定の時刻の KPI の値、この 1 時間の間に各店舗で販売された自転車の数、従業員の年間の業績を左右する要因などのデータを取得できます。 データの取得は、クエリを実行するすべてのアプリケーションにとって不可欠です。  
  
 詳細については:[分析データ ソースからのデータの取得](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md)です。  
  
 **分析データの構造を変更します。**  
 ADOMD.NET を使用すると、分析データ ストアの構造を実際に変更することもできます。 この操作は、分析管理オブジェクト (AMO) オブジェクト モデルを通じて行われるのが一般的ですが、ADOMD.NET を使用すると、Analysis Services Scripting Language (ASSL) コマンドを送信してサーバーのオブジェクトを作成、変更、または削除できます。  
  
 詳細については:[を実行するコマンドに対して、分析データ ソース](../../analysis-services/multidimensional-models-adomd-net-client/executing-commands-against-an-analytical-data-source.md)、[分析管理オブジェクト &#40; を使用した開発AMO &#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)、 [Analysis Services スクリプト言語 & #40 です。ASSL を XMLA &#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)  
  
 メタデータの取得、データの取得、およびデータ構造の変更は、それぞれ一般的な ADOMD.NET アプリケーションのワークフローの特定の段階で行われます。  
  
## <a name="typical-process-flow"></a>一般的な処理フロー  
 通常の ADOMD.NET アプリケーションは、一般に、次に示す同じワークフローに従って分析データベースを操作します。  
  
1.  最初に、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトを使用してデータベースへの接続を確立します。 接続を開くと、接続先サーバーに関するメタデータが <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトによって公開されます。 動的アプリケーションでは、この情報の一部がユーザーに表示されて、クエリを実行するキューブなどをユーザーが選択できるようになるのが一般的です。 このステップで作成された接続は、アプリケーションで繰り返し利用できます。これにより、オーバーヘッドが軽減されます。  
  
     詳細については: [ADOMD.NET で接続を確立します。](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)  
  
2.  接続が確立されると、動的アプリケーションは、サーバーに対してより詳細なメタデータを問い合わせます。 静的アプリケーションの場合は、アプリケーションによるクエリの対象となるオブジェクトがあらかじめわかっているため、このメタデータを取得する必要はありません。 取得したメタデータは、アプリケーションやユーザーが次のステップで使用できます。  
  
     詳細については:[分析データ ソースからメタデータを取得します。](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
3.  次に、アプリケーションはサーバーに対してコマンドを実行します。 追加のメタデータの取得、データの取得、データベースの構造の変更などのためのコマンドを実行できます。 いずれの場合も、アプリケーションであらかじめ決められたクエリを使用することも、新たに取得したメタデータを使用して追加のクエリを作成することもできます。  
  
     詳細については:[分析データ ソースからメタデータを取得する](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)、[分析データ ソースからのデータの取得](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md)、[を実行するコマンドに対して、分析データ ソース](../../analysis-services/multidimensional-models-adomd-net-client/executing-commands-against-an-analytical-data-source.md)  
  
4.  コマンドがサーバーに送信されると、メタデータやデータをクライアントに返す処理がサーバーで開始されます。 使用してこの情報を表示することができます、<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>オブジェクト、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>オブジェクト、または**System.XmlReader**オブジェクト。  
  
 次の例は、この一般的なワークフローを示しています。この例に含まれているメソッドは、データベースへの接続を開き、既知のキューブに対してコマンドを実行し、結果をセルセットに取得します。 このセルセットは、列ヘッダー、行ヘッダー、およびセル データを含むタブ区切りの文字列を返します。  
  
 [!code-cs[Adomd.NetClient#ReturnCommandUsingCellSet](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/adomd-net-client-functio_1.cs)]  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET クライアント プログラミング](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  

