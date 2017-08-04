---
title: "[フラット ファイル接続マネージャー エディター] ([列] ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.ffileconnection.columns.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 40ce7537-abd0-4973-97fd-6ccb90fddfa0
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 791bc8b3edbee92a0154dc03011666a488c19e7a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="flat-file-connection-manager-editor-columns-page"></a>[フラット ファイル接続マネージャー エディター] ([列] ページ)
  **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスの **[列]** ページを使用すると、行および列情報を指定したり、ファイルをプレビューしたりできます。  
  
 フラット ファイル接続マネージャーの詳細については、「 [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md)」を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **[接続マネージャー名]**  
 ワークフローにおけるフラット ファイル接続マネージャーの一意な名前を指定します。 指定された名前は、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーに表示されます。  
  
 **Description**  
 接続の説明を記述します。 パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続の目的について記述することをお勧めします。  
  
## <a name="flat-file-format-dynamic-options"></a>フラット ファイル形式の動的オプション  
  
### <a name="format--delimited"></a>[形式] = [区切り記号]  
 **[行区切り記号]**  
 使用できる行区切り記号の一覧から選択するか、区切り記号テキストを入力します。  
  
|値|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|行は、復帰と改行の組み合わせで区切られます。|  
|**{CR}**|行は、復帰で区切られます。|  
|**{LF}**|行は、改行で区切られます。|  
|**[セミコロン {;}]**|行は、セミコロンで区切られます。|  
|**[コロン {:}]**|行は、コロンで区切られます。|  
|**[コンマ {,}]**|行は、コンマで区切られます。|  
|**[タブ {t}]**|行は、タブで区切られます。|  
|**[縦棒 {&#124;}]**|行は、縦棒で区切られます。|  
  
 **列区切り記号**  
 使用できる列区切り記号の一覧から選択するか、区切り記号テキストを入力します。  
  
|値|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|列は、復帰と改行の組み合わせで区切られます。|  
|**{CR}**|列は、復帰で区切られます。|  
|**{LF}**|列は、改行で区切られます。|  
|**[セミコロン {;}]**|列は、セミコロンで区切られます。|  
|**[コロン {:}]**|列は、コロンで区切られます。|  
|**[コンマ {,}]**|列は、コンマで区切られます。|  
|**[タブ {t}]**|列は、タブで区切られます。|  
|**[縦棒 {&#124;}]**|列は、縦棒で区切られます。|  
  
 **[更新]**  
 スキップする区切り記号を変更したときの効果を表示するには、 **[最新の情報に更新]**をクリックします。 このボタンは、他の接続オプションを変更した場合にのみ表示されます。  
  
 **[プレビュー]**  
 フラット ファイル内のサンプル データを、選択されたオプションに基づいて列と行に分割して表示します。  
  
 **[列のリセット]**  
 元の列以外のすべての列を削除するには、 **[列のリセット]**をクリックします。  
  
### <a name="format--fixed-width"></a>[形式] = [固定幅]  
 **フォント**  
 プレビュー データの表示に使用するフォントを選択します。  
  
 **[変換元データ列]**  
 行の幅を調整するには、赤い垂直行マーカーをスライドさせます。列の幅を調整するには、プレビュー ウィンドウの最上部のルーラーをクリックします。  
  
 **[行幅]**  
 個々の列に対して区切り記号を追加する前に、行の長さを指定します。 または、プレビュー ウィンドウの赤い垂直線をドラッグして行の終わりをマークします。 行幅値は自動的に更新されます。  
  
 **[列のリセット]**  
 元の列以外のすべての列を削除するには、 **[列のリセット]**をクリックします。  
  
### <a name="format--ragged-right"></a>[形式] = [幅合わせしない]  
  
> [!NOTE]  
>  幅合わせしない形式のファイルとは、最後の列を除くすべての列が固定幅のファイルです。 最後の列は、行区切り記号で区切られます。  
  
 **フォント**  
 プレビュー データの表示に使用するフォントを選択します。  
  
 **[変換元データ列]**  
 行の幅を調整するには、赤い垂直行マーカーをスライドさせます。列の幅を調整するには、プレビュー ウィンドウの最上部のルーラーをクリックします。  
  
 **[行区切り記号]**  
 使用できる行区切り記号の一覧から選択するか、区切り記号テキストを入力します。  
  
|値|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|行は、復帰と改行の組み合わせで区切られます。|  
|**{CR}**|行は、復帰で区切られます。|  
|**{LF}**|行は、改行で区切られます。|  
|**[セミコロン {;}]**|行は、セミコロンで区切られます。|  
|**[コロン {:}]**|行は、コロンで区切られます。|  
|**[コンマ {,}]**|行は、コンマで区切られます。|  
|**[タブ {t}]**|行は、タブで区切られます。|  
|**[縦棒 {&#124;}]**|行は、縦棒で区切られます。|  
  
 **[列のリセット]**  
 元の列以外のすべての列を削除するには、 **[列のリセット]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [フラット ファイル接続マネージャー エディター & #40 です。[全般] ページ &#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md)   
 [フラット ファイル接続マネージャー エディター & #40 です。[詳細] ページ &#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-advanced-page.md)   
 [[フラット ファイル接続マネージャー エディター] &#40;[プレビュー] ページ&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-preview-page.md)  
  
  
