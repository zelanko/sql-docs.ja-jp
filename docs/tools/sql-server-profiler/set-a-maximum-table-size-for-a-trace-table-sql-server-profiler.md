---
title: トレース テーブルの最大テーブル サイズを設定する
titleSuffix: SQL Server Profiler
description: トレース テーブルのサイズを制限する方法について説明します。 SQL Server Profiler を使用して、テーブルが保持できる最大行数を指定します。
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: d867d1dca6ab5f17f45c89aa6bbd99394e72bcef
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85726878"
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a>トレース テーブルの最大テーブル サイズの設定 (SQL Server Profiler)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、トレース テーブルの最大テーブル サイズを設定する方法について説明します。  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a>トレース テーブルの最大テーブル サイズを設定するには  
  
1.  **[ファイル]** メニューの **[新しいトレース]** をクリックし、SQL Server のインスタンスに接続します。  
  
     **[トレースのプロパティ]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  **[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。 この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。  
  
2.  **[トレース名]** ボックスに、トレースの名前を入力します。  
  
3.  **[テンプレート名]** ボックスの一覧で、トレース テンプレートを選択します。  
  
4.  **[テーブルに保存]** チェック ボックスをオンにします。  
  
5.  トレースを格納するサーバーに接続します。  
  
     **[キャプチャ先テーブル]** ダイアログ ボックスが表示されます。  
  
6.  **[データベース]** ボックスの一覧から、トレースするデータベースを選択します。  
  
7.  **[テーブル]** ボックスで、テーブル名を入力するか、選択します。  
  
8.  **[最大行数の設定 (1000 行単位)]** チェック ボックスをオンにし、トレース テーブルの最大行数を指定します。  
  
    > [!NOTE]  
    >  テーブル内の行数が、指定した最大数を超えると、トレース イベントは記録されなくなります。 ただし、トレースは続行されます。  
  
## <a name="see-also"></a>参照  
 [[SQL Server Profiler]](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
