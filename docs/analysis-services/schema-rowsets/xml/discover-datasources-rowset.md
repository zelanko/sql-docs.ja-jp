---
title: "DISCOVER_DATASOURCES 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DISCOVER_DATASOURCES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_DATASOURCES rowset
ms.assetid: f3ff26ab-a447-416b-ba54-1716df2283de
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d52c95835c5583bd4b8a01a416131aaa7166f385
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="discoverdatasources-rowset"></a>DISCOVER_DATASOURCES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]XML for Analysis (XMLA) プロバイダー データ ソースは、サーバーまたは Web サービスで使用できるの一覧を返します。 パブリッシュされたデータ ソースは、アプリケーション Web サーバーの URL から返されます。 クライアントは、この一覧内のいずれかのデータ ソースに接続できます。  
  
 呼び出す場合は、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドを**DISCOVER_DATASOURCES**の列挙値に、 [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md)要素、 **Discover**メソッドを返します、 **DISCOVER_DATASOURCES**行セット。  
  
 **適用されます:**表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 クライアントでは、データ ソースを選択するには、 **DataSourceInfo**プロパティに、[プロパティ](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)と共に送信される要素、[コマンド](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)要素を[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。 クライアントの内容を作成する必要があります、 **DataSourceInfo**プロパティをサーバーに送信します。 代わりに、クライアントが使用する必要があります、 **Discover**プロバイダーは、サポートされるデータ ソースを検索するメソッド。 クライアントを送り返します同じ値**DataSourceInfo**プロパティから取得した、 **DISCOVER_DATASOURCES**行セット。  
  
 **DISCOVER_DATASOURCES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**データ ソース名**|**DBTYPE_WSTR**|可|データ ソースの名前など**Adventure Works**です。|  
|**DataSourceDescription**|**DBTYPE_WSTR**||パブリッシャーによって入力されるデータ ソースの説明。<br /><br /> 返す可能性があります**NULL**です。|  
|**[URL]**|**DBTYPE_WSTR**|可|そのデータ ソースに対して XML for Analysis (XMLA) メソッドを呼び出す場所を示す一意のパス。<br /><br /> 返す可能性があります**NULL**です。|  
|**DataSourceInfo**|**DBTYPE_WSTR**||データ ソースに接続するために必要な追加情報が含まれている文字列。<br /><br /> 返す可能性があります**NULL**です。|  
|**ProviderName**|**DBTYPE_WSTR**|可|データ ソースのプロバイダーの名前。<br /><br /> 例: `"MSOLAP"`<br /><br /> 返す可能性があります**NULL**です。|  
|**プロバイダーの種類**|**DBTYPE_WSTR**|可|プロバイダーによってサポートされているデータ型。 この配列には、次の 1 つまたは複数の型を含めることができます。<br /><br /> **MDP**: 多次元データ プロバイダー。<br /><br /> **TDP**: 表形式のデータ プロバイダー。<br /><br /> **DMP**: データ マイニング プロバイダー (を実装して、OLE db for Data Mining 仕様)。|  
|**AuthenticationMode**|**DBTYPE_WSTR**|可|データ ソースで使用するセキュリティ モードの種類の指定。 値は次のいずれかです。<br /><br /> **認証されていない**: 送信するユーザー ID またはパスワードを持たない。<br /><br /> **認証**: データ ソースへの接続に必要な情報では、ユーザー ID とパスワードを含める必要があります。<br /><br /> **統合型**: データ ソースによって提供される統合セキュリティなどの承認を決定する、基になるセキュリティを使用して[!INCLUDE[msCoName](../../../includes/msconame-md.md)]インターネット インフォメーション サービス (IIS)。|  
  
 このスキーマ行セットは並べ替えられません。  
  
> [!IMPORTANT]  
>  **DISCOVER_DATASOURCES** DMV クエリおよび SELECT コマンド構文を使用して行セットをクエリすることはできません。 ただし、 **DISCOVER_DATASOURCES**を使用してクエリできる行セット<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>です。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|06c03d41-f66d-49f3-b1b8-987f7af4cf18|  
|ADOMDNAME|DataSources|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
