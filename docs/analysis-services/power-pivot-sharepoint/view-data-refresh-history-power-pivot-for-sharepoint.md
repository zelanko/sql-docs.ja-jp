---
title: データ更新履歴 (Power Pivot for SharePoint) の表示 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8b05a5f8fa173699aebe8567a329e7a93ee58975
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34028653"
---
# <a name="view-data-refresh-history-power-pivot-for-sharepoint"></a>データ更新履歴の表示 (Power Pivot for SharePoint)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ更新の履歴とは、Excel ブックの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データに対するすべてのデータ更新操作の記録です。 データ更新操作は、指定したスケジュールで SharePoint ファーム内の Analysis Services サーバー インスタンスで実行されます。 既定では、データ更新の履歴は 1 年間保持されます。 ただし、ファーム管理者は、データ更新記録を保持する期間を決定する、使用状況およびイベントの履歴に対する別の保有ポリシーを指定できます。  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010  
  
 **このトピックの内容:**  
  
 [前提条件](#prereq)  
  
 [個々のブックのデータ更新履歴の表示](#viewhistory)  
  
 [すべてのブックのデータ更新履歴の表示](#viewITOps)  
  
 [履歴情報の使用](#pageelements)  
  
##  <a name="prereq"></a> 前提条件  
 データ更新の履歴を表示するには、投稿権限以上の権限が必要です。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データが含まれているブックに対して、データ更新を有効にし、スケジュールしておく必要があります。 データ更新をスケジュールしていない場合、履歴情報の代わりにスケジュール定義ページが表示されます。  
  
##  <a name="viewhistory"></a> 個々のブックのデータ更新履歴の表示  
  
1.  SharePoint サイトで、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データが格納された Excel ブックが含まれているライブラリを開きます。  
  
     SharePoint ライブラリ内のどのブックに [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データが含まれているかを、外観で判別することはできません。 更新可能な [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データが含まれているブックを、あらかじめ調べておく必要があります。  
  
2.  ブックを選択し、右側にある下矢印をクリックします。  
  
3.  **[[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ更新の管理]** をクリックします。  
  
 履歴ページが開き、現在の Excel ブック内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データに関するすべての更新操作の完全なレコードが表示されます。  
  
##  <a name="viewITOps"></a> すべてのブックのデータ更新履歴の表示  
 サーバーの全体管理で [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードを使用すると、ファーム管理者およびサービス アプリケーション管理者は、すべての [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックに関するデータ更新の履歴と状態を一括して表示できます。 詳細については、「 [Power Pivot Management Dashboard and Usage Data](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)」を参照してください。  
  
##  <a name="pageelements"></a> 履歴情報の使用  
 データ更新の履歴ページには、各更新操作に関する詳細な情報が表示されます。 このページの情報を使用すると、更新が行われたかどうかを確認したり、更新が失敗した理由を調べたりすることができます。  
  
|アイテム|Description|  
|----------|-----------------|  
|名前|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データが含まれている Excel ブックのファイル名を示します。|  
|現在の状態|値は、 **[スケジュール]**、 **[更新中]**、 **[成功]**、 **[失敗]** のいずれかです。<br /><br /> **[スケジュール]** は、初めてスケジュールを作成するときに表示されます。 データ更新が初めて実行された後は、この状態メッセージは表示されなくなります。<br /><br /> **[更新中]** は、データ更新が進行中であることを示します。 要求が処理キューにあるか、サーバーで現在実行中です。<br /><br /> **[成功]** は、前回のデータ更新操作が完了したことを示しており、更新後のブックは SharePoint ライブラリにチェックインされて戻されます。<br /><br /> **[失敗]** は、前回のデータ更新操作が成功しなかったことを示します。 更新後のデータは保存されませんでした。 ブックには、データ更新が開始される前と同じデータが含まれています。|  
|成功した前回の更新|前回のデータ更新が正常に完了した日付を示します。|  
|スケジュールされている次回の更新|次回のデータ更新の実行がスケジュールされている日付を示します。<br /><br /> **[スケジュールの構成]** リンクから、スケジュール定義ページに移動できます。 ブックに対する投稿権限がある場合、このリンクをクリックして、ブック内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データに対する自動データ更新を制御するスケジュール情報を表示および変更することができます。|  
|Started|履歴の詳細セクション内の **[開始]** は、実際の処理時間を示します。 実際の処理時間は、スケジュールとは異なることもあります。 処理が開始されるのは、サーバー上に使用可能なメモリが十分にあるときです。 サーバーの負荷が高い場合、指定した開始時刻よりも数時間遅れて処理が開始されることもあります。|  
|[完了]|履歴の詳細セクション内の **[完了]** は、データ更新操作がいつ終了したかを示します。 日付と時刻は、ブックがライブラリにチェックインされて戻されたときを示します。<br /><br /> データ更新が失敗すると、1 つ以上のエラー メッセージによって、失敗の原因が説明されます。 各レコードを展開して詳細な状態を表示できます。 各データ ソースは、成功メッセージ、またはデータ更新が完了しなかった理由を説明する失敗メッセージと共に、別々に表示されます。|  
|[時刻]|データ更新が開始されてから完了するまでの累積時間を示します。|  
|[状態]|更新操作が成功したか失敗したかの履歴レコードを示します。|  
  
## <a name="see-also"></a>参照  
 [使用状況データ収集の構成 (Power Pivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md)   
 [データ更新 (Power Pivot for SharePoint) のスケジュールします。](http://msdn.microsoft.com/en-us/8571208f-6aae-4058-83c6-9f916f5e2f9b)   
 [Power Pivot データ更新](../../analysis-services/power-pivot-sharepoint/power-pivot-data-refresh.md)  
  
  
