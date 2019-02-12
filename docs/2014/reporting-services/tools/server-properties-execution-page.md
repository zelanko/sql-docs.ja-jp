---
title: サーバーのプロパティ ([実行] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.execution.f1
ms.assetid: 53b77db1-b013-4dac-82dd-30c0de276639
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 835aa0c500e53ab28df491fe8209d2af27083365
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56015263"
---
# <a name="server-properties-execution-page"></a>[サーバーのプロパティ] [実行] ページ)
  このページを使用すると、レポート実行のタイムアウト値を設定できます。 この値は、現在のレポート サーバー インスタンスによって処理されるすべてのレポートに適用されます。 この設定は、レポートごとにオーバーライドすることができます。 レポート サーバーで行われるすべてのレポート処理の時間に加え、レポート内で使用されるデータをレポート サーバーが取得するときにデータベース サーバーで実行されるクエリ処理に対応する時間も指定する必要があります。  
  
 このページを開くには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動してレポート サーバー インスタンスに接続し、レポート サーバー名を右クリックして **[プロパティ]** をクリックします。 **[実行]** をクリックするとこのページが開きます。  
  
## <a name="options"></a>および  
 **[レポートの実行をタイムアウトしない]**  
 レポート サーバーでレポート処理が完了するまでの時間を制限しないようにします。  
  
 **[レポートの実行を次の秒数に制限する]**  
 レポート実行の時間制限を設定します。 時間はレポートが要求されたときから測定されます。 レポートが完全に処理される前に制限時間に到達した場合、レポート サーバーは、処理および外部データ ソースに対するインプロセス クエリをすべて取り消します。  
  
## <a name="see-also"></a>参照  
 [レポート サーバーのプロパティを設定する (Management Studio)](set-report-server-properties-management-studio.md)   
 [Management Studio でレポート サーバーに接続する](connect-to-a-report-server-in-management-studio.md)   
 [レポート処理プロパティの設定](../report-server/set-report-processing-properties.md)   
 [レポートおよび共有データセット処理のタイムアウト値の設定 (SSRS)](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)   
 [Management Studio のレポート サーバーの F1 ヘルプ](report-server-in-management-studio-f1-help.md)  
  
  
