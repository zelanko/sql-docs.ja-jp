---
title: サーバーへの接続後の自動的なトレースの開始 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automatic trace start
- traces [SQL Server], starting
- starting trace automatically
ms.assetid: d74b848d-e796-49af-a8c5-dd69230f3a78
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c2681f25f2cc8592d81f436bdc972e418292ac00
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076756"
---
# <a name="start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler"></a>サーバーへの接続後の自動的なトレースの開始 (SQL Server Profiler)
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]のインスタンスに接続したら、自動的にトレースが開始されるようにする方法について説明します。  
  
### <a name="to-start-a-trace-automatically-after-connecting-to-a-server-with-sql-server-profiler"></a>SQL Server Profiler を使用してサーバーへの接続後に自動的にトレースが開始されるようにするには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **[接続の確立直後にトレースを開始する]** チェック ボックスをオンにします。  
  
> [!NOTE]  
>  **[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。 トレースのプロパティを編集する場合は、まずこのチェック ボックスをオフにする必要があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  