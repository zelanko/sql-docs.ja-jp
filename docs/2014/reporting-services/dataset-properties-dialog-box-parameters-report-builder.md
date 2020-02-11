---
title: '[パラメーター] ([データセットのプロパティ] ダイアログボックス) (レポートビルダー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10023"
ms.assetid: 3a0672ad-c969-455b-b952-585164ce1dda
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 295a40bc7964e50e5fc0c4a9ea0294b593fdde18
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109392"
---
# <a name="dataset-properties-dialog-box-parameters-report-builder"></a>[パラメーター] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー)
  [**データセットのプロパティ**] ダイアログボックスの [**パラメーター** ] を選択すると、クエリパラメーターの追加、変更、および削除を行うことができます。  
  
 埋め込みデータセットの場合、オプションはレポート定義のデータセットに適用されます。  
  
 共有データセットの場合、オプションはレポート サーバーの共有データセット定義に適用されます。  
  
 詳細については、「[埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **追加**  
 一覧に新しいパラメーターを追加します。  
  
 **デリート**  
 選択したパラメーターを一覧から削除します。  
  
 **上矢印**  
 選択したパラメーターを一覧内で上に移動します。  
  
 **下方向キー**  
 選択したパラメーターを一覧内で下に移動します。  
  
 **パラメーター名**  
 
  **[データセットのプロパティ]** ダイアログ ボックスの **[クエリ]** タブでデータセットに追加したクエリ パラメーターの名前を入力します。  
  
 **パラメーター値**  
 埋め込みデータセットにのみ適用されます。  
  
 クエリ パラメーターの値を入力します。 この値には、静的な値、またはレポート内のオブジェクトを参照するがレポート アイテムやフィールドは参照できない式を指定できます。 既定では、 **[値]** に、レポート パラメーターを参照する式が設定されています。  
  
 **既定値**  
 共有データセットにのみ適用されます。  
  
 既定値を指定する場合に、このチェック ボックスをオンにします。  
  
 既定値を入力します。 この値には、静的な値か、レポート内のオブジェクトを参照する式を使用できます。 式は、レポート アイテム、レポート パラメーター、またはフィールドを参照できません。  
  
 空白を指定するには、テキスト ボックスを空のままにします。  
  
 NULL を指定するには、NULL 許容オプションを選択します。  
  
 **読み取り専用**  
 共有データセットにのみ適用されます。  
  
 共有データセット定義でこのパラメーターを読み取り専用に指定する場合は、このオプションを選択します。 共有データセットがレポートに追加されると、パラメーターはプロパティに表示されなくなります。 レポート サーバー上で共有データセットがキャッシュされると、値は変更できなくなります。  
  
 **Nullable**  
 共有データセットにのみ適用されます。  
  
 NULL 値を許容する場合は、このオプションを選択します。  
  
 **[クエリから省略]**  
 共有データセットにのみ適用されます。  
  
 レポート パラメーターの参照が共有データセット フィルターの式に含まれ、クエリに含まれていない場合に、このオプションを選択します。 このオプションを選択した場合、クエリの実行時にこのパラメーターの既定値を指定する必要はありません。  
  
## <a name="see-also"></a>参照  
 [ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [[クエリ &#40;レポートビルダー] ([データセットのプロパティ] ダイアログボックス)&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [チュートリアル: レポートへのパラメーターの追加 &#40;レポート ビルダー&#41;](tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](report-design/report-parameters-report-builder-and-report-designer.md)   
 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [クエリデザイナー &#40;レポートビルダー&#41;](../../2014/reporting-services/query-designers-report-builder.md)   
 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [レポートビルダーおよび SSRS を &#40;共有データセットまたは埋め込みデータセットを作成&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
  
