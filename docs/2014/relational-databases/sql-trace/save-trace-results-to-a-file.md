---
title: トレース結果のファイルへの保存 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 74f80667-62f3-4e14-bb1a-f0c2b6ef3402
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a55662b38fbd69dc45d8f0031856ad4da5929038
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63136451"
---
# <a name="save-trace-results-to-a-file"></a>トレース結果のファイルへの保存
  トレース結果をファイルに保存できます。 トレース ファイルは、トレース結果が書き込まれるファイルです。 トレース ファイルは、ローカル ディレクトリ (C:\\*foldername*\\*filename.trc*など) またはネットワーク ディレクトリ ( \\\computername\sharename\filename.trc など) に配置できます。  
  
 トレース ファイルを使用して、次のことを行えます。  
  
-   トレースの再生  
  
-   監査 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   パフォーマンス分析の実行  
  
-   トレース イベントとパフォーマンス カウンターの相互関係による問題の検出の向上  
  
-   データベース エンジン チューニング アドバイザー分析の実行  
  
-   クエリの最適化の実行  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ストアドプロシージャ**@tracefile** **sp_trace_create**の引数にパスとファイル名が指定されている場合に、トレース結果をファイルに保存します。  
  
> [!NOTE]  
>  トレース ファイルの保存用に、 **sp_trace_create** ストアド プロシージャにパスを指定する場合は、サーバーからそのディレクトリにアクセスできる必要があります。 また、 **sp_trace_create**にローカル ディレクトリを指定すると、サーバー コンピューターのローカル ディレクトリを指定したことになるので注意してください。  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用している場合は、トレース結果をファイルまたはテーブルに保存できます。 テーブルにトレース結果を保存すると、ファイルにトレースを保存する場合と同じアクセスが可能になります。そのうえ、そのテーブルにクエリして、特定のイベントを検索できます。  
  
 トレース結果の保存の詳細については、「[トレース結果のテーブルへの保存 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)」および「[トレース結果のファイルへの保存 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)   
 [トレースの作成 &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md)   
 [トレースの作成 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
