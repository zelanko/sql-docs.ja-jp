---
title: "XQueries リレーショナル データの処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- relational data [XQuery]
- XQuery, relational data
ms.assetid: 9812b71a-52ec-48a0-92f3-016a93660229
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 447ffa853f8a5b6a257cc7e2918feaddcbde8a0f
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="xqueries-handling-relational-data"></a>リレーショナル データを処理する XQuery
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  に対して XQuery を指定する、 **xml**型の列または変数のいずれかを使用して、 [XML データ型メソッド](../t-sql/xml/xml-data-type-methods.md)です。 これらを含める**query()**、 **value()**、 **exist()**、または**modify()**です。 XQuery は、XML を生成するクエリで識別される XML インスタンスに対して実行されます。  
  
 XQuery の実行によって生成される XML には、他の Transact-SQL 変数や行セット列から取得される値を含めることができます。 SQL Server では、XML 以外のリレーショナル データを結果の XML にバインドするために、XQuery 拡張として次の擬似関数が用意されています。  
  
-   **sql:column()**関数  
  
-   **sql:variable()**関数  
  
 XQuery を指定する場合は、これらの XQuery 拡張機能を使用することができます、 **query()**のメソッド、 **xml**データ型。 その結果、 **query()**メソッドは、XML および以外のデータを結合する XML を生成できます-**xml**データ型。  
  
 使用するときにこれらの関数を使用することも、 **xml**データ型のメソッド**modify()**、 **value()**、 **query()**、および**exist()**XML 内部のリレーショナル値を公開します。  
  
 詳細については、次を参照してください。 [sql:column() 関数 (XQuery)](../xquery/xquery-extension-functions-sql-column.md)と[sql:variable() 関数 (XQuery)](../xquery/xquery-extension-functions-sql-variable.md)です。  
  
## <a name="see-also"></a>参照  
 [XML データ &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XQuery 言語リファレンス &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [XML の構築と #40 です。XQuery と #41 です。](../xquery/xml-construction-xquery.md)  
  
  
