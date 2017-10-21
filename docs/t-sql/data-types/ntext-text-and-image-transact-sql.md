---
title: "ntext、text、または image (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ntext_TSQL
- ntext
dev_langs:
- TSQL
helpviewer_keywords:
- text data type, about text data type
- text [SQL Server], data types
- ntext data type
- ntext data type, about ntext data type
- image data type, about image data type
ms.assetid: b0d8769c-7598-4f97-8162-ace5f182b5bc
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 76b78b01596b484bc35df1a1e468c5b2bb8ece63
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="ntext-text-and-image-transact-sql"></a>ntext 型、text 型、image 型 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

サイズの大きい非 Unicode 文字、Unicode 文字、およびバイナリ データを格納する固定長データ型と可変長データ型を指定します。 Unicode データは UNICODE UCS-2 文字セットを使用します。
  
>**重要:**  **ntext**、**テキスト**、および**イメージ**データ型は、SQL Server の将来のバージョンで削除される予定です。 新しい開発作業では、これらのデータ型の使用は避け、現在これらのデータ型を使用しているアプリケーションは修正するようにしてください。 代わりに、 [nvarchar(max)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)、 [varchar(max)](../../t-sql/data-types/char-and-varchar-transact-sql.md)、 [varbinary(max)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md) を使用してください。  
  
  
## <a name="arguments"></a>引数  
**ntext**  
文字列の最大長が 2^30 - 1 (1,073,741,823) の可変長の Unicode データを指定します。 格納サイズは、入力した文字列の長さの 2 倍のバイト数です。 ISO シノニムは、 **ntext**は**national テキスト**です。
  
**text**  
サーバー コード ページ内の可変長の非 Unicode データを指定します。文字列の最大長は 2^31-1 (2,147,483,647) です。 サーバー コード ページが 2 バイト文字を使用する場合、格納サイズは、そのまま 2,147,483,647 バイトです。 文字列によっては、格納サイズが 2,147,483,647 バイトより少なくなることもあります。
  
**image**  
0 ～ 2^31-1 (2,147,483,647) バイトの可変長のバイナリ データを指定します。
  
## <a name="remarks"></a>解説  
次の関数とステートメントで使用できます**ntext**、**テキスト**、または**イメージ**データ。
  
|関数|ステートメント|  
|---|---|
|[DATALENGTH & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/datalength-transact-sql.md)|[READTEXT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/readtext-transact-sql.md)|  
|[PATINDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/patindex-transact-sql.md)|[[SET textsize] & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-textsize-transact-sql.md)|  
|[部分文字列と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/substring-transact-sql.md)|[UPDATETEXT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/updatetext-transact-sql.md)|  
|[TEXTPTR & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)|[WRITETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/writetext-transact-sql.md)|  
|[TEXTVALID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/text-and-image-functions-textvalid-transact-sql.md)||  
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[データ型の変換 (&) #40";"データベース エンジン"&"#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[ような & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/like-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[照合順序と Unicode のサポート](../../relational-databases/collations/collation-and-unicode-support.md)


