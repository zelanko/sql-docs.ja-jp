---
title: カーソル関数 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], cursors
- cursor functions
ms.assetid: 7d9daa10-4c50-4212-9400-42120222b2b8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cf11b84be99f1bedee01899494556f0d1b62fe07
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746000"
---
# <a name="cursor-functions-transact-sql"></a>カーソル関数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

これらのスカラー関数は、カーソルについての情報を返します。
  
|||  
|-|-|  
|[@@CURSOR_ROWS](../../t-sql/functions/cursor-rows-transact-sql.md)|[CURSOR_STATUS](../../t-sql/functions/cursor-status-transact-sql.md)|  
|[@@FETCH_STATUS](../../t-sql/functions/fetch-status-transact-sql.md)||  
  
すべてのカーソル関数は非決定的です。 つまり、これらの関数は、同じ一連の入力値を使用しても、実行されるたびに常に同じ結果を返すわけではありません。 関数の決定性の詳細については、「[決定的関数と非決定的関数](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)」を参照してください。
  
## <a name="see-also"></a>参照
[組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)
  
  
