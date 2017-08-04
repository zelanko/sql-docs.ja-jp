---
title: "[フラット ファイル接続マネージャー エディター] ([全般] ページ) |Microsoft ドキュメント"
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
- sql13.dts.designer.ffileconnection.general.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 77296024-5c1a-4f6a-9665-0b50d45d744c
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6e94228deef3c278239cc9f24026677a175d3a65
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="flat-file-connection-manager-editor-general-page"></a>[フラット ファイル接続マネージャー エディター] ([全般] ページ)
  **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、ファイルおよびデータ形式を選択できます。 フラット ファイル接続により、パッケージをテキスト ファイルに接続できるようになります。  
  
 フラット ファイル接続マネージャーの詳細については、「 [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[接続マネージャー名]**  
 ワークフローにおけるフラット ファイル接続の一意な名前を指定します。 指定された名前は、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーに表示されます。  
  
 **Description**  
 接続の説明を記述します。 パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続の目的について記述することをお勧めします。  
  
 **ファイル名**  
 フラット ファイル接続で使用するパスおよびファイル名を入力します。  
  
 **参照**  
 フラット ファイル接続で使用するファイル名を探します。  
  
 **ロケール**  
 ロケールを指定して、順序付けおよび日時の形式に関する言語固有の情報を提供します。  
  
 **Unicode**  
 Unicode を使用するかどうかを示します。 Unicode を使用する場合は、コード ページを指定できません。  
  
 **コード ページ**  
 非 Unicode テキストのコード ページを指定します。  
  
 **Format**  
 区切り記号形式、固定幅形式、または幅合わせしない形式をファイルで使用するかどうかを示します。  
  
|値|Description|  
|-----------|-----------------|  
|[区切り記号]|列は、 **[列]** ページで指定した区切り記号で区切られます。|  
|[固定幅]|列は固定幅を持ちます。|  
|[幅合わせしない]|幅合わせしない形式のファイルとは、最後の列を除くすべての列が固定幅のファイルです。 最後の列は、行区切り記号で区切られます。|  
  
 **テキスト修飾子**  
 使用するテキスト修飾子を指定します。 たとえば、テキスト フィールドを引用符で囲むことを指定できます。  
  
> [!NOTE]  
>  テキスト修飾子を選択した後で、 **[なし]** オプションを再度選択することはできません。 テキスト修飾子の選択を解除するには、「 **なし** 」と入力します。  
  
 **[ヘッダー行区切り記号]**  
 ヘッダー行の区切り記号の一覧から選択するか、区切り記号テキストを入力します。  
  
|値|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|ヘッダー行は、復帰と改行の組み合わせで区切られます。|  
|**{CR}**|ヘッダー行は、復帰で区切られます。|  
|**{LF}**|ヘッダー行は、改行で区切られます。|  
|**[セミコロン {;}]**|ヘッダー行は、セミコロンで区切られます。|  
|**[コロン {:}]**|ヘッダー行は、コロンで区切られます。|  
|**[コンマ {,}]**|ヘッダー行は、コンマで区切られます。|  
|**[タブ {t}]**|ヘッダー行は、タブで区切られます。|  
|**[縦棒 {&#124;}]**|ヘッダー行は、縦棒で区切られます。|  
  
 **[スキップするヘッダー行数]**  
 必要に応じて、スキップするヘッダー行数または初期データ行数を指定します。  
  
 **[先頭データ行を列名として使用する]**  
 先頭データ行を列名として使用するか、ここに列名を指定するかを示します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [フラット ファイル接続マネージャー エディター & #40 です。[列] ページ &#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-columns-page.md)   
 [フラット ファイル接続マネージャー エディター & #40 です。[詳細] ページ &#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-advanced-page.md)   
 [[フラット ファイル接続マネージャー エディター] &#40;[プレビュー] ページ&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-preview-page.md)  
  
  
