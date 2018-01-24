---
title: "トレース データへのアクセスを向上させる | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-trace
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], space
- SQL Server Profiler, space
- space [SQL Server], SQL Server Profiler
ms.assetid: c260c000-fd53-4831-993f-df6894f3228b
caps.latest.revision: "14"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: da917dce9297e934bbaa0fd2236d1c2d17c08795
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="improve-access-to-trace-data"></a>トレース データへのアクセスを向上させる
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] は、トレース データのアクセスを向上させるために、**temp** ディレクトリの領域を使用します。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] には、最低で 10 MB の空き領域が必要です。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]の使用中に空き容量が 10 MB より少なくなると、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] のすべての機能が停止します。  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] によって **temp** ディレクトリの領域が使用されると、 **temp** ディレクトリのサイズがすぐに大きくなってしまう場合があります。 ファイル サイズ増大の問題を防ぐために、TEMP 環境変数の値を変更して、 **temp** ディレクトリをシステム ドライブでないドライブに配置することができます。  
  
 以下の手順は、ほとんどの Microsoft Windows オペレーティング システムで TEMP 環境変数の値を変更する方法を説明しています。 環境変数の設定の詳細については、お使いの Windows オペレーティング システムのドキュメントを参照してください。  
  
### <a name="to-change-the-temp-environment-variable-in-windows-operating-systems"></a>Windows オペレーティング システムで TEMP 環境変数を変更するには  
  
1.  **[スタート]** メニューの **[コントロール パネル]**をクリックし、 **[システム]**をクリックします。  
  
2.  **[システムのプロパティ]** ダイアログ ボックスで、 **[詳細設定]** タブをクリックし、 **[環境変数]**をクリックします。  
  
3.  **[システム環境変数]**ボックスの一覧をスクロールして、 **TEMP** 変数の行をクリックし、 **[編集]**をクリックします。  
  
4.  **[システム変数の編集]** ダイアログ ボックスで、 **temp** ディレクトリを配置するドライブとディレクトリのパスと名前を入力します。  
  
5.  **[OK]** をクリックして変更を保存します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler の起動](../../tools/sql-server-profiler/start-sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
