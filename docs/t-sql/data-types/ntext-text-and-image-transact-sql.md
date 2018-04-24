---
title: ntext、text、および image (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 2e60348cdf1407c653dcadf70a626c5fba8ecaac
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ntext-text-and-image-transact-sql"></a>ntext 型、text 型、image 型 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

サイズの大きい非 Unicode 文字、Unicode 文字、およびバイナリ データを格納する固定長データ型と可変長データ型を指定します。 Unicode データは UNICODE UCS-2 文字セットを使用します。
  
>**重要:**  **ntext**、**text**、および **image** データ型は、今後のバージョンの SQL Server で削除される予定です。 新しい開発作業では、これらのデータ型の使用は避け、現在これらのデータ型を使用しているアプリケーションは修正するようにしてください。 代わりに、 [nvarchar(max)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)、 [varchar(max)](../../t-sql/data-types/char-and-varchar-transact-sql.md)、 [varbinary(max)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md) を使用してください。  
  
  
## <a name="arguments"></a>引数  
**ntext**  
文字列の最大長が 2^30 - 1 (1,073,741,823) の可変長の Unicode データを指定します。 格納サイズは、入力した文字列の長さの 2 倍のバイト数です。 ISO シノニムは、 **ntext** は **national テキスト**です。
  
**text**  
サーバー コード ページ内の可変長の非 Unicode データを指定します。文字列の最大長は 2^31-1 (2,147,483,647) です。 サーバー コード ページが 2 バイト文字を使用する場合、格納サイズは、そのまま 2,147,483,647 バイトです。 文字列によっては、格納サイズが 2,147,483,647 バイトより少なくなることもあります。
  
**image**  
0 ～ 2^31-1 (2,147,483,647) バイトの可変長のバイナリ データを指定します。
  
## <a name="remarks"></a>Remarks  
次の関数とステートメントで使用できる **ntext**, 、**テキスト**, 、または **イメージ** データ。
  
|関数|ステートメント|  
|---|---|
|[DATALENGTH (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/datalength-transact-sql.md)|[READTEXT &#40;Transact-SQL&#41;](../../t-sql/queries/readtext-transact-sql.md)|  
|[PATINDEX (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/patindex-transact-sql.md)|[[SET TEXTSIZE] (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-textsize-transact-sql.md)|  
|[部分文字列 (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/substring-transact-sql.md)|[UPDATETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/updatetext-transact-sql.md)|  
|[TEXTPTR &#40;Transact-SQL&#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)|[WRITETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/writetext-transact-sql.md)|  
|[TEXTVALID &#40;Transact-SQL&#41;](../../t-sql/functions/text-and-image-functions-textvalid-transact-sql.md)||  
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[データ型の変換 (&) #40";"データベース エンジン"&"#41 です。](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[ように (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/like-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[照合順序と Unicode のサポート](../../relational-databases/collations/collation-and-unicode-support.md)

