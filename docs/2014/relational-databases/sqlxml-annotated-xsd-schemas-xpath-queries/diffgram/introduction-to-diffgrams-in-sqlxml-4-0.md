---
title: SQLXML 4.0 で Diffgram の概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- annotations [SQLXML]
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: 1902d67f-baf3-46e6-a36c-b24b5ba6f8ea
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 05f1374292eb3f1024c12519417ae872ffeb3734
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070478"
---
# <a name="introduction-to-diffgrams-in-sqlxml-40"></a>SQLXML 4.0 の DiffGram の概要
  ここでは、DiffGram の概要を説明します。  
  
## <a name="diffgram-format"></a>DiffGram の書式  
 一般的な DiffGram の書式は次のとおりです。  
  
```  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
   <DataInstance>  
      ...  
   </DataInstance>  
   [<diffgr:before>  
        ...  
   </diffgr:before>]  
  
   [<diffgr:errors>  
        ...  
   </diffgr:errors>]  
</diffgr:diffgram>  
```  
  
 DiffGram の書式は次のブロックで構成されています。  
  
 **\<DataInstance>**  
 この要素の名前**DataInstance**、このドキュメントでは説明のために使用します。 たとえば、.NET framework での値のデータセットから DiffGram を生成した場合、**名前**この要素の名前としてデータセットのプロパティを使用するとします。 このブロックには、変更後のすべての関連データを指定します。変更されていないデータも指定できます。 DiffGram の処理ロジックでは、このブロック内の要素を無視する、 **diffgr:hasChanges**属性が指定されていません。  
  
 **\<diffgr:before>**  
 省略可能なブロックです。更新または削除する必要がある元のレコード インスタンス (要素) を指定します。 変更 (更新または削除) されるすべてのデータベースのテーブルでは、DiffGram 必要がありますの最上位要素として表示されます、 **\<する前に >** ブロックします。  
  
 **\<diffgr:errors>**  
 省略可能なブロックです。DiffGram の処理ロジックでは無視されます。  
  
## <a name="diffgram-annotations"></a>DiffGram の注釈  
 これらの注釈は DiffGram 名前空間で定義されている **"urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}-diffgram-01"**:  
  
 **id**  
 この属性は内の要素のペアを使用、 **\<する前に >** と **\<DataInstance >** ブロックします。  
  
 **hasChanges**  
 挿入または更新操作では、DiffGram は、値は、この属性を指定する必要があります**挿入**または**変更**です。 この属性が存在しない場合、対応する要素で、  **\<DataInstance >** 処理では無視されますロジックや更新を実行します。 作業用サンプルについては、次を参照してください。 [DiffGram の例&#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md)です。  
  
 **parentID**  
 この属性は、DiffGram の要素間の親子リレーションシップを指定するときに使用します。 この属性にのみ表示されます、\<する前に > ブロックします。 この属性は更新の適用時に SQLXML で使用されます。 親子リレーションシップは、DiffGram の要素の処理順序を決定するために使用されます。  
  
## <a name="understanding-the-diffgram-processing-logic"></a>DiffGram の処理ロジックについて  
 DiffGram の処理ロジックでは、一定の規則に従い、挿入、更新、削除のうちどの操作であるかが判断されます。 次の表は、この規則についてまとめたものです。  
  
|演算|説明|  
|---------------|-----------------|  
|Insert|要素が表示されたら、DiffGram は挿入操作を示す、  **\<DataInstance >** ブロックではなく、対応する**\<する前に >** ブロック、および、 **diffgr:hasChanges**属性を指定する (**diffgr:hasChanges = 挿入**) 要素にします。 DiffGram で指定されているレコード インスタンスを挿入します。 ここでは、、  **\<DataInstance >** データベースにブロックします。<br /><br /> 場合、 **diffgr:hasChanges**属性が指定されていない、処理ロジックで、要素は無視され、挿入は実行されません。 作業用サンプルについては、次を参照してください。 [DiffGram の例&#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md)です。|  
|更新|内の要素がある場合、DiffGram は更新操作を示す、\<する前に > が対応する要素が存在するブロック、  **\<DataInstance >** ブロック (つまり、両方の要素である、 **diffgr:id**同じ値を持つ属性) と**diffgr:hasChanges**値を持つ属性が指定されて**変更**要素で、 **\<DataInstance >** ブロックします。<br /><br /> 場合、 **diffgr:hasChanges**属性が要素で指定されていない、  **\<DataInstance >** ブロック、処理ロジックで、エラーが返されます。 作業用サンプルについては、次を参照してください。 [DiffGram の例&#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md)です。<br /><br /> 場合**diffgr:parentID**で指定された、 **\<する前に >** ブロックで指定されている要素の親子リレーションシップ**parentID**で使用されますレコードが更新される順序を決定します。|  
|DELETE|要素が表示されたら、DiffGram は削除操作を示す、 **\<する前に >** ブロックではなく、対応する **\<DataInstance >** ブロックします。 DiffGram がで指定されているレコード インスタンスを削除するこの例では、 **\<する前に >** データベースからブロックされます。 作業用サンプルについては、次を参照してください。 [DiffGram の例&#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md)です。<br /><br /> 場合**diffgr:parentID**で指定された、 **\<する前に >** ブロックで指定されている要素の親子リレーションシップ**parentID**で使用されますレコードが削除される順序を決定します。|  
  
> [!NOTE]  
>  DiffGram にパラメーターを渡すことはできません。  
  
  