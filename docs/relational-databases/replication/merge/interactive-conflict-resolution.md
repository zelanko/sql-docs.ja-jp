---
title: "インタラクティブな競合解決 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "インタラクティブな競合解決 [SQL Server レプリケーション]"
  - "インタラクティブ競合回避モジュール [SQL Server レプリケーション]"
  - "アーティクル [SQL Server レプリケーション], 競合回避"
  - "競合回避 [SQL Server レプリケーション]、マージ レプリケーション"
ms.assetid: 172c60c7-f605-4eb5-b185-54ae9e9d3c60
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# インタラクティブな競合解決
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーションでは、インタラクティブ競合回避モジュールでの要求時同期中に競合を手動で解決できる [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 同期マネージャー。 インタラクティブ競合回避モジュールを実行時に有効化すると、グラフィカル インターフェイスに競合する各行のデータが表示されます。ここから、競合するデータを表示および編集し、個々の競合を解決できます。  
  
 インタラクティブ競合回避モジュールは競合表示モジュールに似ています。 ただし、競合表示モジュールではマージ同期後に解決済みの競合の結果が表示されるのに対して、インタラクティブ競合回避モジュールでは解決の前に各競合が表示されるため、マージ同期時に取り込むデータを指定できます。 いずれかのユーザーが、競合発生時にインタラクティブ競合回避モジュールを監視できるようになっている必要があります。  
  
> [!NOTE]  
>  インタラクティブな競合回避には Windows 同期マネージャーが必要です。 同期が Windows 同期マネージャーの外部で (スケジュールされた同期、または [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] かレプリケーション モニターでの要求時同期として) 実行される場合、競合は、アーティクルに指定された競合回避モジュールに従って、ユーザーの介入なしに自動的に解決されます。 論理レコードに関連する競合は、インタラクティブ競合回避モジュールには表示されません。 これらの競合に関する情報を表示するには、レプリケーション ストアド プロシージャを使用します。 詳細については、次を参照してください [#40; (&)、マージ パブリケーションの競合情報の表示。レプリケーション TRANSACT-SQL プログラミングと #41;](../../../relational-databases/replication/view conflict information for merge publications.md)します。  
  
## アーティクル競合回避モジュールおよびインタラクティブ競合回避モジュール  
 競合回避モジュール (既定の競合回避モジュール、ビジネス ロジック ハンドラー、カスタム競合回避モジュールのいずれか) は、パブリケーションの作成時に特定のアーティクルに割り当てられます。そこでルールのセットによって、競合している行データを入力したときにどのデータセットを使用するかが決まります。 インタラクティブ競合回避モジュールは、競合でどのデータを優先するかを指定するルールを持つ独立した競合回避モジュールではなく、既定またはカスタムの競合回避モジュールと組み合わせて使用するツールです。 アーティクル競合回避モジュールでは、どの行を競合で優先し、どの行を優先しないかが指定されますが、インタラクティブ競合回避モジュールでは、その結果にユーザーが介入し、データを受け入れたり、拒否したり、変更したりすることができます。  
  
 インタラクティブ競合回避モジュールを使用するには、競合回避を必要とする各アーティクルまたはサブスクリプションに対して、インタラクティブな競合回避を有効にしておく必要があります。 1 つ以上のアーティクルまたはサブスクリプションで有効にしておくと、マージ同期中に競合が検出された場合、インタラクティブ競合回避モジュールを使用できます。  
  
 インタラクティブ競合回避モジュールを使用するのを参照してください [マージ アーティクルのインタラクティブな競合解決の指定](../../../relational-databases/replication/publish/specify-interactive-conflict-resolution-for-merge-articles.md) と [サブスクリプションを使用して Windows 同期マネージャーと #40; の同期。Windows 同期マネージャーと #41;](../../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md)します。  
  
## 参照  
 [マージ レプリケーションの競合検出および解決の詳細](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  