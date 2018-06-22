---
title: 選択的セカンダリ XML インデックスの作成、変更、および削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45128105-833b-40a9-9cc9-1ae03ac0b52b
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 805dc8effdbd93ddddb81dde4203fff7e808cd36
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084917"
---
# <a name="create-alter-and-drop-secondary-selective-xml-indexes"></a>選択的セカンダリ XML インデックスの作成、変更、および削除
  新しい選択的セカンダリ XML インデックスの作成や、既存の選択的セカンダリ XML インデックスの変更または削除を行う方法について説明します。  
  
##  <a name="create"></a> 選択的セカンダリ XML インデックスの作成  
  
### <a name="how-to-create-a-secondary-selective-xml-index"></a>選択的セカンダリ XML インデックスを作成する方法  
 **Transact-SQL を使用して選択的セカンダリ XML インデックスを作成する**  
 CREATE SELECTIVE XML INDEX ステートメントを呼び出して選択的セカンダリ XML インデックスを作成します。 詳細については、次を参照してください。 [CREATE XML INDEX&#40;選択的 XML インデックス&#41;] (~/t-sql/statements/create-xml-index-selective-xml-indexes です。  
  
 **例**  
  
 次の例では、パス `'pathabc'`に選択的セカンダリ XML インデックスを作成します。 インデックスを作成するパスは、作成時に CREATE SELECTIVE XML INDEX ステートメントで指定された名前によって識別されます。 詳細については、「[CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql)」を参照してください。  
  
```tsql  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="alter"></a> 選択的セカンダリ XML インデックスの変更  
 ALTER ステートメントは、選択的セカンダリ XML インデックスではサポートされません。 選択的セカンダリ XML インデックスを変更するには、既存のインデックスを削除し、再作成します。  
  
### <a name="how-to-alter-a-secondary-selective-xml-index"></a>選択的セカンダリ XML インデックスを変更する方法  
 **Transact-SQL を使用して選択的セカンダリ XML インデックスを変更する**  
 1.  DROP INDEX ステートメントを呼び出して既存の選択的セカンダリ XML インデックスを削除します。 詳細については、「[DROP INDEX &#40;選択的 XML インデックス&#41;](../indexes/indexes.md)」を参照してください。  
  
2.  CREATE XML INDEX ステートメントを呼び出すことによって必要なオプションのインデックスを再作成します。 詳細については、次を参照してください。 [CREATE XML INDEX&#40;選択的 XML インデックス&#41;] (~/t-sql/statements/create-xml-index-selective-xml-indexes です。  
  
 **例**  
  
 次の例では、インデックスを削除して再作成することにより、選択的セカンダリ XML インデックスを変更します。  
  
```tsql  
DROP INDEX filt_sxi_index_c  
  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="drop"></a> 選択的セカンダリ XML インデックスの削除  
  
### <a name="how-to-drop-a-secondary-selective-xml-index"></a>選択的セカンダリ XML インデックスを削除する方法  
 **Transact-SQL を使用して選択的セカンダリ XML インデックスを削除する**  
 DROP INDEX ステートメントを呼び出して選択的セカンダリ XML インデックスを削除します。 詳細については、「[DROP INDEX &#40;選択的 XML インデックス&#41;](../indexes/indexes.md)」を参照してください。  
  
 **例**  
  
 DROP INDEX ステートメントの例を次に示します。  
  
```tsql  
DROP INDEX ssxi_index  
ON tbl  
```  
  
  
## <a name="see-also"></a>参照  
 [選択的 XML インデックス &#40;SXI&#41;](selective-xml-indexes-sxi.md)  
  
  
