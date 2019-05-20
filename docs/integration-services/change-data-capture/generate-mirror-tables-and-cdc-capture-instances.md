---
title: ミラー テーブルおよび CDC キャプチャ インスタンスの生成 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- mirTab
ms.assetid: 260c1617-eecc-4007-a84d-3c5778ce46b6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e4e87cebfac91e8b562c8cc0867d54f38e948ff9
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728825"
---
# <a name="generate-mirror-tables-and-cdc-capture-instances"></a>ミラー テーブルおよび CDC キャプチャ インスタンスの生成

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  [ミラー テーブルの生成] ページを使用すると、CDC インスタンスに含めたテーブルのミラー テーブルを生成できます。  
  
 **[実行]** をクリックするとミラー テーブルが作成されます。 テーブルごとに作成の進行状況が表示され、各ミラー テーブルの作成が正常に終了したか、エラーが発生したかを通知するメッセージが表示されます。 エラーが発生した場合は、 **[詳細]** をクリックしてエラーについて説明するダイアログ ボックスを表示します。  
  
 テーブルの作成に失敗した場合は、そのまま続行するか、または失敗したテーブルを削除してから続行するかを選択できます。 ウィザードの実行が終了したら、Oracle ソース データベースでテーブルを修正するか、CDC インスタンスでそのテーブルを使用しないようにするかを選択できます。 テーブルを修正する場合は、 [Edit Tables](../../integration-services/change-data-capture/edit-tables.md)を行うときにそのテーブルを追加できます。  
  
 **[次へ]** をクリックして [Finish](../../integration-services/change-data-capture/finish.md) ページを開きます。  
  
## <a name="see-also"></a>参照  
 [SQL Server 変更データベース インスタンスを作成する方法](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)  
  
  
