---
title: "SQL Server 2016 の SQL Server インメモリ OLTP 内部 | Microsoft Docs"
ms.custom: 
ms.date: 09/14/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b14da361-a6b8-4d85-b196-7f2f13650f44
caps.latest.revision: 2
author: jodebrui
ms.author: jodebrui
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 93be3a22ee517f90e65b8c8ba6dcaa8d90ed8515
ms.openlocfilehash: 4909bc873609a0e6b83f72d1d99a4e4566ca09e7
ms.contentlocale: ja-jp
ms.lasthandoff: 07/31/2017

---
# <a name="sql-server-in-memory-oltp-internals-for-sql-server-2016"></a>SQL Server 2016 の SQL Server インメモリ OLTP 内部
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**概要:** インメモリ OLTP (コードネームの "Hekaton" で呼ばれることが多い) は SQL Server 2014 で導入されました。
この強力なテクノロジでは、大量のメモリと多数のコアを利用して、OLTP 操作のパフォーマンスを最大で 30 倍から 40 倍まで高めることができます。 SQL Server 2016 では、SQL Server 2014 で見られた多くの制限を取り除き、内部処理アルゴリズムを強化し、インメモリ OLTP によるさらなる改善に向けて、継続的にインメモリ OLTP への投資を行っています。 本書では、SQL Server 2016 RTM 版の時点での SQL Server 2016 のインメモリ OLTP テクノロジの実装について説明します。 インメモリ OLTP を使用して、テーブルを "メモリ最適化" として宣言し、インメモリ OLTP の機能を有効にすることができます。 メモリ最適化テーブルは完全なトランザクション テーブルであり、Transact-SQL を使用してアクセスできます。 Transact-SQL ストアド プロシージャ、トリガーおよびスカラー UDF は、メモリ最適化テーブルでのパフォーマンスをさらに向上させるために、マシン語コードにコンパイルできます。 エンジンは、ブロッキングが発生しない高レベルの同時実行を実現するために設計されています。    
  
**著者:** Kalen Delaney  
  
**テクニカル レビューアー:** Sunil Agarwal および Jos de Bruijn  
  
**公開日:** 2016 年 6 月  
  
**対象:** SQL Server 2016  
  
ドキュメントを確認する場合は、「 [SQL Server 2016 の SQL Server インメモリ OLTP 内部](http://download.microsoft.com/download/8/3/6/8360731A-A27C-4684-BC88-FC7B5849A133/SQL_Server_2016_In_Memory_OLTP_White_Paper.pdf) 」ドキュメントをダウンロードしてください。   

