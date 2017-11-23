---
title: "xml (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xml_TSQL
- xml
dev_langs: TSQL
helpviewer_keywords: xml data type [SQL Server], about xml data type
ms.assetid: 9198f671-8e61-4ca4-9c3a-859f84020e62
caps.latest.revision: "35"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 7dd987cd38c6f4b15e965b2510f7ae91b667a43a
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="xml-transact-sql"></a>xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  XML データを格納するデータ型です。 保存できる**xml**インスタンスは、列や変数の**xml**型です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xml ( [ CONTENT | DOCUMENT ] xml_schema_collection )  
```  
  
## <a name="arguments"></a>引数  
 CONTENT  
 制限、 **xml**インスタンスを整形式の XML フラグメントです。 XML データの最上位レベルには、0 個以上の要素を複数含めることができ、 テキスト ノードも許可されます。  
  
 これは既定の動作です。  
  
 DOCUMENT  
 制限、 **xml**インスタンスを整形式 XML ドキュメントです。 XML データにはルート要素を 1 つだけ含めることができます。 最上位レベルにテキスト ノードは許可されません。  
  
 *xml_schema_collection*  
 XML スキーマ コレクションの名前を指定します。 型指定されたを作成する**xml**列または変数、必要に応じて XML スキーマ コレクションの名前を指定することができます。 詳細については型指定された XML 型指定されていない、参照してください。[比較型指定された XML と型指定されていない XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)です。  
  
## <a name="remarks"></a>解説  
 ストアド表現**xml**データ型のインスタンスは、2 ギガバイト (GB) のサイズを超えることはできません。  
  
 CONTENT および DOCUMENT ファセットは型指定された XML にのみ適用されます。 詳細については、次を参照してください。[比較型指定された XML と型指定されていない XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)です。  
  
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
  
  
