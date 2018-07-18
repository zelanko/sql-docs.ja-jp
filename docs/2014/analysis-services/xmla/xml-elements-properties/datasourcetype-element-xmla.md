---
title: DataSourceType 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DataSourceType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DataSourceType
- microsoft.xml.analysis.datasourcetype
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSourceType
helpviewer_keywords:
- DataSourceType element
ms.assetid: f5a348b1-911b-4139-832e-4bcb6d80a728
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c911f2a0e224cb8ccc9e7fa5b32a89a972fd1c26
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207672"
---
# <a name="datasourcetype-element-xmla"></a>DataSourceType 要素 (XMLA)
  示すかどうかを[場所](location-element-xmla.md)の指定された要素を[復元](../xml-elements-commands/restore-element-xmla.md)または[同期](../xml-elements-commands/synchronize-element-xmla.md)コマンドは、ローカルまたはリモート。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Location>  
   ...  
   <DataSourceType>...</DataSourceType>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*リモート*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[場所]](location-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `DataSourceType` 要素は、`Location` 要素によって定義されるデータ ソースにローカル データ ソースとリモート データ ソースのどちらが含まれるかを決定します。 バックアップおよびリモート パーティションを復元する詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*地元の*|`Location` 要素はローカル データ ソースを定義します。 この値を使用した場合、`Restore` および `Synchronize` コマンドは `Location` 要素で定義された情報を使用してデータ ソースを更新します。データ ソースは、`File` コマンドの `Backup` 要素で指定されたバックアップ ファイルから、あるいは `Source` コマンドの `Synchronize` 要素で指定されたデータベースから取得され、`DataSourceID` 要素の `Location` 要素で識別されます。<br /><br /> この値を使用すれば、リレーショナル OLAP (ROLAP) ストレージを使用するオブジェクトで、復元後または同期後に、データおよびメタデータ用に異なるデータベースを使用できます。 **注:** ディメンション テーブルや書き戻しテーブル内のデータなど、ROLAP データの復元または同期されていません。 ROLAP オブジェクトのメタデータだけが復元または同期されます。|  
|*リモート*|`Location` 要素はリモート データ ソースを定義します。 この値を使用した場合、`Restore` および `Synchronize` コマンドは、`Location` 要素で定義された情報を使用してリモート パーティションを復元または同期します。リモート パーティションは、`File` コマンドの `Backup` 要素で指定されたバックアップ ファイルから、あるいは `Source` コマンドの `Synchronize` 要素で指定されたデータベースから取得され、復元先または同期先リモート インスタンスは `DataSourceID` 要素の `Location` で識別されます。|  
  
## <a name="see-also"></a>参照  
 [ConnectionString 要素&#40;XMLA&#41;](connectionstring-element-xmla.md)   
 [DataSourceID 要素&#40;XMLA&#41;](id-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
