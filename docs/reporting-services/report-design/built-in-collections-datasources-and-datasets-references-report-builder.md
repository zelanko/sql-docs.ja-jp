---
title: "DataSources コレクションと DataSets コレクションの参照 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f951a4aa-da55-4e43-8579-4a5d4480d11f
caps.latest.revision: "7"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 557ea9ee2c43822c699d6c2d855d5ab6c1a980ea
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="built-in-collections---datasources-and-datasets-references-report-builder"></a>組み込みコレクション - DataSources と DataSets の参照 (レポート ビルダー)
  **DataSources** コレクションは、レポートで使用されているすべてのデータ ソースを表します。 同様に、 **DataSets** コレクションは、レポート内のすべてのデータ ソースのデータセットすべてを表します。 参照するデータ ソース別に構成されているレポート データセットの階層ビューを表示するには、 **[レポート データ]** ペインを使用します。 これらのコレクションへの参照を含めても、レポートをプレビューしたときには値が表示されません。 このコレクションを使用できるのは、レポートがレポート サーバーにパブリッシュされた後だけです。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="datasources"></a>DataSources  
 **DataSources** コレクションは、パブリッシュ済みレポート定義で参照されるデータ ソースを表します。 この情報をレポートに含め、レポート データのソースを説明することもできます。 このコレクションは、 **プレビュー** モードでは使用できません。 次の表では、 **DataSources** コレクション内の変数について説明します。  
  
|**変数**|**型**|**Description**|  
|------------------|--------------|---------------------|  
|**DataSourceReference**|**文字列**|レポート サーバー上のデータ ソース定義の完全パスです。 たとえば、レポートでレポート履歴の一部として使用されたすべてのデータ ソースの一覧を含める場合があります。 次の例では、AdventureWorks2012 という名前のデータ ソースの完全パスを示します。<br /><br /> `/DataSources/AdventureWorks2012`」を参照してください。|  
|**型**|**文字列**|データ ソースのデータ プロバイダーの種類です。 たとえば、 `SQL`のようにします。|  
  
## <a name="datasets"></a>DataSets  
 **DataSets** コレクションは、レポート定義で参照されるデータセットを表します。 レポートのクエリをテキスト ボックスに含めて、レポート内のデータに関心を持っているユーザーが元のコマンド テキストを参照できるようにすることもできます。 このコレクションは、 **プレビュー** モードでは使用できません。 次の表では、 **DataSets** コレクションのメンバーについて説明します。  
  
|**メンバー**|**型**|**Description**|  
|----------------|--------------|---------------------|  
|**CommandText**|**文字列**|データベース データ ソースの場合、これはデータ ソースからデータを取得するために使用するクエリです。 クエリが式の場合は、評価済みの式になります。|  
|**RewrittenCommandText**|**文字列**|データ プロバイダーの展開された CommandText 値。 これは通常、レポート パラメーターにマップされたクエリ パラメーターと共にレポートに使用されます。 コマンド テキスト パラメーター参照を、マップされたレポート パラメーターに対して選択された定数値に展開する場合、データ プロバイダーがこのプロパティを設定します。|  
  
### <a name="using-query-expressions"></a>クエリ式の使用  
 式を使用して、データセットに含まれているクエリを定義できます。 この機能を使用して、ユーザーからの入力や他のデータセットのデータ、その他の変数によりクエリが変化するようにレポートをデザインできます。 クエリについては、「[レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [式の例 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)  
  
  
