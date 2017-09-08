---
title: "ヒント (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query optimizer [SQL Server], hints
- hints [SQL Server], about hints
- SELECT statement [SQL Server], hints
- hints [SQL Server]
- INSERT statement [SQL Server], hints
- UPDATE statement [SQL Server], hints
- DELETE statement [SQL Server], hints
ms.assetid: 99412475-b0df-4264-9938-33a0b302b41a
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d2d8b50a38299162677b1f7d5bbff501fba9881
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="hints-transact-sql"></a>ヒント (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  ヒントは、オプションまたは方法によって強制用に指定された、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クエリ プロセッサでは、SELECT、INSERT、UPDATE、または DELETE ステートメント。 ヒントは、クエリ オプティマイザーがクエリのために選択するどの実行プランよりも優先されます。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]通常、クエリ オプティマイザーがクエリの最適な実行プランを選択、ことをお勧め\<join_hint >、 \<query_hint >、および\<table_hint > 経験豊富な最後の手段としてのみ使用します。開発者やデータベース管理者です。
  
 ここでは、次のヒントについて説明します。  
  
-   [結合ヒント](../../t-sql/queries/hints-transact-sql-join.md)  
  
-   [クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)  
  
-   [テーブル ヒント](../../t-sql/queries/hints-transact-sql-table.md)  
  
  

