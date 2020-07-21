---
title: '[フラットファイル変換先エディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfiledestadapter.connection.f1
helpviewer_keywords:
- Flat File Destination Editor
ms.assetid: b01571fa-bc19-4742-8eed-ac163172a919
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 83c3553916ba629382256c0d2c1c7a89131df071
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85425539"
---
# <a name="flat-file-destination-editor-connection-manager-page"></a>[フラット ファイル変換先エディター] ([接続マネージャー] ページ)
  **[フラット ファイル変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、変換先のフラット ファイル接続を選択したり、既存の変換先ファイルに対して上書きまたは追加のどれを実行するかを指定したりできます。 フラット ファイル変換先は、データをテキスト ファイルに書き込みます。 テキスト ファイルには、区切り形式、固定幅形式、行区切り記号付き固定幅形式、または幅合わせしない形式を使用できます。  
  
 フラット ファイル変換先の詳細については、「 [Flat File Destination](data-flow/flat-file-destination.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **フラットファイル接続マネージャー**  
 既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。  
  
 **[新規作成]**  
 **[フラット ファイル形式]** および **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスを使用して、新しい接続を作成します。  
  
 標準のフラット ファイル形式である、区切り形式、固定幅形式、および幅合わせしない形式に加えて、 **[フラット ファイル形式]** ダイアログ ボックスには 4 つ目のオプションとして **[行区切り記号付きの固定幅]** が用意されています。 このオプションは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] がデータの最終列としてダミー列を追加する、特殊な幅合わせしない形式を表します。 このダミー列によって、最終列が固定幅であることが保証されます。  
  
 **[フラット ファイル接続マネージャー エディター]** では **[行区切り記号付きの固定幅]** オプションは使用できません。 必要に応じて、エディターでこのオプションをエミュレートすることができます。 このオプションをエミュレートするには、 **[フラット ファイル接続マネージャー エディター]** の **[全般]** ページにある **[形式]** で、 **[幅合わせしない]** を選択します。 次に、エディターの **[詳細設定]** ページで、データの最終列として新しいダミー列を追加します。  
  
 **[ファイル内のデータを上書きする]**  
 既存のファイルを上書きするか、データを追加するかを指定します。  
  
 **ヘッダー**  
 データが書き込まれる前にファイルに挿入するテキストのブロックを入力します。 このオプションをオンにすると、列見出しなどの追加情報を含めることができます。  
  
 **プレビュー**  
 **[データ ビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 プレビューでは、最大で 200 行を表示できます。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[フラット ファイル変換先エディター] &#40;[マッピング] ページ&#41;](../../2014/integration-services/flat-file-destination-editor-mappings-page.md)  
  
  
