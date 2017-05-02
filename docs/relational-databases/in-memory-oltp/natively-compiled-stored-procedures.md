---
title: "ネイティブ コンパイル ストアド プロシージャ | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- natively compiled stored procedures
ms.assetid: d5ed432c-10c5-4e4f-883c-ef4d1fa32366
caps.latest.revision: 54
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b718bafa35ae753eba0064db2af168054fd211ca
ms.lasthandoff: 04/11/2017

---
# <a name="natively-compiled-stored-procedures"></a>ネイティブ コンパイル ストアド プロシージャ
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  ネイティブ コンパイル ストアド プロシージャは、ネイティブ コードにコンパイルされる [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャであり、メモリ最適化テーブルにアクセスします。 ネイティブ コンパイル ストアド プロシージャでは、ストアド プロシージャでクエリやビジネス ロジックを効率的に実行できます。 ネイティブ コンパイル処理の詳細については、「 [テーブルとストアド プロシージャのネイティブ コンパイル](../../relational-databases/in-memory-oltp/native-compilation-of-tables-and-stored-procedures.md)」を参照してください。 ディスク ベース ストアド プロシージャをネイティブ コンパイル ストアド プロシージャに移行する方法の詳細については、「 [ネイティブ コンパイル ストアド プロシージャの移行に関する問題](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)」を参照してください。  
  
> [!NOTE]  
>  解釈された (ディスク ベースの) ストアド プロシージャとネイティブ コンパイル ストアド プロシージャの相違点の 1 つは、解釈されたストアド プロシージャは最初の実行時にコンパイルされ、ネイティブ コンパイル ストアド プロシージャは作成時にコンパイルされる点です。 ネイティブ コンパイル ストアド プロシージャを使用すると、多くのエラー状態 (算術オーバーフロー、型変換、および 0 除算の状態の一部) を作成時に検出することができます。エラーが見つかった場合、ネイティブ コンパイル ストアド プロシージャの作成は失敗します。 解釈されたストアド プロシージャでは、通常、このようなエラー状態によってストアド プロシージャの作成時にエラーが発生することはありませんが、実行はすべて失敗します。  
  
 このセクションのトピック:  
  
-   [ネイティブ コンパイル ストアド プロシージャの作成](../../relational-databases/in-memory-oltp/creating-natively-compiled-stored-procedures.md)  
  
-   [ATOMIC ブロック](../../relational-databases/in-memory-oltp/atomic-blocks-in-native-procedures.md)  
  
-   [ネイティブ コンパイル T-SQL モジュールでサポートされる機能](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)  
  
-   [ネイティブ コンパイル T-SQL モジュールでサポートされる DDL](../../relational-databases/in-memory-oltp/supported-ddl-for-natively-compiled-t-sql-modules.md)  
  
-   [ネイティブ コンパイル ストアド プロシージャと実行 SET オプション](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures-and-execution-set-options.md)  
  
-   [ネイティブ コンパイル ストアド プロシージャの呼び出しに関するベスト プラクティス](../../relational-databases/in-memory-oltp/best-practices-for-calling-natively-compiled-stored-procedures.md)  
  
-   [ネイティブ コンパイル ストアド プロシージャのパフォーマンスの監視](../../relational-databases/in-memory-oltp/monitoring-performance-of-natively-compiled-stored-procedures.md)  
  
-   [データ アクセス アプリケーションからのネイティブ コンパイル ストアド プロシージャの呼び出し](../../relational-databases/in-memory-oltp/calling-natively-compiled-stored-procedures-from-data-access-applications.md)  
  
## <a name="see-also"></a>参照  
 [メモリ最適化テーブル](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
