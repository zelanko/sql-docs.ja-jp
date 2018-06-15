---
title: ヒント (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|queries
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a404f015c177fe38985c07470645e9a16e2cb716
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33058549"
---
# <a name="hints-transact-sql"></a>ヒント (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  ヒントは、SELECT、INSERT、UPDATE、または DELETE の各ステートメントについて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリ プロセッサが実施するように指定したオプションまたは方法です。 ヒントは、クエリ オプティマイザーがクエリのために選択するどの実行プランよりも優先されます。  
  
> [!CAUTION]  
>  通常、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリ オプティマイザーでは、クエリにとって最適な実行プランが選択されるため、\<join_hint>、\<query_hint> および \<table_hint> は、経験を積んだ開発者やデータベース管理者が最後の手段としてのみ使用することをお勧めします。
  
 ここでは、次のヒントについて説明します。  
  
-   [結合ヒント](../../t-sql/queries/hints-transact-sql-join.md)  
  
-   [クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)  
  
-   [テーブル ヒント](../../t-sql/queries/hints-transact-sql-table.md)  
  
  
