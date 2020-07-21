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
ms.openlocfilehash: 1639a4c95524387859c8163d94ce5bb9d8a5519a
ms.sourcegitcommit: b8933ce09d0e631d1183a84d2c2ad3dfd0602180
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83151656"
---
# <a name="stop-a-trace-sql-server-profiler"></a>トレースの停止 (SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、実行中のトレースを停止する方法について説明します。  
  
 トレースを停止すると、データのキャプチャも停止します。 トレースを停止した場合、トレースを再開すると、既にキャプチャしたデータは失われます。ただし、トレース ファイルまたはトレース テーブルにキャプチャしたデータが失われることはありません。 トレースを停止した後に、キャプチャしたデータをテーブルまたはファイルに保存することは可能です。 トレースを停止しても、あらかじめ選択されているすべてのトレース プロパティは保存されます。 トレースを停止した後は、名前、イベント、列、およびフィルターを変更できます。  
  
### <a name="to-stop-a-trace"></a>トレースを停止するには  
  
1.  実行中のトレースを選択します。  
  
2.  **[ファイル]** メニューの **[トレースの停止]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
