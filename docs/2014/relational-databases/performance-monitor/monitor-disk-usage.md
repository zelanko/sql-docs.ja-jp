---
title: ディスクの使用量の監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- database monitoring [SQL Server], disk usage
- disks [SQL Server]
- monitoring performance [SQL Server], disk usage
- server performance [SQL Server], disk usage
- monitoring [SQL Server], disk activity
- excess paging [SQL Server]
- tuning databases [SQL Server], disk usage
- I/O [SQL Server], monitoring
- disks [SQL Server], monitoring activity
- isolating disk activity [SQL Server]
- database performance [SQL Server], disk usage
- monitoring server performance [SQL Server], disk usage
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
caps.latest.revision: 22
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 58c0251f9277b923b00a32a992761e976483ef8e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083176"
---
# <a name="monitor-disk-usage"></a>ディスクの使用量の監視
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、Microsoft Windows オペレーティング システムの入出力 (I/O) 呼び出しを使用して、ディスクに対する読み取りおよび書き込み操作を実行します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ディスク I/O を実行する時期と方法が管理されます。ただし、基本的な I/O 操作は Windows オペレーティング システムで実行されます。 I/O サブシステムには、システム バス、ディスク コントローラー カード、ディスク、テープ ドライブ、CD-ROM ドライブなど、多数の I/O 装置が含まれます。 ディスク I/O は、頻繁にシステムのボトルネックの原因となります。  
  
 ディスク利用状況の監視には、次の 2 つの領域があります。  
  
-   ディスク I/O の監視と、過度なページングの検出  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で生成されるディスク利用状況の隔離  
  
 詳細については、「 [ディスク使用量の監視](http://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)」を参照してください。  
  
  