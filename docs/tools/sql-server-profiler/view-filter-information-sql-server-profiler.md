---
title: フィルター情報を表示する
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: fb79fc3c75686d2a09d46d1a336a3376028382e2
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307752"
---
# <a name="view-filter-information-sql-server-profiler"></a>フィルター情報の表示 (SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用してイベント クラスのデータ列のフィルターを表示する方法について説明します。  
  
### <a name="to-view-filter-information"></a>フィルター情報を表示するには  
  
1.  トレース ファイル、トレース テーブル、または SQL スクリプトを開き、 **[ファイル]** メニューの **[プロパティ]** をクリックします。 トレース テンプレートを編集している場合、または新しいトレースを作成している場合、この手順は省略します。  
  
2.  **[イベントの選択]** タブで、フィルターを表示するデータ列の名前を右クリックし、 **[列フィルターの編集]** をクリックします。  
  
3.  **[フィルターの編集]** ダイアログ ボックスでフィルターの比較演算子を展開し、指定の条件に割り当てられている値を確認します。 フィルター情報を表示するすべての列に対し、手順 2. と 3. を繰り返します。  
  
> [!NOTE]  
>  値が割り当てられている比較演算子は太字で表示されます。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
