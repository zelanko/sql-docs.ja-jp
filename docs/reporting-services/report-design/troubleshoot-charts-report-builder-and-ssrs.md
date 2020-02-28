---
title: グラフのトラブルシューティング (レポート ビルダー) | Microsoft Docs
ms.date: 01/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 96579c7dadc33c9d8dd74e823cee9cc5ef8e3367
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "77078448"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>グラフのトラブルシューティング (レポート ビルダーおよび SSRS)
  グラフを使用するときに役立つヒントを以下に示します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>グラフの値軸で件数がカウントされ、値が合計されない  
 ほとんどの種類のグラフでは、正確に描画するために値軸 (通常は Y 軸) に数値が必要です。 値フィールドのデータ型が **String**の場合、フィールドに数字が入っていても、グラフでは数値を表示できません。 その代わり、グラフには、そのフィールドに値が格納されている行の総数が表示されます。 この動作を回避するには、値系列に使用するフィールドに、書式設定された数値を格納した文字列ではなく、数値データ型を設定してください。  

## <a name="need-more-help"></a>他に支援が必要でしょうか。  
   
  次の操作を試してください。  
 * スタック オーバーフローの [SQL Server Reporting Services](https://stackoverflow.com/questions/tagged/reporting-services)  
 * [Microsoft SQL Server UserVoice](https://feedback.azure.com/forums/908035-sql-server) で問題や提案を報告  
  
## <a name="see-also"></a>参照  
 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
