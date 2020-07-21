---
title: OPENROWSET (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 125fe829c3b76be0d92a3519249df571890efbf2
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670023"
---
# <a name="ltsource-data-querygt---openrowset"></a>&lt;ソースデータクエリ &gt; -OPENROWSET
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  ソースデータクエリをクエリに置き換えます。 INSERT、SELECT FROM 予測結合、および SELECT FROM ナチュラル予測結合ステートメントでは、 **OPENROWSET**がサポートされています。  
  
## <a name="syntax"></a>構文  
  
```  
  
OPENROWSET(provider_name,provider_string,query_syntax)  
```  
  
## <a name="arguments"></a>引数  
 *provider_name*  
 OLE DB プロバイダー名。  
  
 *provider_string*  
 指定したプロバイダーの OLE DB 接続文字列。  
  
 *query_syntax*  
 行セットを返すクエリ構文です。  
  
## <a name="remarks"></a>Remarks  
 データマイニングプロバイダーは、 *provider_name*と*provider_string*を使用してデータソースオブジェクトへの接続を確立し、 *query_syntax*で指定されたクエリを実行して、ソースデータから行セットを取得します。  
  
## <a name="examples"></a>例  
 次の例は、予測結合ステートメント内で、SELECT ステートメントを使用してデータベースからデータを取得するために使用でき [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] ます。  
  
```  
OPENROWSET  
(  
'SQLOLEDB.1',  
'Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security     Info=False;Initial Catalog=AdventureWorksDW2012;Data Source=localhost',  
'SELECT TOP 1000 * FROM vTargetMail'  
)  
```  
  
## <a name="see-also"></a>参照  
 [&#60;ソースデータクエリ&#62;](../dmx/source-data-query.md)   
 [DMX&#41; データ操作ステートメントを &#40;データマイニング拡張機能](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
