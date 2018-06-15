---
title: 'レッスン 7: 親レポートにドリルスルー アクションを追加する | Microsoft Docs'
ms.custom: ''
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: aad2da1a-d7b1-4afa-a66a-1ff102e8306f
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: afb72e601ef9715cf0951cbff46c1033aa1c1854
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33015289"
---
# <a name="lesson-7-add-drillthrough-action-on-parent-report"></a>レッスン 7: 親レポートにドリルスルー アクションを追加する
Web サイト アプリケーションに ReportViewer コントロールを追加した後は、親レポートにドリルスルー アクションを追加します。  
  
### <a name="to-add-drillthrough-action-on-the-parent-report"></a>親レポートにドリルスルー アクションを追加するには  
  
1.  親レポートに移動します。  
  
2.  **Name**の値を保持するテキスト ボックスを選択します。  
  
3.  テキスト ボックスを右クリックし、**[テキスト ボックスのプロパティ]** を選択します。  
  
4.  **[アクション]** タブに移動し、**[レポートに移動する]** オプションを選択します。  
  
5.  **[レポートの指定]** セクションで、子レポートの名前を入力します。  
  
    > [!NOTE]
    > レポート名にファイル拡張子を含めないでください。  
  
6.  **[レポートの実行に使用するパラメーター]** セクションで、**[追加]** を選択します。  
  
7.  **[名前]** ボックスに「 **productid** 」と入力し、**[値]** ドロップダウン リストで **[ProductID]** をクリックします。  
  
8.  **[OK]** を選択して作業を終了します。  
  
## <a name="next-task"></a>次の作業  
これで、親レポートにドリルスルー アクションを追加できました。 次は、子レポートに対して定義したデータ テーブルのデータ フィルターを作成します。 [「レッスン 8: データ フィルターを作成する」](../reporting-services/lesson-8-create-a-data-filter.md)を参照してください。  
  
  
  

