---
title: トレースを停止する
titleSuffix: SQL Server Profiler
description: SQL Server Profiler で実行されているトレースの停止、調整するプロパティの変更、キャプチャしたデータの保存を行う方法について説明します。
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 47c4f33d-63e0-4444-bec8-4c1c91f8e25c
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: f684e1564042101eece71d8a064746c6464fca52
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85734150"
---
# <a name="stop-a-trace-sql-server-profiler"></a>トレースの停止 (SQL Server Profiler)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、実行中のトレースを停止する方法について説明します。  
  
 トレースを停止すると、データのキャプチャも停止します。 トレースを停止した場合、トレースを再開すると、既にキャプチャしたデータは失われます。ただし、トレース ファイルまたはトレース テーブルにキャプチャしたデータが失われることはありません。 トレースを停止した後に、キャプチャしたデータをテーブルまたはファイルに保存することは可能です。 トレースを停止しても、あらかじめ選択されているすべてのトレース プロパティは保存されます。 トレースを停止した後は、名前、イベント、列、およびフィルターを変更できます。  
  
### <a name="to-stop-a-trace"></a>トレースを停止するには  
  
1.  実行中のトレースを選択します。  
  
2.  **[ファイル]** メニューの **[トレースの停止]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
