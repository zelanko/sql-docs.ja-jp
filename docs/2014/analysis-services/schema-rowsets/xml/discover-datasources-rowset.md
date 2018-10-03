---
title: DISCOVER_DATASOURCES 行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DISCOVER_DATASOURCES
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_DATASOURCES rowset
ms.assetid: f3ff26ab-a447-416b-ba54-1716df2283de
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 070fcc80266169753d98a8ca0673e748250556ae
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174412"
---
# <a name="discoverdatasources-rowset"></a>DISCOVER_DATASOURCES 行セット
  サーバーまたは Web サービスで使用できる XML for Analysis (XMLA) プロバイダー データ ソースの一覧を返します。 パブリッシュされたデータ ソースは、アプリケーション Web サーバーの URL から返されます。 クライアントは、この一覧内のいずれかのデータ ソースに接続できます。  
  
 呼び出す場合、 [Discover](../../xmla/xml-elements-methods-discover.md)メソッドを`DISCOVER_DATASOURCES`列挙値、 [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md)要素、`Discover`メソッドを返します。、`DISCOVER_DATASOURCES`行セット。  
  
 **適用対象:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 クライアントを設定してデータ ソースを選択する、`DataSourceInfo`プロパティ、[プロパティ](../../xmla/xml-elements-properties/properties-element-xmla.md)と共に送信される要素、[コマンド](../../xmla/xml-elements-properties/command-element-xmla.md)要素を[Execute](../../xmla/xml-elements-methods-execute.md)メソッド。 クライアントは、サーバーに送信する `DataSourceInfo` プロパティのコンテンツを作成するのではなく、 `Discover` メソッドを使用して、プロバイダーでサポートされているデータ ソースを見つける必要があります。 次に、クライアントは、`DataSourceInfo` 行セットから取得される `DISCOVER_DATASOURCES` プロパティに同じ値を返送します。  
  
 `DISCOVER_DATASOURCES`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|説明|  
|-----------------|--------------------|-----------------|-----------------|  
|`DataSourceName`|`DBTYPE_WSTR`|はい|`Adventure Works` などのデータ ソースの名前。|  
|`DataSourceDescription`|`DBTYPE_WSTR`||パブリッシャーによって入力されるデータ ソースの説明。<br /><br /> `NULL` を返す場合もあります。|  
|`URL`|`DBTYPE_WSTR`|はい|そのデータ ソースに対して XML for Analysis (XMLA) メソッドを呼び出す場所を示す一意のパス。<br /><br /> `NULL` を返す場合もあります。|  
|`DataSourceInfo`|`DBTYPE_WSTR`||データ ソースに接続するために必要な追加情報が含まれている文字列。<br /><br /> `NULL` を返す場合もあります。|  
|`ProviderName`|`DBTYPE_WSTR`|はい|データ ソースのプロバイダーの名前。<br /><br /> 例: `"MSOLAP"`<br /><br /> `NULL` を返す場合もあります。|  
|`ProviderType`|`DBTYPE_WSTR`|はい|プロバイダーによってサポートされているデータ型。 この配列には、次の 1 つまたは複数の型を含めることができます。<br /><br /> `MDP`: 多次元データ プロバイダー。<br /><br /> `TDP`: 表形式データ プロバイダー。<br /><br /> `DMP`: データ マイニング プロバイダー (OLE DB for Data Mining 仕様を実装)。|  
|`AuthenticationMode`|`DBTYPE_WSTR`|はい|データ ソースで使用するセキュリティ モードの種類の指定。 値は次のいずれかです。<br /><br /> `Unauthenticated`: ユーザー ID とパスワードを送信する必要はありません。<br /><br /> `Authenticated`: データ ソースに接続するために必要な情報にユーザー ID とパスワードを含める必要があります。<br /><br /> `Integrated`: データ ソースでは、権限を決定するために、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) によって提供される統合セキュリティなどの基になるセキュリティを使用します。|  
  
 このスキーマ行セットは並べ替えられません。  
  
> [!IMPORTANT]  
>  `DISCOVER_DATASOURCES` 行セットに対して、DMV クエリおよび SELECT コマンド構文を使用してクエリを実行することはできません。 ただし、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A> を使用して `DISCOVER_DATASOURCES` 行セットにクエリを実行することはできます。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|06c03d41-f66d-49f3-b1b8-987f7af4cf18|  
|ADOMDNAME|DataSources|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  
