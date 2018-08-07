---
title: 国際化に対応した Transact-SQL ステートメントの記述 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: a8959ff278807ced475c63ea1e56388ba23ab9d3
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39564426"
---
# <a name="write-international-transact-sql-statements"></a>国際化に対応した Transact-SQL ステートメントの記述
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  以下のガイドラインに従うと、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用するデータベースやデータベース アプリケーションをある言語から別の言語に移行することが容易になり、複数の言語をサポートできます。  
  
-   **char**、 **varchar**、および **text** の各データ型を使用しているすべての個所をそれぞれ **nchar**、 **nvarchar**、および **nvarchar (max)** データ型に置き換えます。 これを行うことにより、コード ページの変換の問題について考慮する必要がなくなります。 詳細については、「 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。  
  
-   月単位または曜日単位で比較や操作を行う場合、名前の文字列ではない数字の日付要素を使用します。 言語設定が異なると、月や曜日の名前が異なります。 たとえば、DATENAME(MONTH,GETDATE()) は、言語の設定が英語 (U.S.) になっていれば "May" を返します。設定がドイツ語になっていれば "Mai"、フランス語になっていれば "mai" を返します。 代わりに、DATEPART のような関数を使用すると、月の名前の代わりに数字が返されます。 多くの場合、日付を数字で表記するよりも名前で表記する方がよりわかりやすくなるので、ユーザーに表示する結果セットを構築するときは、DATEPART 名を使用してください。 ただし、特定の言語の表示名に依存するロジックはコーディングしないでください。  
  
-   日付を比較する場合、または INSERT ステートメントまたは UPDATE ステートメントで日付を指定する場合は、どの言語設定でも同じ解釈が行われる制約を使用します。  
  
    -   ADO、OLE DB、および ODBC アプリケーションでは、以下に示す ODBC タイムスタンプ、日付、時刻のエスケープ句を使用する必要があります。  
  
         **{ ts'** yyyy**-***mm***-***dd**hh ***:*** mm ***:*** ss *[**.***fff*] **'}** such as: **{ ts'** 1998**-** 09**-** 24 10 **:** 02 **:** 20 **' }**  
  
         **{ d'** *yyyy* **-** *mm* **-** *dd* **'}** such as: **{ d'** 1998**-** 09**-** 24 **'}**  
  
         **{ t'** *hh* **:** *mm* **:** *ss* **'}** such as: **{ t'** 10:02:20 **'}**  
  
    -   他の API、または [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト、ストアド プロシージャ、およびトリガーを使用するアプリケーションでは、区切られていない数字列を使用してください。 たとえば、 *yyyymmdd* には 19980924 を使用します。  
  
    -   他の API、または [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト、ストアド プロシージャ、およびトリガーを使用するアプリケーションでは、 **time**型、 **date**型、 **smalldate**型、 **datetime**型、 **datetime2**型、および **datetimeoffset** のデータ型と文字列データ型間の変換にはすべて、明示的なスタイル パラメーターを指定して CONVERT ステートメントを使用してください。 たとえば、次のステートメントは、すべての言語または日付形式の接続設定で同じように解釈されます。  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         詳細については、「[CAST and CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)」を参照してください。  
  
  
