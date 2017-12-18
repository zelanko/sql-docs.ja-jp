---
title: "ネイティブ コンパイル ストアド プロシージャの呼び出しに関するベスト プラクティス | Microsoft Docs"
ms.custom: 
ms.date: 03/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694bb
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2afbd1c8f7c8fce83b5c626ffba4078b71446406
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="best-practices-for-calling-natively-compiled-stored-procedures"></a>ネイティブ コンパイル ストアド プロシージャの呼び出しに関するベスト プラクティス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] ネイティブ コンパイル ストアド プロシージャの特徴:  
  
-   通常、アプリケーションのパフォーマンスが重要な部分に使用されます。  
  
-   頻繁に実行されます。  
  
-   非常に高速であることが求められます。  
  
 ネイティブ コンパイル ストアド プロシージャを使用することに伴うパフォーマンス上の利点は、プロシージャによって処理される行の数と論理の量に従って大きくなります。 たとえば、次の 1 つ以上を使用している場合は、ネイティブ コンパイル ストアド プロシージャのパフォーマンスが向上します。  
  
-   集計。  
  
-   入れ子になっているループ結合。  
  
-   複数ステートメントの SELECT、INSERT、UPDATE、および DELETE 操作。  
  
-   複合式。  
  
-   条件ステートメントとループなど、手続き型のロジック。  
  
 単一行のみを処理する必要がある場合は、ネイティブ コンパイル ストアド プロシージャを使用しても、パフォーマンス上の利点が得られるとは限りません。  
  
 サーバーによるパラメーター名のマップと型の変換を回避するには:  
  
-   プロシージャに渡されるパラメーターの型をプロシージャ定義の型に一致させます。  
  
-   ネイティブ コンパイル ストアド プロシージャを呼び出すときに序数 (名前のない) パラメーターを使用します。 最も効率的に実行するには、名前付きパラメーターを使用しないでください。  
  
 ネイティブ コンパイル ストアド プロシージャでのパラメーターの非効率性は、XEvent の **natively_compiled_proc_slow_parameter_passing** によって検出できます。
 - 一致しない型: **reason=parameter_conversion**
 - 名前付きパラメーター: **reason=named_parameters**
 - 既定値: **reason=default** 
  
## <a name="see-also"></a>参照  
 [ネイティブ コンパイル ストアド プロシージャ](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
