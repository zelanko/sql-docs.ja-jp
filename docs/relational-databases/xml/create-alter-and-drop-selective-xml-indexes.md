---
title: 選択的 XML インデックスの作成、変更、および削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: c398f396-f630-4a2d-a264-f243c5346de1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 87cdcddb9e797e640dd172067bab2e0632aef656
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664663"
---
# <a name="create-alter-and-drop-selective-xml-indexes"></a>選択的 XML インデックスの作成、変更、および削除
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  新しい選択的 XML インデックスの作成や、既存の選択的 XML インデックスの変更または削除を行う方法について説明します。  
  
 選択的 XML インデックスの詳細については、「 [選択的 XML インデックス &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)」を参照してください。  
  
##  <a name="creating-a-selective-xml-index"></a><a name="create"></a> 選択的 XML インデックスの作成  
  
### <a name="how-to-create-a-selective-xml-index"></a>方法: 選択的 XML インデックスを作成する  
 **Transact-SQL を使用して選択的 XML インデックスを作成する**  
 CREATE SELECTIVE XML INDEX ステートメントを呼び出して選択的 XML インデックスを作成します。 詳細については、「[CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md)」を参照してください。  
  
 **例**  
  
 次の例では、選択的 XML インデックスを作成するための構文を示しています。 また、インデックスを作成するパスと省略可能な最適化ヒントを指定する構文のいくつかのバリエーションを示します。  
  
```sql  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()'  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
)  
```  
  
  
##  <a name="altering-a-selective-xml-index"></a><a name="alter"></a> 選択的 XML インデックスの変更  
  
### <a name="how-to-alter-a-selective-xml-index"></a>方法: 選択的 XML インデックスを変更する  
 **Transact-SQL を使用して選択的 XML インデックスを変更する**  
 ALTER INDEX ステートメントを呼び出して既存の選択的 XML インデックスを変更します。 詳細については、「[ALTER INDEX &#40;選択的 XML インデックス&#41;](../../t-sql/statements/alter-index-selective-xml-indexes.md)」を参照してください。  
  
 **例**  
  
 ALTER INDEX ステートメントの例を次に示します。 このステートメントは、インデックスの XQuery の部分にパス `'/a/b/m'` を追加し、「`'/a/b/e'`CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;[」のトピックの例で作成したインデックスの SQL の部分からパス ](../../t-sql/statements/create-selective-xml-index-transact-sql.md) を削除します。 削除するパスは、作成時に指定された名前によって識別されます。  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
)  
```  
  
  
##  <a name="dropping-a-selective-xml-index"></a><a name="drop"></a> 選択的 XML インデックスの削除  
  
### <a name="how-to-drop-a-selective-xml-index"></a>方法: 選択的 XML インデックスを削除する  
 **Transact-SQL を使用して選択的 XML インデックスを削除する**  
 DROP INDEX ステートメントを呼び出して選択的 XML インデックスを削除します。 詳細については、「[DROP INDEX &#40;選択的 XML インデックス&#41;](../../t-sql/statements/drop-index-selective-xml-indexes.md)」を参照してください。  
  
 **例**  
  
 DROP INDEX ステートメントの例を次に示します。  
  
```sql  
DROP INDEX sxi_index ON tbl  
```  
  
  
  
