---
title: xml (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xml_TSQL
- xml
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], about xml data type
ms.assetid: 9198f671-8e61-4ca4-9c3a-859f84020e62
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6b9d3c8c512611ea9d8d0482acb7fd848c04629b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="xml-transact-sql"></a>xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  XML データを格納するデータ型です。 格納できる **xml** インスタンスは、列や変数の **xml** 型です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xml ( [ CONTENT | DOCUMENT ] xml_schema_collection )  
```  
  
## <a name="arguments"></a>引数  
 CONTENT  
 **xml** インスタンスを整形式の XML フラグメントに制限します。 XML データの最上位レベルには、0 個以上の要素を複数含めることができ、 テキスト ノードも許可されます。  
  
 これは既定の動作です。  
  
 DOCUMENT  
 **xml** インスタンスを整形式の XML ドキュメントに制限します。 XML データにはルート要素を 1 つだけ含めることができます。 最上位レベルにテキスト ノードは許可されません。  
  
 *xml_schema_collection*  
 XML スキーマ コレクションの名前を指定します。 型指定された **xml** 列または変数を作成するには、必要に応じて、XML スキーマ コレクションの名前を指定することができます。 型指定された XML および型指定されていない XML に関する詳細については、「 [型指定された XML と型指定されていない XML の比較](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 ストアド表現 **xml** データ型のインスタンスは、サイズの 2 ギガバイト (GB) を超えることはできません。  
  
 CONTENT および DOCUMENT ファセットは型指定された XML にのみ適用されます。 詳細については、「[型指定された XML と型指定されていない XML の比較](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @y xml (Sales.IndividualSurveySchemaCollection);  
SET @y =  (SELECT TOP 1 Demographics FROM Sales.Individual);  
SELECT @y;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データ型の変換 &#40;データベース エンジン&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)   
 [XQuery 言語リファレンス &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)  
  
  
