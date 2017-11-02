---
title: "OPENROWSET (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENROWSET
dev_langs:
- DMX
helpviewer_keywords:
- OPENROWSET statement
ms.assetid: 8c8b61b4-2bf6-46c7-8976-51484004dc22
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 914e1be70255414373fd758301ef0682f3aba6e7
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="ltsource-data-querygt---openrowset"></a>&lt;ソース データ クエリ&gt;-OPENROWSET
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ソース データ クエリを外部プロバイダーへのクエリで置き換えます。 INSERT、SELECT FROM PREDICTION JOIN、および SELECT FROM NATURAL PREDICTION JOIN ステートメントをサポートして**OPENROWSET**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
OPENROWSET(provider_name,provider_string,query_syntax)  
```  
  
## <a name="arguments"></a>引数  
 *provider_name*  
 OLE DB プロバイダー名です。  
  
 *provider_string*  
 指定されたプロバイダーの OLE DB 接続文字列です。  
  
 *query_syntax*  
 行セットを返すクエリ構文です。  
  
## <a name="remarks"></a>解説  
 データ マイニング プロバイダーを使用して、データ ソース オブジェクトへの接続を確立する*provider_name*と*provider_string、*で指定されたクエリを実行して*query_syntax*をソース データから行セットを取得します。  
  
## <a name="examples"></a>使用例  
 次の例からデータを取得する、PREDICTION JOIN ステートメント内で使用できる、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]を使用してデータベースを[!INCLUDE[tsql](../includes/tsql-md.md)]SELECT ステートメント。  
  
```  
OPENROWSET  
(  
'SQLOLEDB.1',  
'Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security     Info=False;Initial Catalog=AdventureWorksDW2012;Data Source=localhost',  
'SELECT TOP 1000 * FROM vTargetMail'  
)  
```  
  
## <a name="see-also"></a>参照  
 [&#60;以外の場合はソース データ クエリ &#62;。](../dmx/source-data-query.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

